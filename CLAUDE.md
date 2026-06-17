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

*Último análisis: 2026-06-16*

#### ✅ Lo que ya está hecho

- [x] `index.html` en la raíz con estructura base.
- [x] Header con logo y menú hamburguesa responsive (técnica checkbox + label, container queries).
- [x] Sección perfil ("¿Quién es Juan Carlos Lorenzo?") con foto y barras de skills.
- [x] Sección portfolio con grid responsive (4 proyectos placeholder).
- [x] Sección contacto con formulario (nombre, apellido, email, mensaje) en grid-areas.
- [x] Nomenclatura BEM consistente en todo el CSS.
- [x] Responsive con container queries (header, profile, portfolio, form).
- [x] Etiquetas semánticas básicas: `header`, `nav`, `main`, `section`.
- [x] Un solo `h1` por página.
- [x] `meta viewport` y `meta charset` presentes.
- [x] Repo en GitHub inicializado, rama `main`, commits descriptivos.
- [x] Algo de interactividad: `:hover` en proyectos del portfolio y links de nav.

#### ❌ HTML / Páginas (pendiente)

- [ ] Crear las 4 páginas secundarias (en carpeta `pages/` o similar; solo index en la raíz). Ideas: Sobre mí, Portfolio, Servicios/Skills, Contacto.
- [ ] Nav con links reales a las 5 páginas (hoy los `<a>` apuntan a `#`) y accesible desde todas las páginas.
- [ ] Contenido distintivo en cada página (los proyectos del portfolio son placeholders "Proyecto 1..4").
- [ ] Reemplazar el Lorem ipsum por contenido real.
- [x] Agregar `<footer>` (etiqueta semántica) — ya presente en `index.html`.
- [ ] Corregir `lang="en"` → el contenido está en español (`lang="es"`).
- [ ] Tipos de input correctos en el form (el email usa `type="text"`), `name` en los inputs, `required` donde corresponda.

#### ❌ SEO y accesibilidad (pendiente)

- [ ] `meta name="description"` en cada página.
- [ ] `title` único y descriptivo por página.
- [ ] Atributos `alt` en TODAS las imágenes (hoy ninguna `<img>` tiene alt).
- [ ] `loading="lazy"` en imágenes debajo del fold.
- [ ] Favicon.
- [ ] (Opcional/plus) Open Graph, atributos ARIA donde sumen.

#### ✅ SASS (requisito central — los 5 pilares CUMPLIDOS)

- [x] Compilador SASS configurado (Dart Sass vía npm, script `dev` con `sass ./scss/main.scss:./css/styles.css --watch`).
- [x] Estructura de carpetas `scss/` con partials (`base/` y `components/`), compilando a `css/styles.css`.
- [x] Migrar a SCSS: header, profile, portfolio, form, footer y reset (base) ya migrados.
- [x] Aplicar **variables** (`_variables.scss` con `$color-primario`, `$color-superficie`, `$color-oscuro`; colores con transparencia vía funciones de color).
- [x] Aplicar **nesting** (bloques BEM con `&`, container queries anidadas que "burbujean").
- [x] Aplicar **partials** (`_variables`, `_mixin`, `_extend`, `_reset`, `_header`, `_profile`, `_portfolio`, `_form`, `_footer`; `_responsive` recién creado, ver abajo).
- [x] **mixins**: `flex-center` creado y usado en `.form`.
- [x] **extend**: `%barra-base` en `_extend.scss`, aplicado en `.load-bar__bar` (verificado en `styles.css`: estilos en la barra, `.profile` limpio).
- [x] **Switch del `<link>`** a `styles.css` HECHO (index.html ya apunta a `./css/styles.css`).

**Pendientes menores de SASS (pulido, no bloquean la entrega):**
- [ ] Mixin `responsive($medida)` con `@content` para reemplazar las `@container ... (min-width)` repetidas (se creó `scss/base/_responsive.scss`, falta escribir/aplicar el mixin).
- [ ] Verificar visualmente la página completa con `styles.css` y **borrar `oldstyles.css`** (ya cumplió su rol de red de seguridad).

*Notas de la sesión 2026-06-16:* se aprendió y aplicó nesting, `&`, `@use` (scoping por archivo + `as *`), burbujeo de at-rules, comentarios `//` vs `/* */`, mixins (`@include`), extend con `%placeholder`, y rutas relativas de `@use` (mismo nivel = solo nombre; `../` para subir). Bugs recurrentes detectados y resueltos: estilos de escritorio en la capa base (patrón mobile-first), rutas de `@use` con carpeta duplicada, y `@extend` suelto que aplicaba estilos al selector padre equivocado.

#### ❌ Bootstrap y librerías (pendiente)

- [ ] Linkear Bootstrap (CSS y JS bundle) en todas las páginas.
- [ ] Usar al menos algunos componentes Bootstrap adaptados a la identidad propia (sin estilos genéricos del framework).
- [ ] Librería de animaciones (ej: AOS, Animate.css) linkeada y aplicada.

#### ❌ Estilos avanzados (pendiente)

- [ ] Transiciones (los `:hover` actuales cambian en seco — falta `transition`).
- [ ] Transformaciones (`transform: scale/translate/rotate...`).
- [ ] Al menos una animación con `@keyframes` (candidato: animar las barras de skills al cargar).

#### ❌ Optimización y deploy (pendiente)

- [ ] Optimizar imágenes (la foto de perfil `IMG-20211212-WA0074.jpg` está sin comprimir y con nombre poco descriptivo).
- [ ] Deploy en Vercel o Netlify.
- [ ] Verificar rutas relativas de imágenes y links en todas las páginas una vez deployado.

### Convenciones del proyecto

- Nomenclatura de clases: BEM (`bloque__elemento--modificador`).
- Imágenes en `assets/`.
