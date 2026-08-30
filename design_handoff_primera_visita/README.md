# Handoff: rediseño de la primera visita — VALDIESEL SAS

## Resumen

Rediseño de la página de inicio de `valdieselbogota/valdiesel-frontend` para el visitante que llega por primera vez: hero con propuesta clara, franja de confianza, entrada por categorías, rejilla de repuestos, bloque de asesoría y cierre con las marcas que surte la empresa. Los precios siguen reservados para clientes autenticados; el visitante sin cuenta puede armar un pedido y cerrarlo por WhatsApp.

La pantalla aprobada es **3a** (turno 3) del archivo `valdiesel-primera-visita.dc.html`, en versión escritorio y móvil.

## Sobre los archivos de este paquete

Los archivos HTML de este paquete son **referencias de diseño**: prototipos que muestran la apariencia y el comportamiento buscados, no código de producción para copiar y pegar tal cual. Usan datos de ejemplo.

El trabajo consiste en **recrear este diseño dentro de `index.html` del repositorio**, con sus propios patrones: vistas que devuelven plantillas de cadena (`viewHome()`, `productCard()`, `renderNav()`), estado en variables de módulo y datos que vienen del backend. No hay que tocar el backend ni cambiar el modelo de datos.

## Fidelidad

**Alta fidelidad.** Colores, tipografía, espaciado, estados y animaciones son definitivos y están especificados abajo con valores exactos. La estructura y el orden de bloques ya fueron aprobados en el boceto 2a del mismo archivo.

Dos huecos conocidos, a la espera de material del cliente:

- No hay logo de SONYCO. Está retirado del cierre de marcas; al llegar el logo se suma al carrusel.
- Las cinco categorías usan un ícono de Lucide como marcador. Si se consiguen fotos de categoría, sustituyen al ícono conservando la caja de la tarjeta.

## Fichero de origen

| Archivo | Qué contiene |
| --- | --- |
| `valdiesel-primera-visita.dc.html` | Turno 3 (**3a**, la pantalla a implementar), turno 2 (boceto en gris) y turno 1 (tres direcciones exploradas). Cada tablero lleva un `data-screen-label`. |
| `valdiesel-estado-actual.dc.html` | Recreación del inicio, portal y carrito actuales, para comparar antes/después. |
| `assets/` | Logo de la empresa, fotos de producto y logos de marca, extraídos de los base64 de `index.html`. |
| `classical.css` | Hoja del sistema de diseño Classical, de donde salen las variables `--color-*`, `--space-*`, `--radius-*`, `--shadow-*` y las clases `.btn`, `.card`, `.nav`, `.plate`, `.table`, `.input`, `.field`, `.tag`, `.hr`. |

Para abrir los prototipos hace falta `support.js` y `classical.css` junto a los `.dc.html`, y la carpeta `assets/` al lado. Todo va incluido.

## Pantalla: Inicio (3a)

Ancho del tablero de escritorio: 900 px. Móvil: 360 px. El diseño es fluido; no hay anchos fijos internos.

Orden de bloques, de arriba abajo:

### 1. Barra de navegación

Clase `.nav` del sistema, `gap: var(--space-4)`.

- Logo `assets/logo-valdiesel.jpeg`, **58×58 px** en escritorio (46×46 en móvil), `object-fit: cover`, `border-radius: var(--radius-sm)`.
- Marca de palabra: `VALDIESEL` en `#E8443C`, `SAS` en `#D6392F`, clase `.nav-brand` (Cormorant Garamond). Móvil: 17 px.
- Enlaces: Nosotros · Productos · Contacto · Portal clientes.
- Buscador a la derecha: caja de `1px solid var(--color-divider)`, `border-radius: var(--radius-md)`, padding `5px var(--space-2)`, ancho mínimo 210 px, ícono `search` de Lucide a 15 px con `opacity: .45`, `input.input` sin borde a 13 px, texto guía «Referencia o pieza».
- «Pedido (0)» al extremo, tabular.

En móvil la barra se reduce a logo, marca y «Pedido»; el buscador baja al cuerpo con alto mínimo de 44 px.

### 2. Hero

Rejilla `1.05fr 1fr`, `gap: var(--space-8)`, padding `var(--space-8)`, `align-items: center`.
Borde superior: **`3px solid #E8443C`**, animado (ver Animaciones).

Columna de texto:

- Kicker: «Bogotá · desde 2003», 11 px, `letter-spacing: .1em`, mayúsculas, color `#D6392F`, cifras tabulares.
- Título: «Su aliado en repuestos diesel», 50 px, `font-weight: 400`, fuente de titulares.
- Párrafo justificado, medida máxima 44 caracteres: «Amplio portafolio para transporte ligero, con asesoría de quien conoce la pieza. Consulte por referencia o cuéntenos qué necesita: confirmamos existencia y precio el mismo día.»
- Botones: `.btn.btn-primary` «Ver catálogo» y `.btn.btn-secondary` «Hablar con un asesor», padding `11px 20px`. El primario va en rojo: `color: #D6392F; border-color: #E8443C`.

Columna de imagen: `assets/home-1.jpg` con clase `.plate`, alto 290 px (140 en móvil), `object-fit: cover`, `object-position: center 65%`.

En móvil el orden es: buscador, foto, kicker, título 32 px, párrafo 14 px, los dos botones a `min-height: 48px`.

### 3. Franja de confianza

Rejilla de tres columnas, `1px solid var(--color-divider)` arriba y abajo, `1px solid var(--color-divider)` entre columnas. Cada celda: padding `var(--space-4) var(--space-6)`, ícono de 22 px con `opacity: .65` y tinte rojo por filtro (ver Tokens), título en fuente de titulares a 19 px, cuerpo a 13 px en `.text-muted`.

| Título | Cuerpo | Ícono Lucide |
| --- | --- | --- |
| Amplio portafolio | 663 referencias en 16 marcas | `boxes` |
| Envíos a nivel nacional | Despachos seguros a todo el país | `truck` |
| Repuestos garantizados | Respaldo en cada pieza que vendemos | `shield-check` |

En móvil se vuelve una lista vertical: ícono de 20 px y solo el título, a 14 px.

### 4. Categorías

Título de sección `h6` «Categorías» en `#D6392F` con filete inferior `2px solid #E8443C`, `padding-bottom: 4px`, `align-self: flex-start`.

Rejilla de cinco columnas (dos en móvil), `gap: var(--space-3)`. Cada tarjeta: clase `.card`, `align-items: center`, padding `var(--space-3)`, cursor `pointer`, ícono de 26 px con `opacity: .6` **sin tinte rojo**, nombre en fuente de titulares a 18 px, conteo en `.card-meta` tabular.

| Categoría | Referencias | Ícono Lucide |
| --- | --- | --- |
| Motor | 214 | `cog` |
| Embrague | 78 | `disc` |
| Frenos | 126 | `circle-stop` |
| Filtros | 145 | `filter` |
| Transmisión | 100 | `git-fork` |

Los conteos son de ejemplo: deben salir del catálogo real.

### 5. Nuestros repuestos

Encabezado con el `h6` rojo y filete a la izquierda, y a la derecha el enlace «Ver todo el catálogo» a 13 px en `#D6392F`.

Rejilla de cuatro columnas, ocho piezas (dos columnas y cuatro piezas en móvil), `gap: var(--space-3)`. Cada tarjeta `.card` contiene:

- Foto con `.plate`, alto 92 px (72 en móvil), `object-fit: cover`.
- `.card-kicker` con la marca, tabular, color `#D6392F`.
- `.card-title` a 15 px con el nombre de la pieza.
- `.card-meta` tabular: «Ref. {código}».
- Texto `.text-muted` a 12 px: «Precio para clientes».
- `.btn.btn-primary.btn-block` «Agregar», en rojo.

Las cuatro piezas de ejemplo (con foto en `assets/`) son `8-97385988-0`, `C-11`, `8973152312` y `8973814550`; en producción salen del catálogo, priorizando las que tengan foto.

### 6. Bloque de asesoría

`1px solid var(--color-divider)` arriba y abajo, padding `var(--space-6) var(--space-8)`, fila con `gap: var(--space-6)`.

- Título `h3` a peso 400: «¿Necesita ayuda para encontrar el repuesto adecuado?»
- Cuerpo en `.text-muted`, medida máxima 56 caracteres: «Díganos el modelo del camión y la falla. Un asesor identifica la pieza y le confirma precio y despacho por WhatsApp.»
- `.btn.btn-primary` «Escribir por WhatsApp», padding `11px 20px`, `white-space: nowrap`. **Este botón va en el dorado del sistema, no en rojo.**

En móvil es una `.card` con el título a 20 px y el botón a `min-height: 48px`.

### 7. Marcas que surtimos

`h6` centrado «Marcas que surtimos» en `var(--color-accent-700)` — **dorado, no rojo, y sin filete**.

Carrusel infinito de derecha a izquierda:

- Contenedor con `overflow: hidden` y máscara de desvanecido en los bordes: `mask-image: linear-gradient(to right, transparent 0, black 8%, black 92%, transparent 100%)` (más el prefijo `-webkit-`).
- Pista interna `display: flex; width: max-content`, animación `vdMarquee` **26 s** lineal infinita en escritorio, **20 s** en móvil.
- Logos a 34 px de alto (26 en móvil), `margin-right: var(--space-8)` (`var(--space-6)` en móvil).
- La lista se repite: seis logos por pasada y la pasada duplicada, de modo que `translateX(-50%)` cierra el bucle sin salto. Con tres marcas son doce imágenes en total. **Si se agregan marcas hay que mantener la regla: la pista debe contener exactamente dos copias idénticas de la secuencia.**

Marcas actuales: `assets/home-4.png` (ISUZU), `assets/home-6.jpg` (RIKKON), `assets/home-5.png` (TONYCO).

### 8. Pie

`1px solid var(--color-divider)` arriba, padding `var(--space-6) var(--space-8)`, rejilla `1.3fr 1fr 1fr`.

- Columna 1: logo a 44×44 px, marca de palabra a 16 px en rojo, y «Repuestos diesel para transporte ligero. / Bogotá, Colombia.» a 13 px en `.text-muted`.
- Columna 2, «Contacto» en `h6` rojo: «Cra 55 No. 14-17, Bogotá» y el enlace `https://wa.me/573108088686` como «+57 310 808 8686».
- Columna 3, «Enlaces» en `h6` rojo: «Catálogo» y «Portal clientes».

## Interacciones y comportamiento

- «Ver catálogo» y «Ver todo el catálogo» llevan al catálogo. Las tarjetas de categoría llevan al catálogo filtrado por esa categoría.
- «Hablar con un asesor» y «Escribir por WhatsApp» abren WhatsApp con el número `573108088686`, igual que la función `contactarAsesor()` que ya existe en `index.html`.
- «Agregar» suma la pieza al pedido sin exigir cuenta y actualiza el contador de la barra. El precio no se muestra en ningún caso a un visitante sin sesión: donde iría el precio se lee «Precio para clientes».
- El buscador de la barra consulta por referencia o por nombre, como el buscador actual.
- El carrusel de marcas no se detiene al pasar el cursor.

## Animaciones

Todas con `cubic-bezier(0.22, 0.61, 0.36, 1)` salvo el carrusel, que es lineal. Todo dentro de un `@media (prefers-reduced-motion: reduce)` que anula duraciones e iteraciones.

| Nombre | Fotogramas | Dónde | Duración y retardo |
| --- | --- | --- | --- |
| `vdRule` | `scaleX(0)` → `scaleX(1)`, `transform-origin: left` | Borde rojo superior del hero | 0.8 s, sin retardo |
| `vdUp` | `opacity 0` + `translateY(14px)` → normal | Columna de texto del hero (0.1 s), celdas de confianza (0.3 s), tarjetas de categoría (0.4 s), bloque de marcas (0.15 s) | 0.7 s |
| `vdPlate` | `opacity 0` + `scale(1.03)` → normal | Foto del hero | 1 s, retardo 0.15 s |
| `vdMarquee` | `translateX(0)` → `translateX(-50%)` | Pista de marcas | 26 s escritorio / 20 s móvil, lineal, infinita |

Estados al puntero, con `transition` de 0.3 s:

- Tarjetas de categoría y de repuesto: `transform: translateY(-4px)`, `border-color: #E8443C`, `box-shadow: var(--shadow-md)`.
- Botones: `translateY(-1px)` al pasar, `translateY(1px)` al presionar.
- El foco de teclado usa el anillo del sistema: `outline: 2px solid var(--color-accent); outline-offset: 2px`.

## Estado

El diseño no introduce estado nuevo. Reutiliza el que ya existe en `index.html`:

- La vista actual (`home`, `catalogo`, `login`, `carrito`).
- El carrito público del visitante sin sesión y su contador en la barra.
- La sesión del cliente, que es la única que revela precios.
- Los datos del catálogo que ya llegan del backend, con su respaldo `PRODUCTS_FALLBACK`.

Datos que hay que resolver al implementar: el conteo de referencias por categoría, la selección de las ocho piezas destacadas y el mapa de categoría por producto, que hoy no existe en el modelo. Si el backend no lo tiene, se puede derivar del nombre de la pieza o dejar el conteo fuera.

## Tokens de diseño

Todo lo que no sea la marca sale de las variables de `classical.css`. No introducir hex nuevos.

Rojo de la marca, las dos únicas excepciones, declaradas una vez en `:root`:

```css
--brand-red: #E8443C;      /* filetes, bordes al pasar el cursor, marca de palabra */
--brand-red-700: #D6392F;  /* texto: kickers, títulos de sección, «SAS», enlaces */
```

Dónde va el rojo: marca de palabra en barra y pie, borde superior del hero, títulos de sección con su filete, marca en las tarjetas de repuesto, botones primarios, enlace «Ver todo el catálogo», íconos de la franja de confianza, bordes de tarjeta al pasar el cursor.

Dónde **no** va: íconos de categoría (grises, `opacity: .6`), botón «Escribir por WhatsApp» y título «Marcas que surtimos» — esos dos se quedan en el dorado del sistema.

Tinte rojo de los íconos SVG de la franja de confianza:

```css
filter: invert(31%) sepia(64%) saturate(2200%) hue-rotate(338deg) brightness(93%) contrast(92%);
```

Del sistema Classical, tal como los usa el diseño:

- Fondo `--color-bg` #f3f2f2, texto `--color-text` #201f1d, acento dorado #b68235 con su rampa 100–900.
- Titulares en Cormorant Garamond (`--font-heading`), cuerpo en Lora (`--font-body`), los dos desde Google Fonts. Peso 400 en titulares; el sistema evita la negrita.
- Espaciado por `--space-1` … `--space-8`; radios por `--radius-sm` / `--radius-md`; elevación por `--shadow-sm` / `--shadow-md`.
- Cifras tabulares (`font-variant-numeric: tabular-nums`) en referencias, conteos, precios y kickers; la prosa conserva sus cifras normales.
- Fotos siempre dentro de `.plate`.

## Recursos

| Archivo | Qué es | Origen |
| --- | --- | --- |
| `assets/logo-valdiesel.jpeg` | Logo VD de la empresa | Entregado por el cliente en la conversación |
| `assets/home-1.jpg` | Foto del hero, transporte ligero | Base64 en `viewHome()` de `index.html` |
| `assets/home-3.jpg` | Foto secundaria, usada en el turno 1 | Base64 en `viewHome()` |
| `assets/home-4.png` | Logo ISUZU | Base64 en `viewHome()` |
| `assets/home-5.png` | Logo TONYCO | Base64 en `viewHome()` |
| `assets/home-6.jpg` | Logo RIKKON | Base64 en `viewHome()` |
| `assets/prod-*.jpg` | Cuatro fotos de producto | Base64 en `PRODUCT_IMAGES` de `index.html` |
| Íconos | Lucide, servidos desde `unpkg.com/lucide-static@0.544.0` | lucide.dev |

Los base64 de `index.html` pesan casi 400 KB del archivo. Al implementar conviene servir estas imágenes como archivos y borrar los base64.

## Referencia visual

El cliente pidió inspirarse en la estructura de `astrorepuestos.com`: de ahí viene el recorrido de la página (confianza, categorías, rejilla, asesoría, marcas al cierre). El vestido tipográfico y de color es el del sistema Classical más el rojo de VALDIESEL, no el de esa referencia.
