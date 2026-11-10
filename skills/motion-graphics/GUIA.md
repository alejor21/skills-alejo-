# Guía: motion graphics comerciales con `saas-animation`

Resumen en español de [saas-animation](./saas-animation/SKILL.md) y de cómo usarla para anuncios de empresas (cada una con su logo, su tipografía y su estilo).

## Cómo se usa (paso a paso)

1. Crea una carpeta por anuncio, por ejemplo `clientes/acme-launch/`.
2. Mete ahí los ingredientes reales: logo en alta resolución (SVG o PNG grande), tipografía de la marca, colores, guía de marca si existe y capturas reales de la app o fotos del producto desde todos los ángulos.
3. Dale a Claude acceso a esa carpeta y pide el anuncio.
4. Claude entrega primero un **storyboard numerado** (5 a 10 planos, cada uno con tiempo, frame con assets reales, texto en pantalla, qué se mueve y cómo se transforma en el siguiente). Se aprueba o se corrige ("la transición del 4 al 5 no funciona") antes de animar nada: es el paso más barato para cambiar cosas.
5. Claude construye, revisa fotogramas como un motion designer y renderiza en 4K.
6. Solo con la imagen aprobada se añade sonido (efectos sincronizados con los beats), música y voz en off. Cambiar la animación después mueve todos los beats.

## Los tres niveles

| Nivel | Para qué | Herramienta |
|---|---|---|
| 1. Solo assets | Apps y software: UI real volando en 3D | `templates/template-3d.html` (WebGL) o three.js |
| 2. Arte y voz de marca | Marcas con ilustraciones o personajes (puppet animation) | `templates/template-2d.html` |
| 3. Blender | Producto físico con luz realista, look de estudio | `scripts/blender/` (Blender corre sin abrirse) |

## Las reglas que hacen que se vea premium

- Cada plano **se transforma** en el siguiente (morph de forma), nunca un fundido cruzado.
- Lo importante, **centrado**. Siempre hay algo moviéndose, aunque sea un leve empuje de cámara.
- La dirección del movimiento **nunca se invierte** (nada de zoom in y luego zoom out). Una curva continua por movimiento.
- **Rápido y luego lento por más tiempo.** Los primeros borradores casi siempre van demasiado rápido.
- Texto con la tipografía de la marca, frases cortas, palabra por palabra de borroso a nítido con una pequeña subida. Sin rebotes.
- **Una sola fuente de luz** y poca profundidad de campo: es lo que da el look cinematográfico.
- UI real y limpia (sin datos personales ni badges de notificación).
- Un **llamado a la acción** claro al final (App Store, URL, registro).

## Antes de publicar

- Solo marcas propias o con permiso. Un anuncio "spec" de otra marca (Apple, Spotify, Google...) es pieza de portafolio: lleva al final "Spec ad. Not affiliated with <marca>.", no imita sus campañas y no se pauta.
- Solo assets con licencia (fuentes, música, modelos 3D, footage).
- Todo lo que se dice debe ser verdad: nada de cifras, reseñas o garantías inventadas.

## Requisitos de la máquina

Node 18+, Python 3 con Pillow, numpy, scipy y opencv-python, ffmpeg, Google Chrome o Chromium. Para el nivel 3, Blender oficial de blender.org (las versiones de algunos repositorios de Linux vienen sin el denoiser que usa `kit.py`). Los servicios de pago (ElevenLabs, Suno) solo se usan cuando se pide, porque gastan créditos.
