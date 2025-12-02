# 🏆 Reto 2: Automatización del Procesamiento de Documentos con Logic Apps 🚀  

## 📖 Objetivo  

En este reto deberás:  

✅ Configurar una **Azure Logic App** para procesar archivos PDF automáticamente  
✅ Habilitar la **Identidad Administrada** para un acceso seguro a los recursos  
✅ Asignar **permisos** a la Logic App para almacenamiento y procesamiento con IA  
✅ Usar **Document Intelligence (Form Recognizer)** para analizar PDFs  
✅ Crear un **pipeline de ADF** para mover PDFs desde **Fabric** hacia una **Cuenta de Almacenamiento**  
✅ Guardar los **JSON analizados** en la **Cuenta de Almacenamiento**  
✅ Verificar que los **archivos procesados** se guarden correctamente en el **Storage Account**  

---

## 🚀 Paso 1: Crear una Logic App  

💡 **¿Por qué?** La Logic App permitirá **automatizar** la detección de nuevos archivos PDF y activar el análisis con **Document Intelligence**.  

### 1️⃣ Crear una Azure Logic App  
🔹 En el **Azure Portal**, crea una nueva **Logic App (Consumption Plan)**.  

🔹 **¿Qué configuraciones debes definir durante la creación?**  

✅ **Resultado**: Se crea una Logic App lista para ser configurada.  

---

## 🚀 Paso 2: Habilitar la Identidad Administrada para la Logic App  

💡 **¿Por qué?** La Logic App necesita autenticarse de forma segura para interactuar con **Azure Storage** y **Document Intelligence**.  

### 1️⃣ Activar la Identidad Asignada del Sistema  
🔹 En la configuración de la **Logic App**, habilita la opción **System-Assigned Identity**.  

🔹 **¿Dónde puedes copiar el Object (Principal) ID para usarlo más adelante?**  

✅ **Resultado**: La Logic App cuenta con una identidad para autenticación.  

---

## 🚀 Paso 3: Asignar Permisos a la Logic App  

💡 **¿Por qué?** La Logic App necesita **acceso** para leer desde **Blob Storage** y escribir en la **Cuenta de Almacenamiento**.  

### 1️⃣ Asignar permisos IAM a la Logic App  
🔹 Dirígete a **Storage Account y Document Intelligence** → **Access Control (IAM)**  

🔹 Asigna los siguientes **roles** a la **Identidad Administrada** de la Logic App:  
✅ **Storage Blob Data Contributor**  
✅ **Storage Account Contributor**  
✅ **Cognitive Services Contributor** (para Document Intelligence)  

🔹 **¿Por qué son importantes estos roles para el procesamiento de documentos?**  

✅ **Resultado**: La Logic App ahora puede acceder al **Blob Storage** y a los **servicios de IA**.  

---

## 🚀 Paso 4: Configurar la Logic App usando el Portal de Azure (Diseñador)  

💡 **¿Por qué?** Es necesario **definir el flujo de trabajo** para procesar los PDFs entrantes.  

### 1️⃣ Crear el flujo de trabajo en el Logic App Designer  
🔹 Abre el **Logic App Designer** → Inicia con una **Blank Logic App**  

🔹 **Disparador (Trigger):**  
✅ Agrega **"When a blob is added or modified (properties only)"**  
✅ **Selecciona la cuenta de almacenamiento**: `(Tu Storage Account)`  
✅ **Selecciona el contenedor**: `Tu-Contenedor`  
✅ Agrega una **condición**: que se active solo para archivos `.pdf`  

🔹 **Paso de procesamiento:**  
✅ Agrega **"Analyze Document (Prebuilt-Invoice)"**  
✅ Proporciona la **URL de almacenamiento** del archivo  

🔹 **Guardar la salida:**  
✅ Agrega **"Create Blob"** en **Azure Blob Storage**  
✅ **Selecciona el contenedor**: `processed-json`  
✅ **Define el nombre del Blob:**  

```plaintext
analyzed-document-@{triggerOutputs()?['body']['name']}.json
