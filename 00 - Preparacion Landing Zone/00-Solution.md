# Solución Reto 00 — Preparación de la Landing Zone y Conexión de Datos (Microsoft Fabric)

Este documento describe, paso a paso, cómo completar el *Reto 0*: crear la zona de aterrizaje (landing zone) en Microsoft Fabric, provisionar Azure Cosmos DB con los JSON suministrados y conectar ambas plataformas.

Objetivos
- Provisionar Azure Cosmos DB (NoSQL) y cargar los datasets JSON.
- Crear un workspace y una Lakehouse en Microsoft Fabric con la estructura Bronze / Silver / Gold.
- Conectar Fabric a Cosmos DB y verificar la ingesta inicial.

Requisitos previos
- Permisos para crear recursos en Azure.
- Archivos JSON (por ejemplo `creditScore.json`, `products.json`).

Resultado esperado
- Cosmos DB con contenedores que contienen los JSON.
- Workspace en Fabric conectado a una Capacity.
- Lakehouse `Contoso_Lakehouse` con carpetas o tablas: `bronze`, `silver`, `gold`.

---

## 1. Crear Azure Cosmos DB (NoSQL)

1. Accede al portal de Azure.
2. Busca **Azure Cosmos DB** → Crear → seleccionar API **NoSQL**.
3. Rellena: resource group, account name (`contoso-cosmosdb`), region.
	![Crear Cosmos](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Creando%20Cosmos%20-%20Basics.png)

	![Review](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Creando%20Cosmos%20-%20Review.png)
4. Crear la cuenta. En *Data Explorer* crea la base de datos y contenedores (por ejemplo `sales`, `credit`).
  	![Data Explorer](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/2%20-Data%20Explorer.png)
   
   	![New item](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/2%20-Upload%20Item.png)

5. Carga los archivos JSON (manualmente desde Data Explorer o usando Azure Data Factory para cargas repetibles).
   	![Upload Jason](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/2%20-Upload%20json.png)

Verificación
- En *Data Explorer* se ven documentos JSON en el contenedor.

---

## 2. Crear Workspace en Microsoft Fabric

1. Abre Microsoft Fabric y crea un workspace llamado `ContosoData-Fabric`.
2. Asocia una Fabric Capacity (si tu organización la tiene asignada).

Verificación
- El workspace aparece en el listado y tienes permisos adecuados.

---

## 3. Crear Lakehouse y definir capas

1. En el workspace, crea una Lakehouse `Contoso_Lakehouse`.
2. Dentro, crea carpetas o tablas con la convención:
	- `bronze.*` para datos crudos
	- `silver.*` para datos limpios
	- `gold.*` para datos curados/consumo

Verificación
- Las carpetas/tablas están visibles en el navegador del Lakehouse.

---

## 4. Conectar Fabric a Azure Cosmos DB

1. Crear nuevo item.
2. En Fabric DataFlow gen 2 → New → Connection → Azure Cosmos DB.  
	![Crear Conexion](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Crear%20Dataflow%201.png)

	![Buscar conector Cosmos](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Crear%20Dataflow%202.png)

	![Buscar Conector 2](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Crear%20Dataflow%203.png)

4. Proporciona endpoint y clave (Azure Portal → Cosmos DB → Keys).
	![Conectar cosmos](https://github.com/stmora98/Del_Insight_a_la_Decision/blob/main/00%20-%20Preparacion%20Landing%20Zone/Reference%20Pictures/Connect%20Data%20source.png)

5. Testea y guarda la conexión.

Verificación
- La conexión se prueba y puedes ver containers/collections disponibles.

---



