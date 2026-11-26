# scatto-agente-ia

Agente de atención al cliente para **Scatto**, marca argentina de soportes magnéticos MagSafe para rejilla de auto, construido en **n8n** con **Google Gemini**.

Es el proyecto integrador de la carrera **AI Automation Avanzado** de Coderhouse. Es un solo agente que crece módulo a módulo: cada checkpoint importa el workflow anterior y le suma solo los nodos nuevos.

| Módulo | Qué se suma | Carpeta | Estado |
|---|---|---|---|
| M1 | Agente base: Chat Trigger, AI Agent con System Prompt, 1 tool y log de observabilidad | [`m1-agente-base`](m1-agente-base/) | Entregado |
| M2 | Multi agente: manager y workers como sub workflows | `m2-multi-agente` | Pendiente |
| M3 | Memoria y contexto por Session_ID | `m3-memoria` | Pendiente |
| M4 | Integraciones reales vía OAuth2 (WhatsApp, CRM, calendario) | `m4-integraciones` | Pendiente |
| M5 | RAG con base documental | `m5-rag` | Pendiente |
| M6 | Voz (STT / TTS) | `m6-voz` | Pendiente |
| M11 | Proyecto Final Integrador | `final` | Pendiente |

## Stack

| Componente | Elección |
|---|---|
| Orquestador | n8n 2.43.4 self hosted (Docker en Windows), expuesto con ngrok |
| Modelo | Google Gemini Flash vía nodo Google Gemini Chat Model |
| Base de conocimiento | Google Sheets ("FAQ Scatto", columnas tema, respuesta, estado) |
| Observabilidad | Gmail (log por cada ejecución) |

### Por qué Gemini y no GPT-4o o Claude

La consigna sugiere OpenAI o Anthropic de forma preferente. Elegí Gemini porque ya lo usaba en el curso anterior con el mismo caso de negocio, tiene un plan gratuito suficiente para la etapa de desarrollo y soporta tool calling en paralelo, que el agente aprovecha cuando una consulta toca varios temas. En las pruebas, la versión Flash Lite inventó un plazo de entrega (ver más abajo), así que el agente usa la versión Flash, que respeta mejor las instrucciones con herramientas sin cambiar el orden de costo.

## Autor

Juan Carlos Stanghelini · [github.com/jcstanghelini](https://github.com/jcstanghelini)
