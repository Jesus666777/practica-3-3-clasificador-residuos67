# Práctica 3.3 – Clasificador de residuos por foto

Práctica de **Desarrollo Sustentable (ACD-0908)**, Ingeniería en Sistemas Computacionales.
Tema 3.3: Impacto de actividades humanas sobre la naturaleza.

**Autor:** Sanchez Gamboa Jesus

## ¿Qué es?
Un bot de Telegram que recibe la **foto de un residuo** y responde con inteligencia artificial: qué es, de qué material está hecho, cómo se clasifica, si se recicla, a dónde va y cuánto tarda en degradarse. Se armó sin programar, con **Telegram (BotFather)** y **Make (Make AI Agent con visión)**.

## Cómo funciona
`Telegram (Watch Updates)` → `Telegram (Download a File)` → `Make AI Agent` → `Telegram (respuesta)`

![Escenario completo en Make](imagenes/make/01_escenario_completo.png)

## Video
Demostración del bot funcionando: https://youtu.be/gZRNZdN_M0M

## Estructura del repositorio

| Carpeta / archivo | Contenido |
| --- | --- |
| `index.html` | Página principal con el resumen, el video, las pruebas y los resultados |
| `codigo/` | Instrucciones del agente de IA y configuración de cada módulo de Make |
| `imagenes/make/` | Capturas del escenario en Make y del historial de créditos |
| `imagenes/pruebas_bot/` | Capturas de las 10 pruebas con el bot |
| `video/` | Enlace al video de YouTube |
| `resultado/` | Reporte completo de la práctica (PDF y Word) |

## Resultados
Se probaron 10 residuos reales y se verificó cada respuesta contra fuentes confiables.

| # | Residuo | Clasificación de la IA | ¿Correcta? |
| --- | --- | --- | --- |
| 1 | Trapo de tela verde | Inorgánico reciclable | Parcial |
| 2 | Botella PET | Inorgánico reciclable | Sí |
| 3 | Zapato deportivo | Inorgánico no reciclable | Sí |
| 4 | Cable eléctrico con enchufe | Manejo especial o peligroso | Sí |
| 5 | Peluche | Inorgánico no reciclable | Sí |
| 6 | Desodorante en barra (envase) | Inorgánico reciclable | Sí |
| 7 | Lata de aluminio | Inorgánico reciclable | Sí |
| 8 | Folleto de papel | Orgánico | No |
| 9 | Bolsa de plástico | Inorgánico reciclable | Sí |
| 10 | Control remoto | Manejo especial o peligroso | Sí |

- **Aciertos de la IA en la clasificación: 80% (8 de 10).**
- **Consumo:** entre 4.2 y 4.3 créditos de Make por foto.
- La tabla completa (tiempos de degradación y fuentes), la investigación y las preguntas de reflexión están en [`resultado/Practica_3_3_Clasificador_de_residuos.pdf`](resultado/Practica_3_3_Clasificador_de_residuos.pdf).

## Seguridad
El **token del bot no está incluido** en este repositorio. Si quieres reproducir el proyecto, crea tu propio bot con @BotFather y usa tu token en la conexión de Make.

## Cómo reproducirlo
1. Crea un bot en Telegram con **@BotFather** (`/newbot`) y guarda el token.
2. En Make, crea el escenario con los 4 módulos descritos en [`codigo/configuracion_make.md`](codigo/configuracion_make.md).
3. Pega las instrucciones de [`codigo/instrucciones_ai_agent.txt`](codigo/instrucciones_ai_agent.txt) en el Make AI Agent.
4. Activa el escenario y mándale una foto de un residuo al bot.
