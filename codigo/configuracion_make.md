# Configuración del escenario en Make

El proyecto no usa código tradicional: se arma en Make (sin programar) con 4 módulos.
Nombre del escenario: `ClasificadorResiduos`.

Flujo: **Telegram Bot (Watch Updates) → Telegram Bot (Download a File) → Make AI Agent → Telegram Bot (Send a Text Message or a Reply)**

## 1. Telegram Bot → Watch Updates
- Connection: conexión del bot creado con @BotFather (el token **no** se incluye en este repositorio).
- Webhook: el que crea el propio módulo.

## 2. Filtro (entre Watch Updates y Download a File)
- Condición: `Message → Photo` **Exists**.
- Así el escenario solo corre cuando llega una foto.

## 3. Telegram Bot → Download a File
- Connection: la misma del bot.
- File ID:

```
{{last(map(1.message.photo; file_id))}}
```

Telegram manda cada foto en varios tamaños; `last()` toma la de mayor calidad.

## 4. Make AI Agent → Run an agent
- Connection: Make's AI Provider.
- Instructions: ver [`instrucciones_ai_agent.txt`](instrucciones_ai_agent.txt).
- Input: `Clasifica el residuo de las imagenes`
- Input files → File 1 → File: el archivo descargado en el módulo 3 (Telegram Bot - Download a File).
- Conversation ID: vacío.

## 5. Telegram Bot → Send a Text Message or a Reply
- Connection: la misma del bot.
- Chat ID: `1. Message: Chat: ID`
- Text: `4. Response` (respuesta del AI Agent).
- Message Thread ID: vacío.

## Consumo de créditos
Cada foto consume entre 4.2 y 4.3 créditos (4 operaciones). Ver `../imagenes/make/05_historial_creditos.png`.
