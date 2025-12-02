# 🚀 Reto: Gobierno y Productos de Datos con Purview + Fabric  

## 🌍 Contexto  
La organización **Contoso Retail** busca establecer un **marco de gobierno de datos unificado** que permita a los equipos de análisis y negocio **identificar, clasificar y consumir datos** de forma confiable dentro de **Microsoft Fabric**.  

Para lograrlo, se requiere **configurar Microsoft Purview** como herramienta de gobierno y **Fabric** como plataforma de análisis y colaboración de datos.  

---

## 🎯 Objetivo general  
Diseñar e implementar un entorno gobernado que permita:  
- Catalogar los activos de datos mediante **Purview**.  
- Integrar las fuentes de datos con **Fabric**.  
- Crear y documentar **data products** que puedan ser consumidos por diferentes equipos.  

---

## 🧠 Tareas del reto  

### 🔹 1. Configuración inicial de Purview  
- Crear una cuenta de **Microsoft Purview** y acceder al **Data Map**.  
- Agregar una colección llamada **ContosoData** para organizar los activos.  
- Registrar al menos una **fuente de datos proveniente de Fabric** (por ejemplo, un Lakehouse o un Warehouse).  
- Ejecutar un **escaneo automático** para descubrir metadatos.  
- Verificar que los activos aparezcan correctamente **catalogados en el Data Map**.  

---

### 🔹 2. Clasificación y etiquetado de datos  
- Aplicar **clasificadores automáticos o manuales** a las columnas con información sensible (nombre, correo, país).  
- Crear **glosarios de negocio** para definir términos clave (por ejemplo: *Cliente*, *Venta*, *Suscripción*).  
- Asociar los términos del glosario a los activos catalogados para mejorar la búsqueda semántica.  

---

### 🔹 3. Integración con Microsoft Fabric  
- En **Fabric**, crear un **Lakehouse** llamado `Contoso_Sales_Lakehouse`.  
- Cargar **datos de ejemplo** (ventas y clientes) y validar su visibilidad en el **Data Hub**.  
- Desde **Purview**, vincular la fuente de **Fabric** al catálogo para habilitar la **visibilidad del linaje**.  

---

### 🔹 4. Creación de Data Products  
- En **Fabric**, dentro de **Data Activator** o **Data Warehouse**, construir un **data product** que combine información de *clientes* y *ventas*.  
- Publicar el producto con el nombre **Sales Insights Product**.  
- Documentar en el catálogo de **Purview**:  
  - Propósito del data product.  
  - Calidad de los datos.  
  - Responsables.  
  - Linaje de datos desde la fuente hasta el consumo.  

---

### 🔹 5. Validación del Gobierno  
- Verificar que los usuarios puedan **buscar y descubrir activos** desde el catálogo de **Purview**.  
- Revisar el **linaje de datos** para confirmar la trazabilidad desde la fuente original hasta el producto final.  
- Generar un **informe resumen** con:  
  - Activos catalogados.  
  - Términos de glosario creados.  
  - Data products publicados.  

---

## 🏁 Resultado esperado  
Un entorno **gobernado y colaborativo**, donde todos los activos de **Microsoft Fabric** estén:  
- Catalogados y clasificados en **Purview**.  
- Vinculados con linaje completo desde origen hasta consumo.  
- Documentados y disponibles como **data products** listos para ser utilizados por **analistas** o **científicos de datos**.  
