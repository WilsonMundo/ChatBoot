# 🤖 Bot de Inventario con IA (Detección de Productos Electrónicos)

Este proyecto implementa un bot de Telegram que recibe imágenes, detecta si representan productos electrónicos (como celulares, laptops, audífonos, etc.), y devuelve una descripción estructurada con precio estimado y cantidad en stock. Todo esto se realiza automáticamente a través de un flujo visual usando [n8n](https://n8n.io/), la API de Telegram y el modelo Gemini de Google.

---

## 📸 Funcionalidad

1. El usuario envía una imagen por Telegram.
2. El flujo detecta si contiene una foto.
3. Se descarga la imagen desde Telegram.
4. Se envía a Gemini con un prompt para análisis visual.
5. La IA determina si la imagen representa un producto.
6. Si lo es, se responde al usuario con:
   - Nombre
   - Categoría
   - Descripción
   - Precio estimado
   - Existencia aleatoria
7. Se registra el evento en una base de datos SQL.
8. Se reinicia el flujo para procesar la siguiente imagen.

---

## 🚀 ¡Probar el bot ahora!

Puedes probar el bot directamente desde Telegram:  
👉 [https://t.me/ecommerce_ai_umg_bot](https://t.me/ecommerce_ai_umg_bot)

📌 **Límite:** Cada usuario puede procesar hasta **6 imágenes** durante el período de prueba.

---

## 🧠 Tecnologías utilizadas

- **n8n** para orquestación del flujo
- **Telegram Bot API** para recibir y responder mensajes
- **Google Gemini (AI Studio)** como modelo de análisis de imágenes
- **Microsoft SQL Server** para persistencia de datos de usuarios

---

## 📂 Archivos importantes

| Archivo/Carpeta          | Descripción |
|--------------------------|-------------|
| `workflow.json`          | Export del flujo visual (n8n compatible) |
| `scripts/code_nodes.js`  | Código de nodos personalizados (`Code`) |
| `scripts/prompt.md`      | Prompt utilizado por el modelo IA |
| `sql/estado_usuarios_telegram.sql` | Script de base de datos para seguimiento de usuarios |
| `flujo.png`  | Diagrama opcional del flujo |
| `flujo.png`| Captura del flujo visual |

---

## ⚙️ Requisitos

- Cuenta activa en [n8n](https://n8n.io/) (self-hosted o cloud)
- Bot de Telegram con token válido
- Acceso a Google AI Studio o Vertex AI con Gemini habilitado
- SQL Server disponible (local o en la nube)

---

## 📦 Instalación

1. Clona este repositorio:

```bash
git clone https://github.com/tuusuario/bot-inventario-electronica.git
cd bot-inventario-electronica

## 🧱 Script completo de base de datos

Si estás usando SQL Server en entorno local o Docker, puedes usar el script completo:

➡️ `sql/full_setup_chatbotumg.sql`

Este script:
- Crea la base de datos `ChatBotUMG`
- Aplica configuraciones comunes de SQL Server
- Crea la tabla `[dbo].[estado_usuarios_telegram]` con campos y defaults
## 🔄 Flujo del proceso

A continuación se muestra una vista general del flujo del bot desde la recepción de una imagen hasta la respuesta y actualización del estado del usuario:

![Flujo del Bot](https://raw.githubusercontent.com/WilsonMundo/ChatBoot/refs/heads/main/Flujo.jpg)


🧪 Ejemplo de salida esperada
📦 *Producto detectado*
📱 *Nombre*: Smartphone Honor Magic 5 Pro
📂 *Categoría*: Teléfono celular
📝 *Descripción*: Smartphone de alta gama con sistema de cámara avanzado y diseño elegante
💰 *Precio*: Q8500.00
📦 *Existencia*: 62


