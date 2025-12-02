# 🏆 Reto 1: Ingesta de Datos desde Cosmos DB a Microsoft Fabric (Capa Bronze) + Limpieza Básica  

📖 Escenario  
Contoso necesita consolidar sus **datos operativos** en **Microsoft Fabric**.  
El equipo de datos debe realizar la **ingesta desde Azure Cosmos DB** hacia la capa **Bronze** y aplicar una **limpieza inicial** para preparar los datos antes de avanzar a las siguientes fases de transformación.  

---

### 🎯 Tu Misión  
Al completar este reto podrás:  

✅ Ingerir los datos desde **Azure Cosmos DB** hacia **Microsoft Fabric** utilizando **Dataflows Gen2**.  
✅ Aplicar una **limpieza básica** que incluya:  
- Manejo de valores nulos o vacíos.  
- Eliminación de columnas innecesarias.  
- Normalización de formatos básicos (fechas, texto, etc.).  
✅ Generar una tabla limpia dentro de la capa **Bronze** del Lakehouse.  

---

## 🚀 Paso 1: Crear un Dataflow Gen2 para la Ingesta desde Cosmos DB  
💡 *¿Por qué?* Los **Dataflows Gen2** permiten realizar la ingesta y transformación inicial de datos sin necesidad de código, conectando fácilmente fuentes externas como Cosmos DB con tu Lakehouse.  

1️⃣ En **Microsoft Fabric**, crea un nuevo **Dataflow Gen2** dentro de tu workspace.  
🔹 Selecciona **Azure Cosmos DB** como fuente de datos.  
🔹 Ingresa las credenciales de conexión (endpoint y clave de acceso).  
🔹 Conecta con el contenedor que contiene los datos de **ventas** o **finanzas**.  
🔹 Define como destino tu **Lakehouse (Bronze)** para almacenar los datos ingeridos.  

✅ **Resultado esperado:** Los datos JSON de Cosmos DB se encuentran almacenados en la capa Bronze del Lakehouse.  

---

## 🚀 Paso 2: Validar la Carga y Estructura de los Datos  
💡 *¿Por qué?* Validar la ingesta garantiza que los datos sean completos y coherentes antes de iniciar la limpieza.  

1️⃣ Accede a tu **Lakehouse** desde el Dataflow o desde el panel de Fabric.  
🔹 Revisa que las tablas o archivos creados contengan los campos esperados.  
🔹 Comprueba que no existan errores de formato o registros incompletos.  

✅ **Resultado esperado:** La estructura base de los datos ha sido validada correctamente.  

---

## 🚀 Paso 3: Aplicar Limpieza Básica en el Dataflow Gen2  
💡 *¿Por qué?* Este paso mejora la calidad de los datos, asegurando consistencia y usabilidad para análisis posteriores.  

1️⃣ Edita tu **Dataflow Gen2** para agregar pasos de transformación:  
   - 🧹 **Eliminar columnas innecesarias** que no aporten valor analítico.  
   - 🩹 **Reemplazar o eliminar valores nulos o vacíos.**  
   - 🕒 **Normalizar formatos básicos** (por ejemplo, campos de fecha o texto en minúsculas).  
2️⃣ Guarda y ejecuta el Dataflow para aplicar las transformaciones.  
3️⃣ Publica los resultados en la **capa Bronze** de tu Lakehouse.  

✅ **Resultado esperado:** La tabla “Bronze” contiene datos limpios, estructurados y listos para su transformación en la capa Silver.  

---

## 🏁 Puntos de Control Finales  

✅ ¿Se completó la ingesta desde Cosmos DB mediante Dataflows Gen2?  
✅ ¿Se aplicaron correctamente las transformaciones básicas?  
✅ ¿Los datos resultantes están almacenados y accesibles en la capa Bronze?  
✅ ¿Se documentaron los pasos realizados y las evidencias visuales?  

---

## 📝 Documentación  


- [Creacion Dataflow Gen2](https://learn.microsoft.com/es-mx/fabric/data-factory/create-first-dataflow-gen2)



