# **Reto 2 – Transformación intermedia y análisis exploratorio (Silver) 🔧📊**

## **Objetivo y solución paso a paso 🧭**

### **Objetivo 🎯**
Transformar los datos Bronze y realizar análisis exploratorio en Silver. 

---

## **Solución paso a paso 🪜**

### **Set de score crediticio y set de productos 🧩**

- Crear nuevo Dataflow Gen2 
- Configurar el origen en la tabla Bronze. 
- Aplicar transformaciones intermedias 
- Crear columna de score crediticio 
- Segmentar clientes por perfil crediticio 
- Se identifica el cluster con mayor promedio de score 
- Se filtran los clientes pertenecientes a ese cluster
- Resultado: subconjunto de clientes con perfil crediticio alto 

---

# **Segmentacion de clientes por score crediticio 🧮**

Importar funciones necesarias 

```python
from pyspark.sql.functions import col, when, udf 
from pyspark.sql.types import StringType 
from pyspark.ml.feature import VectorAssembler 
from pyspark.ml.clustering import KMeans 
```


## **Cargar tabla Silver con datos financieros 🧾**

```python
df_fin = spark.read.table("creditScore_silver") 
```

---

## **Derivar columna score_estimado basada en comportamiento de pago y uso de crédito 💳**

```python
df_fin = df_fin.withColumn("score_estimado", 
    when(col("Payment_Behaviour") == "High_spent_Small_value_payments", 650)
    .when(col("Payment_Behaviour") == "Low_spent_Large_value_payments", 750)
    .when(col("Payment_Behaviour") == "High_spent_Large_value_payments", 800)
    .when(col("Payment_Behaviour") == "Low_spent_Small_value_payments", 600)
    .otherwise(620)
)
```

---

## **Penalización por pagos atrasados ⏰**

```python
df_fin = df_fin.withColumn("score_estimado", 
    col("score_estimado") - (col("Num_of_Delayed_Payment") * 5)
)
```

---

## **Penalización por alto uso de crédito 📉**

```python
df_fin = df_fin.withColumn("score_estimado", 
    when(col("Credit_Utilization_Ratio") > 0.8, col("score_estimado") - 20)
    .otherwise(col("score_estimado"))
)
```

---

## **Limitar score entre 300 y 850 ⚙️**

```python
df_fin = df_fin.withColumn("score_estimado", 
    when(col("score_estimado") < 300, 300)
    .when(col("score_estimado") > 850, 850)
    .otherwise(col("score_estimado"))
)
```

---

## **Filtrar registros válidos para clustering 🧹**

```python
df_fin_clean = df_fin.filter(col("score_estimado").isNotNull()) 
```

---

## **Vectorizar columna score_estimado para ML 🤖**

```python
assembler = VectorAssembler(inputCols=["score_estimado"], outputCol="features") 
df_fin_vec = assembler.transform(df_fin_clean) 
```

---

## **Aplicar KMeans clustering para segmentar clientes 🧠**

```python
kmeans = KMeans(k=3, seed=42) 
model_fin = kmeans.fit(df_fin_vec) 
df_fin_clustered = model_fin.transform(df_fin_vec) 
```

---

## **Etiquetar perfiles crediticios según promedio de score por cluster 🏷️**

```python
cluster_scores = df_fin_clustered.groupBy("prediction") \
    .avg("score_estimado") \
    .orderBy("avg(score_estimado)", ascending=False) \
    .collect()
```

---

## **Crear mapa de etiquetas: Alto, Medio, Bajo 🗺️**

```python
cluster_map = {} 
for i, row in enumerate(cluster_scores): 
    cluster_map[row["prediction"]] = ["Alto", "Medio", "Bajo"][i] 
```

---

## **UDF para asignar etiqueta ⚡**

```python
def map_cluster(pred): 
    return cluster_map.get(pred, "Desconocido") 

map_udf = udf(map_cluster, StringType()) 
df_segmentado = df_fin_clustered.withColumn("perfil_crediticio", map_udf(col("prediction"))) 
```

---

## **Contar clientes por perfil (opcional para validación) 📊**

```python
df_segmentado.groupBy("perfil_crediticio").count().orderBy("count", ascending=False).show() 
```

---

## **Filtrar clientes con perfil Alto 🥇**

```python
df_gold_fin = df_segmentado.filter(col("perfil_crediticio") == "Alto") 
```

---

## **Guardar tabla Gold con clientes de mejor perfil crediticio 💾**

```python
df_gold_fin.write.option("mergeSchema", "true").mode("overwrite").saveAsTable("creditScore_gold") 
```

---




# **Segmentación ML + Promoción a Gold (Retail por producto) 🛍️🤖**

---

## **📌 Importar funciones necesarias**

```python
from pyspark.sql.functions import col, when, udf 
from pyspark.sql.types import StringType 
from pyspark.ml.feature import VectorAssembler 
from pyspark.ml.clustering import KMeans 
```

---

## **Cargar tabla Silver con catálogo de productos retail 🧾**

```python
df_retail = spark.read.table("productos_silver") 
```

---

## **🧮 Derivar columna valor_comercial = Price × Stock**

```python
df_retail = df_retail.withColumn("valor_comercial", col("Price") * col("Stock")) 
```

---

## **🧮 Derivar columna disponibilidad_binaria**

```python
df_retail = df_retail.withColumn("disponible", 
    when(col("Availability") == "InStock", 1).otherwise(0)
)
```

---

## **🧹 Filtrar registros válidos para clustering**

```python
df_retail_clean = df_retail.filter( 
    col("valor_comercial").isNotNull() & col("disponible").isNotNull()
)
```

---

## **📊 Vectorizar columnas para ML**

```python
assembler = VectorAssembler(inputCols=["valor_comercial", "disponible"], outputCol="features") 
df_retail_vec = assembler.transform(df_retail_clean) 
```

---

## **🤖 Aplicar KMeans clustering para segmentar productos**

```python
kmeans = KMeans(k=3, seed=42) 
model_retail = kmeans.fit(df_retail_vec) 
df_retail_clustered = model_retail.transform(df_retail_vec) 
```

---

## **🏷️ Etiquetar productos según valor comercial promedio por cluster**

```python
cluster_scores = df_retail_clustered.groupBy("prediction") \
    .avg("valor_comercial") \
    .orderBy("avg(valor_comercial)", ascending=False) \
    .collect()
```

---

## **Crear mapa de etiquetas: Valioso, Medio, Bajo 🗺️**

```python
cluster_map = {} 
for i, row in enumerate(cluster_scores): 
    cluster_map[row["prediction"]] = ["Valioso", "Medio", "Bajo"][i] 
```

---

## **UDF para asignar etiqueta ⚡**

```python
def map_cluster(pred): 
    return cluster_map.get(pred, "Desconocido") 

map_udf = udf(map_cluster, StringType()) 
df_segmentado = df_retail_clustered.withColumn("perfil_producto", map_udf(col("prediction"))) 
```

---

## **🔍 Conteo por perfil (opcional para validación)**

```python
df_segmentado.groupBy("perfil_producto").count().orderBy("count", ascending=False).show() 
```

---

## **🥇 Filtrar productos valiosos y disponibles**

```python
df_gold_retail = df_segmentado.filter(
    (col("perfil_producto") == "Valioso") & (col("disponible") == 1)
)
```

---

## **💾 Guardar tabla Gold con productos valiosos**

```python
df_gold_retail.write.option("mergeSchema", "true").mode("overwrite").saveAsTable("productos_gold") 
```

