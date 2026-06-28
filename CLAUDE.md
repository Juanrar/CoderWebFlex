# Contexto del proyecto y rol de la IA

## Rol: TUTOR, no programador

Juan Carlos está aprendiendo HTML, CSS y SASS. Claude actúa como **tutor/mentor de frontend**, NO como agente que escribe código.

### Reglas estrictas para Claude

1. **NUNCA escribir, editar ni generar código** en los archivos del proyecto (HTML, CSS, SCSS, JS). Ni con herramientas de edición ni pegando bloques de código completos en el chat.
2. **SÍ se puede:** leer los archivos del proyecto para entender el contexto y dar feedback sobre el código que Juan Carlos escribió.
3. **Explicar la LÓGICA y el razonamiento**: ante una pregunta tipo "quiero mover esta imagen más arriba", la respuesta debe ser el *proceso mental* de un frontend:
   - ¿Qué elemento es y quién es su contenedor padre?
   - ¿Qué modelo de layout lo está posicionando (flujo normal, flexbox, grid, position)?
   - ¿Qué propiedades controlan ese comportamiento y por qué?
   - ¿Cómo lo inspeccionaría en DevTools para verificarlo?
4. **Dar sugerencias y pistas**, nombrar propiedades/conceptos relevantes (ej: "investigá `align-items` porque tu contenedor es flex"), pero que Juan Carlos escriba el código él mismo.
5. **Hacer preguntas socráticas** cuando ayude: "¿qué creés que pasa si...?", "¿qué te dice el inspector sobre ese elemento?"
6. Mostrar fragmentos mínimos de sintaxis SOLO si es imprescindible para explicar un concepto (ej: la sintaxis de un mixin de SASS que nunca vio), nunca la solución completa de su problema.
7. Responder en **español**.
8. Conectar las explicaciones con los requisitos de la entrega final (abajo) cuando sea relevante.

---

## Proyecto: Entrega final del curso (CoderHouse - Desarrollo Web)

Web estática **institucional/portfolio personal** en HTML + SASS.

### Requisitos de la entrega

**HTML (5 páginas):**
- `index.html` en la raíz + 4 páginas secundarias (en carpeta, ej: `pages/`).
- Contenido distintivo en cada página.
- Estructura prolija y legible, etiquetas semánticas (`header`, `nav`, `main`, `section`, `article`, `footer`...).
- SEO: `title` único por página, `meta description`, atributos `alt` en imágenes, jerarquía correcta de headings (un solo `h1` por página).
- Accesibilidad y performance (atributos que aporten a ambas, ej: `alt`, `loading="lazy"`).
- Las 5 páginas accesibles desde la nav en todo momento, con rutas relativas correctas.
- Linkear estilos y librerías (Bootstrap CSS/JS, librerías de animación) en todas las páginas.

**SASS (obligatorio, reemplaza al CSS plano):**
- Toda la estructura de estilos con el preprocesador.
- Aplicar: **nesting, partials, mixins, extend y variables**.
- Respetar estructura de carpetas vista en el curso (ej: `scss/` con partials, compilando a `css/`).

**Responsive design:**
- Adaptación a todos los dispositivos (media queries / mobile-first).

**Estilos avanzados:**
- Transformaciones, transiciones y/o animaciones.

**Identidad:**
- Si se usa Bootstrap, sobreescribir los estilos genéricos con la paleta e identidad propia.

**Repositorio y deploy:**
- GitHub con commits claros y precisos.
- Deploy en Vercel o Netlify.

**Optimización:**
- Imágenes optimizadas, compresión, CDN.

### Estado del proyecto — checklist de entrega (actualizar a medida que avance)

*Último análisis: 2026-06-28*

#### ✅ Lo que ya está hecho

- [x] `index.html` en la raíz con estructura base.
- [x] Header con logo y menú hamburguesa responsive (técnica checkbox + label, container queries).
- [x] Sección perfil ("Who is Juan Carlos Lorenzo?") con foto y barras de skills.
- [x] Sección portfolio con grid responsive, ahora con 4 proyectos REALES.
- [x] Sección contacto con formulario (nombre, apellido, email, mensaje) en grid-areas.
- [x] Nomenclatura BEM consistente en todo el CSS.
- [x] Responsive con container queries (header, profile, portfolio, form, project).
- [x] Etiquetas semánticas básicas: `header`, `nav`, `main`, `section`, `footer`.
- [x] Un solo `h1` por página.
- [x] `meta viewport` y `meta charset` presentes en las 5 páginas.
- [x] Repo en GitHub inicializado, rama `main`, commits descriptivos.
- [x] Algo de interactividad: `:hover` en proyectos del portfolio y links de nav.
- [x] **Las 4 páginas secundarias creadas** en `pages/`: `dance.html`, `feeder.html`, `beatmatch.html`, `assembler.html`.
- [x] **Contenido distintivo y real en cada página** (descripción de cada proyecto, sin Lorem ipsum), con semántica rica: `article`, `figure`, `dl/dt/dd`, `video` (assembler).
- [x] **Portfolio enlaza a las páginas reales** (`pages/*.html`) y cada subpágina tiene link "Back" al index + logo clickeable al home.
- [x] `title` único por página (cada subpágina tiene su propio `<title>`).
- [x] **Nav del index funcional**: links About/Contact saltan a anclas reales (secciones con `id="about"`/`id="contact"`); el ítem "projects" es un **dropdown** que despliega las 4 páginas de proyectos.
- [x] **Dropdown de proyectos sin JS** (técnica checkbox+label anidada): en mobile abre con tap (`input:checked ~ ul`), en desktop flota al estar abierto (`position: absolute`, `top:100%`, `right:0` para no salirse de pantalla) con fondo, padding, sombra y `border-radius`. Rutas relativas correctas a `pages/*.html`.
- [x] **Nav completa replicada en las 5 páginas** (las 4 subpáginas + `contact.html` tienen la nav de 5 destinos, no solo el "Back"). Rutas relativas correctas (`../index.html#about`, `dance.html`, logo envuelto en `<a href="../index.html">`). **Cierra el requisito "5 páginas accesibles desde la nav en todo momento".**
- [x] **`contact.html` pasó a página propia** (ya no es ancla `#contact`): el index la enlaza vía `pages/contact.html`.
- [x] **Bugs de `contact.html` resueltos**: agregado el `<h1 class="form__title">CONTACT</h1>` (antes la página no tenía `h1`) y cerrado el `</body>` que faltaba. Bonus: se le sumó `<footer>` para quedar consistente con el resto.

#### ❌ HTML / Páginas (pendiente)

- [ ] **`<main>` en `contact.html`**: el formulario entra directo con `<section class="form">`, sin envolver en `<main>` como hacen las otras 4 subpáginas. Detalle semántico (consistencia + accesibilidad), no bloquea.
- [ ] **Estado activo** en la nav (marcar la página/sección actual) — opcional, suma puntos.
- [x] **Idioma unificado a inglés (2026-06-24)**: corregido el `¿Who is...` del index, los `<h2>Descripcion</h2>` de assembler/dance, y las labels del form (`Name/Last Name/Email/Message`). Todo coherente con `lang="en"`.
- [x] **Tipos de input correctos en el form (2026-06-25)**: `contact.html` ya usa `type="email"`, `name` en los 4 inputs (name/lastname/email/message) y `required` en todos. Verificado.

#### ✅ SEO y accesibilidad (COMPLETADO 2026-06-24)

- [x] **`meta name="description"` única y descriptiva en las 5 páginas** (~150 caracteres, en inglés coherente con `lang="en"`). Ojo histórico: primero quedaron con `name="project"/"contact"` (nombres inventados que Google ignora) → corregido a `name="description"`.
- [x] **`alt` en TODAS las imágenes**, según qué describe cada una: logos = destino del link ("Go back / Go to the main menu"), foto de perfil, y cada demo describe su captura concreta (no genérico "Project image"). Se quitó la palabra redundante "image".
- [x] **Texto alternativo del `<video>` de assembler** vía `aria-label` (typo `aria-lebel` detectado y corregido).
- [x] **`loading="lazy"`** aplicado SOLO a imágenes bajo el fold (3 demos + foto de perfil); **se quitó de los logos** (above the fold, era anti-patrón).
- [x] **Favicon** en las 5 páginas (`<link rel="icon" href="...hacker.png">`, rutas relativas correctas `./assets/` vs `../assets/`).

**Pendiente menor de SEO/accesibilidad:**
- [ ] Revisar si la foto de perfil del index queda above-the-fold en desktop (si se ve sin scrollear, conviene quitarle el `lazy`).
- [ ] (Opcional/plus) Open Graph, atributos ARIA donde sumen.

#### ✅ SASS (requisito central — los 5 pilares CUMPLIDOS)

- [x] Compilador SASS configurado (Dart Sass vía npm, script `dev` con `sass ./scss/main.scss:./css/styles.css --watch`).
- [x] Estructura de carpetas `scss/` con partials (`base/` y `components/`), compilando a `css/styles.css`.
- [x] Migrar a SCSS: header, profile, portfolio, form, footer y reset (base) ya migrados.
- [x] Aplicar **variables** (`_variables.scss` con `$color-primario`, `$color-superficie`, `$color-oscuro`; colores con transparencia vía funciones de color).
- [x] Aplicar **nesting** (bloques BEM con `&`, container queries anidadas que "burbujean").
- [x] Aplicar **partials** (`_variables`, `_mixin`, `_extend`, `_reset`, `_header`, `_profile`, `_portfolio`, `_form`, `_footer`, `_project`; `_responsive` existe pero está vacío, ver abajo).
- [x] **mixins**: `flex-center` creado y usado en `.form`.
- [x] **extend**: `%barra-base` en `_extend.scss`, aplicado en `.load-bar__bar` (verificado en `styles.css`: estilos en la barra, `.profile` limpio).
- [x] **Switch del `<link>`** a `styles.css` HECHO (las 5 páginas apuntan a `styles.css` con ruta relativa correcta: `./css/` en index, `../css/` en subpáginas).
- [x] Partial `_project.scss` creado (estilos de las subpáginas, container queries propias) y linkeado en `main.scss`.
- [x] **`oldstyles.css` eliminado** — solo queda `css/styles.css` compilado.

**Pendientes menores de SASS (pulido, no bloquean la entrega):**
- [ ] Mixin `responsive($medida)` con `@content` para reemplazar las `@container ... (min-width)` repetidas. `scss/base/_responsive.scss` existe pero sigue **VACÍO** (falta escribir el mixin, aplicarlo y agregar el `@use` en `main.scss`).

*Notas de la sesión 2026-06-16:* se aprendió y aplicó nesting, `&`, `@use` (scoping por archivo + `as *`), burbujeo de at-rules, comentarios `//` vs `/* */`, mixins (`@include`), extend con `%placeholder`, y rutas relativas de `@use` (mismo nivel = solo nombre; `../` para subir). Bugs recurrentes detectados y resueltos: estilos de escritorio en la capa base (patrón mobile-first), rutas de `@use` con carpeta duplicada, y `@extend` suelto que aplicaba estilos al selector padre equivocado.

*Notas de la sesión 2026-06-23 (nav del index):* se construyó el menú con dropdown de proyectos. Conceptos trabajados: anclas (`href="#id"` ↔ `id` en la sección destino), reutilización de la técnica **checkbox + label** anidada para un toggle sin JS (`for`↔`id` únicos; el combinador hermano `~` exige que la `ul` vaya DESPUÉS del input), reparto mobile (tap/`:checked`) vs desktop (flotante con `position: absolute`). Bugs detectados y resueltos: rutas absolutas `/pages/` (deben ser relativas `pages/`), typo BEM `&_nav-item` (un guion) vs `&__nav-item` (dos), `display:none` puesto en la capa equivocada, y el clásico **falso "tapado por z-index"** que en realidad era **clipping horizontal** (el submenú se salía del viewport → se resolvió con `right:0` para que crezca hacia la izquierda). Pendiente que quedó abierto: dar color/`cursor:pointer` al `<label>` "projects" (no lo agarra la regla `&__nav-item a`).

*Notas de la sesión 2026-06-24 (nav en subpáginas + SEO/accesibilidad):* se replicó la nav completa a las 5 páginas y se cerró entero el bloque de SEO. Conceptos trabajados: el atributo **`name`** de un `<meta>` es la "llave" que el buscador reconoce (inventar `name="project"` = ignorado; solo `name="description"` cuenta); una meta description es **copywriting** (~150 chars, frase real, no etiqueta de 2 palabras), comprimible a partir del propio `<h1>`+`<p>` de cada página. Sobre `alt`: describe el **contenido/función**, nunca el tipo ("image" es redundante, el lector de pantalla ya lo anuncia); cuando la imagen es el único hijo de un `<a>`, el `alt` nombra el **destino del link**; `<video>` no lleva `alt` → se usa `aria-label`. Sobre performance: `loading="lazy"` solo para imágenes **fuera de la pantalla inicial** (ponérselo a un logo above-the-fold es contraproducente). Favicon vía `<link rel="icon">` (mismo patrón que el `<link rel="stylesheet">`). Bugs recurrentes de esta sesión: **el texto correcto en el lugar equivocado** (descripción del proyecto metida en el `alt` del logo en vez del `content` del meta), y **typos que anulan atributos** (`aria-lebel`, `name="project"`) — el patrón de fondo es siempre el mismo: la llave mal escrita = atributo muerto. También se arreglaron los bugs estructurales de `contact.html` (faltaba `h1` y `</body>`).

#### 🟡 Bootstrap y librerías (parcial)

- [x] **Bootstrap linkeado en las 6 páginas (2026-06-25)**: CSS en el `<head>` (Bootstrap 5.3.3 vía CDN jsDelivr) y JS bundle antes de `</body>` con `integrity` + `crossorigin`. Verificado en index + las 5 de `pages/`.
- [x] **Componentes Bootstrap en uso (2026-06-25)**: `contact.html` usa grid (`container`, `row g-3`, `col-md-6`, `col-12`), `form-control`, `form-label`, `btn btn-primary`. Cumple el "usar al menos algunos componentes".
- [ ] **Override de identidad (PARCIAL, 2026-06-28)**: ya se pisó el `background-color` del `.btn-primary` con `$color-primario` (regla anidada en `.form` dentro de `_form.scss:12`). PENDIENTE completar la identidad del botón: el `border-color` sigue azul de fábrica y los estados `:hover`/`:focus`/`:active` de Bootstrap vuelven a pintarlo de azul (hay que pisar también esas pseudoclases). Idealmente sacar la regla de adentro de `.form` para que el override aplique a cualquier `.btn-primary` del sitio, no solo al del formulario.
- [ ] Librería de animaciones (ej: AOS, Animate.css) linkeada y aplicada.

#### ✅ Estilos avanzados (COMPLETADO 2026-06-28)

- [x] **Transiciones (2026-06-28)**: el dropdown de proyectos ahora aparece con fade (`opacity` + `visibility` + `transition` en la regla base del `ul`, no en `:checked`); el hover de las tarjetas del portfolio (`&__project`) anima `opacity`/`outline`/`transform`. Resuelto el clásico "`display` no se anima" pasando a `opacity`/`visibility`.
- [x] **Transformaciones (2026-06-28)**: hover de las tarjetas del portfolio con `transform: scale(1.02)` (efecto real de UI, no el `translateY` de centrado del header).
- [x] **Animación con `@keyframes` (2026-06-28)**: barras de skills se llenan al cargar. `@keyframes chargeBar { from { width: 0 } }` (sin `to`, para que cada `.bar--XX` use su propio ancho como estado final) aplicado vía `animation` en `.load-bar__bar`.

#### ❌ Optimización y deploy (pendiente)

- [ ] **Optimizar imágenes (PARCIAL, 2026-06-25)**. Foto de perfil `IMG-20211212-WA0074.jpg` ya en ~235 KB (mejorada). PENDIENTE el grueso del peso: `demoFeeder.png` ~922 KB 🔴 y `demoDance.png` ~686 KB 🔴 (PNG sin pérdida para capturas = anti-patrón; comprimir o pasar a JPG/WebP — comparar con `demoBeatmatch.png` que pesa solo ~169 KB siendo la misma naturaleza). `demoAssembler.webm` ~175 KB ok.
- [x] **Deploy hecho (2026-06-28)** en Vercel/Netlify (conectado al repo de GitHub, sin archivo de config en el repo — para un sitio estático no hace falta).
- [ ] Verificar rutas relativas de imágenes y links en todas las páginas una vez deployado.

### Convenciones del proyecto

- Nomenclatura de clases: BEM (`bloque__elemento--modificador`).
- Imágenes en `assets/`.
