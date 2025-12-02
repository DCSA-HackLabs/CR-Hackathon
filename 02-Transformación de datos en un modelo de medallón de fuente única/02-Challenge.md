# 🏆 Reto 2: Transformación Intermedia y Análisis Exploratorio en Microsoft Fabric (Capa Silver) 

📖 Escenario  
Contoso busca **evaluar la calidad de sus datos** antes de construir modelos predictivos.  
Para ello, el equipo de datos debe **transformar y analizar los datos** que provienen de la capa **Bronze**, generando una versión intermedia optimizada en la capa **Silver**.  

---

### 🎯 Tu Misión  
Para completar este reto deberas:  

✅ Crear una **tabla Silver** a partir de los datos limpios en **Bronze**.  
✅ Aplicar **transformaciones intermedias** que mejoren la estructura y consistencia de los datos.  
✅ Realizar un **análisis exploratorio** usando técnicas de agrupación y machine learning (ML).  
✅ Dejar los datos listos para la etapa de **modelado semántico (Gold)**.  

---

## 🚀 Paso 1: Crear la Tabla Silver a partir de Bronze  
💡 *¿Por qué?* La capa Silver sirve como base para aplicar transformaciones y análisis intermedios, preparando los datos para el modelado analítico posterior.  

1️⃣ Accede al **Lakehouse** en tu workspace de Microsoft Fabric.  
2️⃣ Utiliza un **notebook** o un **Dataflow Gen2** para leer los datos de la capa **Bronze**.  
3️⃣ Aplica una limpieza adicional si es necesario (por ejemplo, corrección de formatos o estandarización de nombres de columnas).  
4️⃣ Guarda los datos transformados en una nueva tabla dentro de la **capa Silver**.  

✅ **Resultado esperado:** Los datos están disponibles en Silver y listos para aplicar transformaciones más avanzadas.  

---

## 🚀 Paso 2: Aplicar Transformaciones Intermedias  
💡 *¿Por qué?* Estas transformaciones permiten generar vistas analíticas y facilitar los procesos de modelado y segmentación.  

1️⃣ Abre tu **notebook de Fabric** y carga la tabla Silver creada.  
2️⃣ Aplica transformaciones que aporten valor analítico, por ejemplo:  
   - 📊 **Agrupaciones:** Identificar el **score crediticio más alto por cliente**.  
   - 🏷️ **Perfiles de producto:** Clasificar productos por categoría o nivel de ventas.  
3️⃣ Crea nuevas columnas o métricas que sirvan para análisis posteriores (por ejemplo, promedio de compras o niveles de riesgo).  

✅ **Resultado esperado:** La tabla Silver contiene transformaciones útiles y listas para análisis exploratorio o segmentación.  

---

## 🚀 Paso 3: Realizar un Análisis Exploratorio con ML  
💡 *¿Por qué?* Las técnicas de **Machine Learning (ML)** permiten evaluar la distribución y similitud entre los datos, ayudando a descubrir patrones.  

1️⃣ Usa **funciones de ML integradas** o **librerías PySpark MLlib** / **scikit-learn** en tu notebook.  
2️⃣ Implementa un algoritmo de **K-Means** para agrupar registros en *k* clusters:  
   - 🎯 Agrupa clientes o productos según características numéricas similares.  
   - 🔍 Analiza las relaciones entre variables dentro de cada cluster.    

✅ **Resultado esperado:** Obtienes una segmentación de tus datos y una comprensión más profunda de su comportamiento.  

---

## 🚀 Paso 4: Preparar la Tabla para el Modelado Semántico (Capa Gold)  
💡 *¿Por qué?* La preparación de la tabla Silver es el paso final antes de crear modelos analíticos o dashboards de negocio.  

1️⃣ Ajusta nombres de columnas, tipos de datos y claves primarias necesarias para el modelado.  
2️⃣ Guarda la versión final de la tabla en el **Lakehouse (Silver)** o publícala como fuente para la **capa Gold**.  

✅ **Resultado esperado:** Los datos están listos para ser consumidos en la capa Gold por herramientas de BI o modelos de análisis avanzados.  

---

## 🏁 Puntos de Control Finales  

✅ ¿Se creó correctamente la tabla Silver a partir de Bronze?  
✅ ¿Se aplicaron transformaciones intermedias (agrupaciones, cálculos, perfiles)?  
✅ ¿Se implementó y analizó un modelo de K-Means o técnica ML similar?  
✅ ¿Están los datos listos para su uso en la capa Gold?  
✅ ¿Se documentaron las transformaciones y resultados del análisis exploratorio?  

---

## 📝 Documentación  

- [Notebook de Transformaciones y ML](https://learn.microsoft.com/es-es/fabric/data-engineering/how-to-use-notebook)  


💡 *Consejo:* Mantén un registro de los parámetros y resultados de tus modelos, ya que serán fundamentales para el siguiente reto: **modelado y curación en la capa Gold**. 🚀  

