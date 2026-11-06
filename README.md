OCULA — Cursor Controlado por la Mirada (Versión en Español)
Un dispositivo de entrada asistivo libre, de código abierto y basado en navegador web. Permite mover el cursor con la mirada y activar acciones mediante fijación (dwell-to-click). Sin hardware especializado ni instalaciones complejas: solo con una cámara web estándar.

Licencia: MIT | MediaPipe Face Mesh | Accesibilidad | Open Source
|---|---|
🚀 Demo en Vivo
El proyecto se encuentra desplegado y funcional en:
https://oculaesp.netlify.app/
📌 ¿Qué es OCULA?
OCULA es una solución de tecnología asistiva de código abierto construida en un único archivo web. Utiliza la cámara web integrada de una notebook o PC junto con MediaPipe Face Mesh para estimar la dirección de la mirada, suavizar la señal mediante filtros matemáticos y permitir "hacer clic" fijando la vista sobre un objetivo durante una fracción de segundo.

Esta versión adaptada al español incorpora un tablero CAA (Comunicación Aumentativa y Alternativa) de 6 tarjetas esenciales con síntesis de voz automática (Text-to-Speech) en español y pictogramas visuales integrados.
💡 ¿Por qué existe este proyecto?
Los sistemas comerciales de seguimiento ocular dedicados (como Tobii) tienen costos que oscilan entre USD 200 y más de USD 3.000, además de requerir controladores propietarios, adaptadores y software exclusivo para determinados sistemas operativos. Muchas personas que podrían beneficiarse directamente del control visual —pacientes con ELA (esclerosis lateral amiotrófica), personas con lesiones por esfuerzo repetitivo (RSI), parálisis cerebral en etapas avanzadas o lesiones temporales en extremidades superiores— quedan frecuentemente excluidas por barreras económicas.

OCULA es un proyecto abierto de investigación y educación que demuestra que una solución asistiva gratuita, sin instalación y que funcione directamente desde una pestaña del navegador web es viable en hardware accesible.
✨ Características Principales
Estimación de mirada solo con cámara web: no requiere infrarrojos (IR) ni cámaras especiales.
Tablero CAA en Español: 6 tarjetas de necesidades básicas con pronunciación automática vía Web Speech API (speechSynthesis).
Fijación de mirada (Dwell-to-click): activación automática tras sostener la vista en un objetivo (con anillo de progreso visual).
Calibración en pantalla: sistema de calibración afín de 5 puntos para alinear la mirada a la pantalla.
Suavizado exponencial: filtro paso bajo en las coordenadas de pantalla para mantener la estabilidad del cursor visual.
Aviso de pérdida de rostro: detección y alerta cuando el usuario se desplaza fuera del cuadro de la cámara.
Recalibración dinámica: opción para recalibrar en cualquier momento sin recargar la página.
100% del lado del cliente: ningún fotograma, coordenada ni dato biométrico sale del navegador.
📋 Pictogramas y Mensajes del Tablero CAA
Tarjeta
Mensaje Vocalizado
Propósito del Mensaje
1
Necesito ayuda
Alerta rápida para requerir asistencia inmediata.
2
Tengo sed
Solicitud de hidratación y agua.
3
Estoy feliz
Comunicación de estado de ánimo positivo y bienestar.
4
Necesito descansar
Indicación de fatiga o solicitud de reposo.
5
Quiero a mi familia
Expresión afectiva y llamada a los cuidadores o familiares.
6
Tengo hambre
Solicitud directa de alimentación.

⚙️ ¿Cómo funciona internamente?
Captura de video: Adquisición continua del flujo visual vía MediaPipe Camera Utils.
Malla facial e iris: Detección y extracción de malla mediante MediaPipe Face Mesh (468 puntos faciales más puntos clave de iris 468 y 473).
Vector de mirada: Cálculo del vector relativo de cada iris respecto al contorno de la cuenca ocular.
Transformación afín: Mapeo calibrado de 5 puntos hacia las coordenadas absolutas $(x, y)$ de la pantalla.
Filtrado paso bajo: Suavizado exponencial para amortiguar el temblor involuntario y micro-sacadas oculares.
Temporizador Dwell: Al posar el cursor sobre un elemento interactivo durante el umbral fijado, se dispara el evento y se emite la voz en español.
🖥️ Requisitos y Recomendaciones de Uso
Distancia recomendada: Ubicarse entre 50 y 70 cm de la cámara web.
Estabilidad postural: Mantener la cabeza razonablemente quieta; desplazamientos excesivos del torso o cuello desfasan la estimación angular.
Iluminación: Luz frontal homogénea sobre el rostro. Evitar contraluces severos y ventanas detrás del usuario.
Dispositivos óptimos: PC de escritorio o notebook con pantalla fija. En tablets se aconseja soporte rígido en orientación horizontal. No se recomienda sostener teléfonos a mano alzada.
Navegadores compatibles: Chrome 120+, Edge 120+, Safari 17+, Firefox 121+ (cualquier entorno con soporte WebAssembly SIMD y API getUserMedia).
⚠️ Limitaciones Conocidas (Aviso Honesto)
No es un dispositivo médico: Se trata de un prototipo experimental, educativo y de investigación abierta.
Compensación de postura cefálica: No compensa actualmente rotaciones pronunciadas de la cabeza sin una recalibración posterior.
Resolución angular: Precisión típica de 3 a 5 grados de ángulo visual. Excelente para botones grandes (como el tablero de 6 tarjetas), pero no apto para lectura de texto fino ni teclados virtuales compactos.
Factores ópticos y ambientales: Reflejos en cristales de anteojos, penumbra o lentes gran angular tipo ojo de pez pueden degradar el seguimiento.
📥 Puesta en Marcha Local
Para clonar y desplegar el proyecto en tu entorno local:

Clonar el repositorio:

git clone <URL_DEL_REPOSITORIO>

Acceder a la carpeta del proyecto:

cd ocula

Iniciar un servidor HTTP local (requerido para habilitar permisos de cámara sin restricciones de seguridad de origen cruzado):

python3 -m http.server 8080

Abrir en el navegador web:

http://localhost:8080

Conceder permisos a la cámara web y realizar un clic inicial en cualquier parte de la ventana para desbloquear la API de síntesis de voz (AudioContext/SpeechSynthesis).
🔒 Privacidad y Seguridad
Todo el procesamiento de visión artificial, detección de iris y cálculo de mirada corre estrictamente en la memoria volátil local de tu navegador. Ningún fotograma de video, imagen ni dato biométrico se almacena ni se transmite a servidores externos.
📄 Licencia
Publicado bajo la Licencia MIT. Libre para uso personal, educativo, clínico y comercial.



# OCULA — Eye-Controlled Cursor

> A free, browser-based assistive input device.
> Move the cursor with your gaze. Dwell to click. No special hardware, no install — just your webcam.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![MediaPipe Face Mesh](https://img.shields.io/badge/MediaPipe-Face%20Mesh-4285F4.svg)](https://developers.google.com/mediapipe)
[![Accessibility](https://img.shields.io/badge/A11y-AAC%20demo-5eead4.svg)](#)
[![Open Source](https://img.shields.io/badge/Open%20Source-%E2%9D%A4-red.svg)](#)

---

## What is it?

OCULA is an open-source **eye-tracking cursor** built as a single HTML file. It uses your laptop webcam and MediaPipe Face Mesh to estimate where you're looking, smooths the signal, and lets you "click" by **dwelling** on a target for a fraction of a second.

The included demo is a 6-tile **AAC (Augmentative and Alternative Communication) board** — proof that a no-hands, no-hardware communication aid can run in a tab.

## Demo

Open `index.html`, allow camera access, run the 5-point calibration, and start gazing.

## Why it exists

Dedicated eye trackers like Tobii cost USD 200–3000+ and require drivers, dongles, and Windows software. Many people who would benefit from gaze input — ALS patients, RSI sufferers, late-stage cerebral-palsy users, anyone with a temporary arm injury — never get access.

OCULA is a **research / educational** project showing that "good enough for an AAC board, browser-only, free" is achievable on a 2019-era laptop.

## Features

- **Webcam-only gaze estimation** — no IR, no special camera
- **5-point on-screen calibration** with progress feedback
- **Dwell-to-click** with adjustable speed (fast / medium / slow)
- **Visual cursor** with progress ring showing dwell fill
- **AAC communication board** demo — 6 large gaze-clickable tiles
- **Recalibrate** without reloading
- **Face-not-detected warning** when the user moves out of frame
- **Welcome → calibrate → tracking** state machine with proper transitions
- Fully **client-side** — no frames or landmarks leave the browser

## Quick start

```bash
# 1. Just open it
open index.html

# 2. Or serve it (recommended — some browsers restrict camera on file://)
python3 -m http.server 8080
# then visit http://localhost:8080
```

1. Click **Begin**.
2. Look at each of the 5 calibration dots until the ring fills.
3. The AAC board appears. Look at a tile — when the cursor's progress ring fills (default 0.8 s) the tile activates.
4. Use the **Speed** button to cycle dwell time. Use **Recalibrate** if accuracy drifts (e.g. you moved).

## How it works

```
Webcam ──▶ MediaPipe Face Mesh ──▶ Iris + eye-corner landmarks
                                          │
                                          ▼
                                 Per-eye gaze vector
                                          │
                                          ▼
            5-point affine calibration → screen (x, y)
                                          │
                                          ▼
                       Exponential smoothing → cursor
                                          │
                                          ▼
                  Dwell timer per hovered tile → click
```

- **MediaPipe Face Mesh** gives 468 face landmarks at video frame rate, including dedicated iris landmarks.
- The relative position of each iris inside its eye socket is mapped to screen space via a calibration captured from 5 known points.
- A low-pass filter on the screen coordinates keeps the cursor stable.
- Hovering over a `.gaze-clickable` element starts a dwell timer; on completion the element's `data-action` fires.

## Calibration tips

- Sit roughly 50–70 cm from the camera.
- Keep your head reasonably still during calibration — head pose isn't compensated yet.
- Good even lighting on your face helps a lot. Backlight = bad.
- Recalibrate any time you change posture significantly.

## Limitations (honest list)

OCULA is not a medical device. It's a fun, open prototype.

- **No head-pose compensation** — moving your head shifts the gaze estimate.
- **Accuracy is roughly ~3–5 °** of visual angle, enough for 6 large tiles, not enough for general text input.
- **Webcam-dependent** — low light, glasses with strong reflections, or fish-eye lenses will degrade accuracy.
- Not benchmarked against clinical eye trackers.

PRs that improve any of the above are very welcome.

## Tech stack

- [MediaPipe Face Mesh](https://developers.google.com/mediapipe) `0.4` — face + iris landmarks
- [MediaPipe Camera Utils](https://developers.google.com/mediapipe) `0.3` — webcam plumbing
- Vanilla HTML / CSS / JS — no framework, no bundler, no npm

## Browser support

Works in any browser with `getUserMedia` + WASM SIMD. Tested on:
- Chrome 120+ (desktop)
- Edge 120+
- Safari 17+
- Firefox 121+

Mobile browsers technically run it but accuracy is poor — the demo is desktop-first.

## Privacy

Everything — face detection, iris tracking, calibration, smoothing — runs **inside your browser tab**. No camera frames, landmarks, or coordinates are uploaded anywhere. There is no backend.

## Roadmap / Ideas

- Head-pose decoupling (use full mesh, not just iris-in-socket)
- Saccade vs. fixation classifier instead of fixed dwell time
- On-screen keyboard with word prediction
- 9-point or 13-point calibration option
- Export gaze trace for research use

## Contributing

Issues and PRs welcome. This project is meant to be hacked on — please consider sharing improvements upstream so the broader accessibility community benefits.

## License

[MIT](LICENSE) — free for personal, educational, clinical, and commercial use.

## Credits

Built as an open experiment in webcam-only assistive tech. If OCULA helped you or someone you know, please open an issue and tell the story — it informs the roadmap.
