# 🏆 Reto 4: Creación de un Agente Conversacional en AI Foundry con Integración a Microsoft Fabric 🤖  

📖 Escenario  
Contoso desea que sus **analistas puedan interactuar con los datos utilizando lenguaje natural**, sin necesidad de conocimientos técnicos en T-SQL o modelado.  
El objetivo es crear un **agente en Azure AI Foundry** que consuma el **modelo semántico conectado a Fabric mediante un Data Agent**, permitiendo obtener respuestas claras, comprensibles y basadas en datos confiables.  

---

### 🎯 Tu Misión  
Al completar este reto podrás:  

✅ Diseñar un **agente conversacional en AI Foundry** integrado con Microsoft Fabric.  
✅ Conectar el agente a un **Data Agent** asociado al modelo semántico Gold.  
✅ Configurar intents y prompts orientados a preguntas reales de negocio.  
✅ Validar que el agente responda en **lenguaje natural**, sin mostrar código ni sintaxis técnica.  
✅ Publicar el agente para uso de analistas dentro de **Copilot, Power BI o AI Foundry**.  

---

## 🚀 Paso 1: Crear el Agente en AI Foundry  
💡 *¿Por qué?* El agente es la interfaz conversacional que permitirá a los analistas interactuar directamente con los datos del modelo semántico.  

1️⃣ Ingresa a **Azure AI Foundry** dentro de Microsoft Fabric.  
2️⃣ Selecciona **“Crear nuevo agente”** y asigna un nombre descriptivo, por ejemplo: `Contoso_AnalistaVirtual`.  
3️⃣ Define el **tipo de agente** como *Conversacional*.  

✅ **Resultado esperado:** El agente está creado y configurado para interacción conversacional.  

---

## 🚀 Paso 2: Conectar el Agente al Data Agent de Fabric  
💡 *¿Por qué?* El Data Agent es el enlace entre AI Foundry y los datos gobernados en Microsoft Fabric.  

1️⃣ En la sección **Fuentes de datos** del agente, selecciona el **Data Agent** creado en el reto anterior.  
2️⃣ Verifica que el Data Agent esté vinculado al **modelo semántico Gold**, que incluye tablas como:  
   - `score_productos_gold`  
   - `creditScore_gold`

3️⃣ Guarda la configuración de conexión.  

✅ **Resultado esperado:** El agente puede acceder al modelo semántico y consultar los datos de manera controlada.  

---

## 🚀 Paso 3: Definir Intents y Prompts Orientativos  
💡 *¿Por qué?* Los intents ayudan a entrenar al agente para comprender las preguntas frecuentes del negocio.  

1️⃣ Crea intents que reflejen las necesidades analíticas de Contoso.  
2️⃣ Ejemplos sugeridos:  

| **Intent / Tema** | **Prompt orientativo (pregunta del analista)** |
|--------------------|-----------------------------------------------|
| score_por_segmento | “¿Cuál es el score promedio por segmento?” |
| productos_con_devolucion | “¿Qué productos tienen mayor tasa de devolución?” |
| correlacion_score_monto | “¿Hay correlación entre score y monto de compra?” |
| productos_valiosos_por_categoria | “¿Qué categoría tiene más productos valiosos?” |
| clientes_por_ocupacion | “¿Cuántos clientes activos hay por ocupación?” |
| ventas_totales_por_marca | “¿Cuál es el valor comercial total por marca?” |

✅ **Resultado esperado:** El agente entiende las preguntas de negocio y responde de forma contextual.  

---

## 🚀 Paso 4: Configurar el Comportamiento del Agente  
💡 *¿Por qué?* Controlar el tono y tipo de respuesta garantiza una experiencia clara y libre de lenguaje técnico.  

1️⃣ En la sección de configuración de respuestas, selecciona:  
   - “Respuestas en **lenguaje natural**”.  
   - “**Ocultar código y sintaxis técnica**”.
   - “No muestre código ni sintaxis técnica **(como T-SQL)**”.
2️⃣ Activa la opción de **respuestas explicativas**, para que el agente justifique sus respuestas con frases como:  
> “Según los datos del modelo, el score promedio en el segmento alto es de 87 puntos.”  

✅ **Resultado esperado:** El agente comunica los hallazgos en lenguaje natural, sin mostrar código o consultas.  

---

## 🚀 Paso 5: Validar el Agente con Preguntas Reales  
💡 *¿Por qué?* La validación permite confirmar que el agente comprende correctamente las consultas y correlaciones entre tablas.  

1️⃣ Prueba directamente en **AI Foundry** con preguntas como:  
   - “¿Qué segmento tiene mayor score promedio?”  
   - “¿Qué marca tiene más productos disponibles?”  
   - “¿Cuál es la tendencia mensual de riesgo?”  
   - “¿Qué perfil de producto genera más ingresos?”

2️⃣ Verifica que las respuestas:  
   - Sean **claras y sin código**.  
   - Entiendan correlaciones entre entidades (por ejemplo, *score* y *productos*).  
   - Provengan de métricas del **modelo semántico conectado**.  

✅ **Resultado esperado:** El agente responde preguntas complejas de forma coherente y basada en datos del modelo.  

---

## 🚀 Paso 6: Publicar y Habilitar el Agente  
💡 *¿Por qué?* Publicar el agente lo hace accesible para analistas y equipos de negocio dentro del entorno de Fabric.  

1️⃣ Publica el agente en el **workspace de Contoso**.  
2️⃣ Habilítalo para que pueda ser usado desde **Copilot, Power BI o directamente desde AI Foundry**.  
3️⃣ Confirma que el agente aparezca en la lista de recursos disponibles para los usuarios autorizados.  

✅ **Resultado esperado:** El agente está activo y disponible para consultas en lenguaje natural dentro del ecosistema de Contoso.  

---

## 🏁 Puntos de Control Finales  

✅ ¿Se creó y configuró correctamente el agente en AI Foundry?  
✅ ¿Está conectado al Data Agent y modelo semántico Gold?  
✅ ¿Se definieron intents y prompts alineados con las necesidades del negocio?  
✅ ¿El agente responde en lenguaje natural sin mostrar código?  
✅ ¿Está publicado y disponible para los analistas de Contoso?  

---

## 📝 Documentación  

-  [Configuración del Agente en AI Foundry](https://learn.microsoft.com/es-es/azure/ai-foundry/agents/environment-setup)  
-  [Conexión con el Data Agent de Fabric](https://learn.microsoft.com/es-es/azure/ai-foundry/agents/how-to/tools/fabric?pivots=portal)  
-  [Ejemplos de Intents y Prompts Entrenados](*****enlace******)  
-  [Referencia oficial - Creación de Agentes de Datos en Fabric](*****enlace******)  
  
