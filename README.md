# 🤖 Asistente Técnico de Alarmas de Incendio con IA (RAG)

Este repositorio contiene el **Trabajo Práctico Final** del curso de **Inteligencia Artificial con n8n** (Programa Tu Futuro / TECNO3F).

El proyecto consiste en un **Agente de IA** integrado en **Telegram** capaz de responder consultas técnicas especializadas sobre sistemas de incendio (marca INIM) y normativas vigentes, utilizando una arquitectura **RAG (Retrieval-Augmented Generation)**.

---

## 📋 Descripción del Proyecto

El sistema resuelve la necesidad de consultar manuales técnicos extensos de forma rápida. A través de un bot de Telegram, los técnicos pueden enviar preguntas (por texto o audios de voz) y recibir respuestas precisas basadas exclusivamente en la documentación oficial cargada en el sistema.

### Características Principales
* **Interfaz Chatbot:** Integración completa con Telegram.
* **Soporte Multimedia:** Transcripción automática de notas de voz a texto (Whisper/Gemini).
* **Motor RAG:** Búsqueda vectorial en documentos PDF para evitar alucinaciones de la IA.
* **Actualización Automática:** Sistema de "Ingesta" que detecta nuevos manuales en la nube y actualiza la base de conocimientos automáticamente.

---

## 🛠️ Arquitectura y Tecnologías

El proyecto se estructura en dos flujos de trabajo (Workflows) de **n8n**:

1.  **Backend de Ingesta (ETL):**
    * Monitorea una carpeta en **Supabase Storage**.
    * Extrae texto de archivos PDF/Docs.
    * Genera Embeddings y los guarda en **Supabase Vector Store**.
2.  **Frontend del Bot (Agente IA):**
    * Recibe mensajes de Telegram.
    * Orquesta la conversación con **LangChain**.
    * Consulta la base vectorial y genera la respuesta con un LLM.

### Stack Tecnológico
* **Orquestación:** [n8n](https://n8n.io/)
* **Base de Datos Vectorial:** [Supabase](https://supabase.com/) (PostgreSQL + pgvector)
* **LLM & Embeddings:** Cohere / Google Gemini
* **Interfaz:** Telegram Bot API

---

## 📂 Contenido del Repositorio

* `Tarea Final Miguel Flores20251120final.json`: **Workflow de Ingesta.** Se encarga de leer los documentos, fragmentarlos (chunks) y guardarlos en la base de datos vectorial.
* `TpFinaLn8nMiguelFlores20251120final2.json`: **Workflow del Bot.** Contiene la lógica del agente de IA, la memoria de conversación y la integración con Telegram.
* `Informe_Proyecto.pdf`: Documentación detallada del funcionamiento, lógica condicional y credenciales utilizadas.

---

## 🎓 Contexto del Curso

Este proyecto aplica los conocimientos adquiridos durante los 5 módulos del curso **"Inteligencia Artificial con n8n"**:

* **Módulo 1: Introducción**
    * Conceptos de automatización, Triggers y Nodos básicos (Gmail, Google Sheets).
* **Módulo 2: Inteligencia Artificial**
    * Nodos de IA, System Prompt, Tokens, Ventana de contexto y Memoria.
* **Módulo 3: HTTP + Webhooks**
    * Peticiones GET/POST, manejo de JSON y diferencias entre Polling y Webhooks.
* **Módulo 4: Integraciones y APIs**
    * Conexión con Telegram, WhatsApp (Evolution API) y otras herramientas externas.
* **Módulo 5: Trabajo Práctico Final (RAG)**
    * Implementación de **RAG** (Retrieval-Augmented Generation).
    * Generación de **Embeddings** y uso de **Bases de Datos Vectoriales**.
    * Estrategias de **Chunking** (fragmentación de textos).
