# Institute of the Self — ESSENCE for Companies

Sitio estático en una sola página (`index.html`) para presentar la metodología IF Loop, diagnóstico Self Scan, talleres y mentoría. Incluye animaciones suaves y micro‑interacciones.

## Arranque rápido

- Opción 1: abrir directamente `index.html` en el navegador.
- Opción 2: servidor local (PHP embebido):

```bash
php -S 127.0.0.1:8000
# Navega a http://127.0.0.1:8000/
```

## Estructura

- `index.html`: el sitio completo (HTML + CSS + JS).
- `img/`: imágenes usadas en el sitio.
  - `Logo.png`: logo para el splash.
  - `3.png`, `4.png`: imágenes del collage del hero (intercambiables al hacer clic).
  - `card1.png`, `card2.png`, `card3.png`: cards de la sección “Qué ofrecemos”.
- `EMPRESA/`: material gráfico adicional (no referenciado directamente).

## Secciones y funcionalidades

- Hero
  - Dos columnas: texto (izquierda) y collage visual (derecha).
  - Chips informativos bajo el CTA.
  - Collage interactivo: al hacer clic (o Enter/Espacio) alterna qué imagen queda al frente.
  - Indicador “Ver más” enlaza a `#espera`.

- Qué te espera (`#espera`)
  - Listado con cuatro puntos, estilo numerado.

- Qué ofrecemos (`#oferta`)
  - Tres tarjetas con imagen y descripción: Self Scan, Talleres, Mentoría.
  - Animación de entrada con `IntersectionObserver`.

- IF Loop (`#ifloop`)
  - Pilares con acordeón simple.
  - Apertura automática de “SABER” al entrar en viewport.

- Cómo funciona (`#proceso`)
  - Título grande en mayúsculas y lista animada al hacer scroll.

- Impacto (`#impacto`)
  - Barras con porcentajes en modo “Antes/Después”.
  - “Antes” se muestra por defecto al entrar la sección en viewport.

- Preguntas frecuentes (`#faq`)
  - Fondo oscuro (`#1E2025`) con contraste ajustado.
  - Filtros por chips: Todas, Proceso, Metodología, Logística.
  - Acordeón minimal con +/−.

- Contacto (`#contacto`)
  - Callout oscuro con dos CTAs (correo).

## Barra de navegación

- Enlaces y anclas:
  - `Inicio` → `#inicio`
  - `Qué ofrecemos` → `#oferta`
  - `IF Loop` → `#ifloop`
  - `Cómo funciona` → `#proceso`
  - `Impacto` → `#impacto`
  - `Preguntas frecuentes` → `#faq`
  - `Contacto` → `#contacto`
- Separación lateral: `.nav-wrap .container { padding: 0 16px; }`

## Personalización rápida

- Cambiar imágenes del hero:
  - Edita las rutas en el bloque del hero:
    - `img/3.png` (clase `collage-a`)
    - `img/4.png` (clase `collage-b`)

- Duración del splash de carga:
  - CSS: `.splash-fill { animation: progress 4s ... }`
  - JS: busca “Splash: duración 4s y salida suave” y ajusta `const DURATION_MS = 4000;`
  - Ideal mantener ambos valores sincronizados.

- Estado inicial de Impacto (Antes/Después):
  - En el script “Impacto: toggle Antes/Después…”, cambia `applyMode('antes', true)` por `'despues'` si lo deseas.
  - Porcentajes se controlan con atributos `data-before` y `data-after` en `.impact-fill`.

- Filtros FAQ:
  - Cada `.faq-item` tiene `data-group` con valores `proceso`, `metodologia`, `logistica`.
  - Ajusta o añade categorías según necesites.

- Colores y estilo base:
  - Variables en `:root`:
    - `--primary`, `--secondary`, `--text`, `--text-light`, `--muted`, `--line`, `--accent`.

## Accesibilidad

- Collage del hero: `role="button"`, `tabindex="0"`, alterna con teclado (Enter/Espacio).
- Navegación con `scroll-behavior: smooth`.
- Imágenes con `alt` descriptivo.

## Deploy

- Es un sitio estático: sube la carpeta completa a cualquier hosting estático (Netlify, Vercel, S3, o servidor tradicional).
- Asegúrate de mantener la estructura de carpetas y rutas relativas.

## Notas

- Breakpoints principales a `max-width: 980px` y `960px` (oferta).
- Probado en navegadores modernos; animaciones usan `IntersectionObserver` y transiciones CSS.