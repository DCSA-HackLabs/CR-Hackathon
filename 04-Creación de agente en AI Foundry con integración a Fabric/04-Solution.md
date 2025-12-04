# Solución Reto 04 — Crear Agente conversacional en AI Foundry integrado con Fabric

Objetivo
- Crear un agente en AI Foundry que consulte el Data Agent en Fabric (modelo semántico) y responda en lenguaje natural sin exponer código.

Requisitos previos
- Modelo semántico Gold y Data Agent creados (Reto 03).

## Pasos

### 1 — Crear el agente en AI Foundry

1. Accede a Azure AI Foundry (desde Fabric o portal).
2. Crear -> Nuevo agente conversacional (nombre: `Contoso_AnalistaVirtual`).

### 2 — Conectar al Data Agent de Fabric

1. En configuración de fuentes, añade la conexión al Data Agent (seleccionar el Data Agent creado previamente).
2. Verifica permisos y alcance (solo lectura a las medidas/tablas necesarias).

### 3 — Definir intents y prompts

1. Lista intents según preguntas de negocio (score_por_segmento, ventas_totales_por_marca, productos_valiosos).
2. Para cada intent define ejemplos de pregunta y respuestas esperadas.

### 4 — Ajustar comportamiento (tono y formato)

1. Configura respuestas en lenguaje natural. Desactiva la exposición de consultas (T-SQL) o cualquier sintaxis técnica.
2. Habilita explicaciones breves que justifiquen la respuesta.

### 5 — Probar y publicar

1. Ejecuta pruebas con preguntas reales y valida que las respuestas sean correctas y sin código.
2. Publica el agente y habilita su uso desde Copilot / Power BI o AI Foundry UI.

## Validaciones
- El agente responde con frases naturales y no muestra consultas SQL.
- Las respuestas coinciden con los números del modelo Gold.
