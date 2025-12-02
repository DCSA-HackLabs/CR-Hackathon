# 🏆 Reto 3: Modelo Semántico, Data Agent y Dashboard de Valor en Microsoft Fabric (Capa Gold) 

📖 Escenario  
Contoso busca **habilitar análisis de negocio sobre datos confiables**.  
El equipo de datos debe construir un **modelo semántico**, crear un **Data Agent conectado al modelo** y diseñar un **dashboard de valor** en Power BI que permita responder preguntas clave del negocio.  

---

### 🎯 Tu Misión  
Al completar este reto podrás:  

✅ Diseñar un **modelo semántico** en la capa **Gold** con medidas y dimensiones relevantes.  
✅ Crear un **Data Agent** en Microsoft Fabric conectado a dicho modelo.  
✅ Construir un **dashboard interactivo en Power BI** con visualizaciones de valor.  
✅ Validar que el modelo responda correctamente a preguntas de negocio a través de Copilot o Power BI.  

---

## 🚀 Paso 1: Crear la Tabla Gold con Agregaciones y Relaciones Clave  
💡 *¿Por qué?* La capa **Gold** contiene datos curados y listos para análisis, donde se aplican las últimas transformaciones y agregaciones.  

1️⃣ Desde tu workspace en **Microsoft Fabric**, crea una **tabla Gold** basada en las tablas de la capa Silver.  
2️⃣ Aplica **agregaciones** y define **relaciones clave** entre tablas por `productID`.  
3️⃣ Asegúrate de que todas las tablas necesarias para análisis estén consolidadas y con claves correctamente relacionadas.  

✅ **Resultado esperado:** La capa Gold contiene una estructura de datos optimizada, lista para la creación del modelo semántico.  

---

## 🚀 Paso 2: Diseñar el Modelo Semántico  
💡 *¿Por qué?* El modelo semántico permite representar las medidas, dimensiones y relaciones de negocio de forma que los usuarios puedan consultar y analizar los datos fácilmente.  

1️⃣ En **Power BI o Microsoft Fabric**, diseña el **modelo semántico Gold** incluyendo:  
   - 🔹 **Dimensiones:** `Brand`, `Category`, `perfil_producto`, `availability`.  
   - 📏 **Medidas clave:**  
     - `valor_comercial_total = SUM([valor_comercial])`  
     - `productos_disponibles = COUNTIF([availability] = "In Stock")`  
2️⃣ Valida que las medidas y relaciones estén correctamente configuradas.  
3️⃣ Si tienes múltiples tablas (clientes, productos, transacciones), crea las relaciones por **productID** o campos equivalentes.  

✅ **Resultado esperado:** El modelo semántico Gold está completo y refleja la lógica del negocio de Contoso.  

---

## 🚀 Paso 3: Validar el Modelo con Preguntas de Negocio  
💡 *¿Por qué?* Validar el modelo garantiza que las consultas naturales en Copilot o Power BI devuelvan respuestas precisas.  

1️⃣ Prueba las siguientes preguntas en **Copilot o Power BI**:  
   - 💬 “¿Qué categoría tiene más productos valiosos?”  
   - 💬 “¿Cuál es el valor comercial total por marca?”  
   - 💬 “¿Cuántos productos están disponibles?”  
   - 💬 “¿Qué perfil de producto genera más ingresos?”  
2️⃣ Si alguna respuesta no es correcta, ajusta las medidas o relaciones en el modelo.  

✅ **Resultado esperado:** El modelo responde de manera precisa y coherente a las preguntas de negocio.  

---

## 🚀 Paso 4: Diseñar un Dashboard en Power BI  
💡 *¿Por qué?* El dashboard permite visualizar métricas clave y comunicar insights de negocio de forma efectiva.  

1️⃣ Abre **Power BI (dentro de Fabric o Power BI Desktop)** y crea un nuevo dashboard conectado a tu modelo Gold.  
2️⃣ Incluye visualizaciones como:  
   - 📊 **Score promedio por segmento (financiero).**  
   - 💰 **Productos más vendidos y tasa de devolución (retail).**  
   - 📈 **Tendencias semanales o mensuales.**  
3️⃣ Personaliza colores, títulos y formato para mejorar la presentación.  
4️⃣ Publica el dashboard en el **workspace correspondiente**.  

✅ **Resultado esperado:** El dashboard está publicado y conectado al Data Agent, listo para responder preguntas en tiempo real.  

---

## 🚀 Paso 5: Crear un Data Agent Conectado al Modelo  
💡 *¿Por qué?* Un **Data Agent** en Fabric permite que los usuarios consulten los datos mediante lenguaje natural, potenciando el uso de **Copilot**.  

1️⃣ En Microsoft Fabric, crea un **Data Agent** y conéctalo a tu **modelo semántico Gold**.  
2️⃣ Configura los permisos y acceso para los usuarios del workspace.  
3️⃣ Prueba consultas con lenguaje natural para validar que el agente responde adecuadamente.  

✅ **Resultado esperado:** El Data Agent está conectado al modelo y permite realizar consultas interactivas.  

---

## 🏁 Puntos de Control Finales  

✅ ¿Se creó la tabla Gold con agregaciones y relaciones clave?  
✅ ¿Se diseñó el modelo semántico con medidas y dimensiones adecuadas?  
✅ ¿El modelo responde correctamente a preguntas de negocio en Copilot o Power BI?  
✅ ¿Se creó y probó el Data Agent conectado al modelo?  
✅ ¿El dashboard está publicado y funcionando correctamente?  

---

## 📝 Documentación  

- [Modelo Semántico Gold (Power BI)](https://learn.microsoft.com/es-es/fabric/data-warehouse/semantic-models)  
- [Actualiza Modelo Semantico](https://learn.microsoft.com/es-es/power-bi/connect-data/data-pipeline-templates)
- [Crear Data Agent](https://learn.microsoft.com/es-es/fabric/data-science/how-to-create-data-agent)

💡 *Consejo:* Documenta las relaciones, medidas y fuentes de datos utilizadas, ya que este modelo servirá como base para la creación de **copilotos empresariales** y **análisis predictivos avanzados**. 🚀  
