# Solución Reto 01 — Ingesta desde Cosmos DB a Microsoft Fabric (Capa Bronze) + Limpieza Básica

Guía paso a paso para ingerir datos desde Azure Cosmos DB hacia la capa Bronze de la Lakehouse en Microsoft Fabric, aplicar limpieza inicial y validar resultado.

Objetivo
- Ingerir datos desde Cosmos DB usando Dataflow Gen2 o pipeline y aplicar transformaciones básicas (nulos, columnas, formatos).

Requisitos previos
- Conexión a Cosmos DB desde Fabric (ver `00-Solution.md`).

## Pasos

### 1 — Crear Dataflow Gen2

1. En Fabric, Data → New → Dataflow Gen2.
2. Selecciona **Azure Cosmos DB** como fuente.
3. Rellena endpoint y key (o selecciona la conexión ya creada).
4. Selecciona la colección/contenedor que contiene `products` o `creditScore`.

### 2 — Diseñar transformaciones básicas

Dentro del diseñador de Dataflow:
- Elimina columnas no necesarias.
- Normaliza formatos: convertir fechas, cadenas (trim, lower), normalizar decimales.
  ![formato fechas](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Ejemplo%20transformacion%20fechas.png)
  
- Reemplaza o marca valores nulos (por ejemplo, `unknown` o valores por defecto).
   ![valores vacios](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Ejemplo%20transformacion%202.png)
- Filtra registros corruptos o incompletos (si aplica).
  

Consejo: agrega pasos de validación intermedios y usa muestras pequeñas para probar transformaciones.

### 3 — Destino: Lakehouse Bronze

1. Configura el sink/destino como la Lakehouse `Contoso_Lakehouse` → esquema/tabla `bronze.sales`.
   ![Guardar en tabla bronce](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Guardar%20bronze%201.png)

   ![Guardar como tabla nueva](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/01-Ingesta%20con%20Data%20Factory%20en%20Fabric/Reference%20Pictures/Guardar%20bronze%202.png)

3. Ejecuta el Dataflow en modo de prueba y luego en producción.

### 4 — Verificar y documentar

1. Abre la Lakehouse y revisa `bronze.sales`.
2. Verifica conteo de registros, columnas esperadas y formatos de columna (fechas, numéricos).
3. Guarda un registro de la ejecución (logs) y captura de pantalla.

## Validaciones clave
- Conteo total vs origen en Cosmos DB.
- No hay columnas que deban eliminarse accidentalmente.
- Nulos manejados y formatos normalizados.

## Siguientes pasos sugeridos
- Automatizar con un pipeline (schedule) para ingestas periódicas.
- Implementar pruebas de calidad de datos (Data Quality checks) antes de mover a Silver.
