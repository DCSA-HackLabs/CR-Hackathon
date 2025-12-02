# Guía de Prerrequisitos para el Hackathon  
### 🧩 Preparativos esenciales para participar con éxito  

---

## ✅ Registro de Proveedores de Recursos  
Asegúrate de que los siguientes proveedores de recursos estén registrados en tu suscripción de **Azure**:  
- `Microsoft.PolicyInsights`  
- `Microsoft.Cdn`  
- `Microsoft.StreamAnalytics`  

**Cómo registrarlos:**  
1. Ve al **Portal de Azure** → Configuración de la suscripción → *Proveedores de recursos*.  
2. Selecciona cada proveedor y haz clic en **Registrar**.  

---

## ✅ Identidad y Autenticación  
**Principal de Servicio y Autenticación:**  
- ID de cliente y secreto *(que no expire antes del segundo día del evento)*.  
- Los participantes deben tener disponible su **ID de cliente** y **secreto** durante el hackathon.  

---

## ✅ Prerrequisitos de Microsoft Fabric  
**Opciones de acceso:**  
- Crear una **nueva prueba gratuita de Microsoft Fabric**, o  
- Usar una **capacidad de Fabric ya aprovisionada** en su suscripción de Azure.  

**Requisitos de configuración de Fabric:**  
- Al menos un miembro asignado como **administrador de Microsoft Fabric**.  
- Un **espacio de trabajo de Fabric** asignado al equipo.  
- Capacidad para crear **Lakehouses** y **Modelos Semánticos** en Fabric.  
- Acceso a **OneLake** (almacenamiento de Fabric) para subir archivos.  

---

## ✅ Requisitos de Azure OpenAI  
**Cuota TPM para Modelos OpenAI:**  
- `text-embedding-ada-002`  
- `gpt-35-turbo-16k`  

Si la cuota actual es menor a **100.000**, solicita un aumento antes del evento para garantizar disponibilidad.  
> ⏱️ Las aprobaciones suelen tardar 24 horas, por lo que es crítico completar este paso con antelación.  

**Pasos recomendados:**  
- Verifica tu cuota actual → [Guía de Cuotas de Azure OpenAI](#)  
- Solicita aumento de cuota → [Solicitud de Aumento de Cuota](#)  

---

## ✅ Requisitos de Red y Acceso  
Asegura acceso sin restricciones a las siguientes plataformas:  
- **Azure AI Foundry**  
- **Azure Data Factory**  
- **Document Intelligence Studio**  
- **Portal de Azure**  
- **Microsoft Fabric**  

---

## ✅ Requisitos de Visual Studio Code  
**Extensiones necesarias en VS Code:**  
- Python 🐍  
- Azure Tools ☁️  
- Azure Semantic Kernel Tools 🧠  

---

## 🎯 Qué Esperar  
- 💡 Retos técnicos prácticos  
- 🤝 Colaboración con profesionales afines  
- 🧩 Resolución de problemas en vivo y guía experta  
- 🚀 Oportunidad para mejorar habilidades y generar ideas con nuestros equipos  

---

## 🚀 Lista Final de Verificación  
✔️ Completa todos los prerrequisitos antes del evento  
✔️ Verifica tu acceso a **Azure**, **Microsoft Fabric** y **servicios de OpenAI**  
✔️ Confirma que puedes acceder a **todos los recursos y herramientas necesarias**  

---
# Requisitos Dia 2

# 🔐 Roles en Azure y su Uso

| **Rol en Azure** | **Uso Principal** |
|------------------|-------------------|
| **Owner o Contributor** | Permite **crear y administrar recursos** como *AI Services*, *Azure ML*, *App Services*, entre otros. |
| **Cognitive Services Contributor** | Habilita la **configuración y administración de recursos de Cognitive Services**. |
| **Storage Blob Data Contributor** | Brinda **acceso completo al almacenamiento** utilizado por *AI Foundry* (lectura, escritura y eliminación de blobs). |
| **Azure OpenAI Contributor (si aplica)** | Otorga **acceso a modelos GPT, embeddings y otros servicios** de *Azure OpenAI*. |
| **Key Vault Administrator (opcional)** | Permite **gestionar secretos, certificados y claves API** almacenadas en *Azure Key Vault*. |

## 🎉 ¡Nos vemos en el Hackathon!  
Esperamos un evento **dinámico e inspirador** — y sobre todo, una **experiencia de aprendizaje enriquecedora para todos**.  

Si tienes preguntas o necesitas asistencia, **no dudes en contactarnos**.  

> 🚀 ¡Prepárate para innovar, colaborar y construir soluciones potenciadas por IA! 🎉
