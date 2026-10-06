# Brief — Landing de Código Nativo (codigonativo.com.ar)

Este archivo tiene dos partes:

- **Parte 1 — Para Rodrigo:** cómo armar el proyecto desde cero en VS Code y cómo pasárselo a Claude.
- **Parte 2 — Para Claude:** qué construir, con qué diseño y con qué textos (español e inglés).

---

# PARTE 1 — PARA RODRIGO

## Paso 1. Instalar lo necesario

1. **VS Code:** si no lo tenés, bajalo de code.visualstudio.com e instalalo.
2. **Extensión de Claude:** en VS Code, abrí el panel de extensiones (el ícono de los cuatro cuadraditos en la barra izquierda), buscá **"Claude Code"** e instalala. Te va a pedir que inicies sesión con tu cuenta de Claude.
   - Si preferís no instalar nada, también podés pegar este archivo en una conversación de claude.ai y pedirle el `index.html`.
3. **Live Server (opcional pero muy útil):** en el mismo panel de extensiones buscá **"Live Server"** e instalala. Sirve para ver la página en el navegador y que se actualice sola cada vez que guardás un cambio.

## Paso 2. Crear la carpeta del proyecto

Creá esta estructura en tu computadora (por ejemplo en Documentos):

```
codigo-nativo-web/
├── brief-web-codigo-nativo.md   ← este archivo
└── assets/
    ├── og-image.png             ← el símbolo blanco sobre fondo negro (la imagen cuadrada)
    └── rodrigo-lauro.jpg        ← tu foto
```

El logo para la web (`logo-simbolo.svg`) **no lo ponés vos**: lo crea Claude con código. Ver más abajo.

**Por qué una carpeta `assets`:** es la convención para guardar imágenes y archivos que la página usa. Así el código queda separado de las imágenes y es más fácil de mantener.

**Nombres de archivo:** en minúsculas, sin espacios, sin tildes y sin ñ. Los servidores web distinguen mayúsculas de minúsculas y los espacios rompen los enlaces. Por eso `rodrigo-lauro.jpg` y no `Rodrigo Lauro.JPG`.

### Tu foto: cómo tiene que ser

- Cuadrada o casi cuadrada, mínimo 800 × 800 píxeles.
- Formato JPG, idealmente de menos de 300 KB (si pesa más, comprimila en squoosh.app).
- Cara bien visible, fondo neutro, buena luz. Que se vea profesional pero cercana: es la foto de "la persona que responde".

### El logo

- **El símbolo** (el óvalo con la línea vertical) lo crea Claude como archivo SVG. Un SVG no es una foto: es código que describe formas, y tu símbolo son solo dos formas (un óvalo y una línea). Así se ve nítido en cualquier tamaño y ya sale en blanco para el fondo oscuro.
- **`og-image.png`** es la imagen que aparece cuando alguien comparte el link de la web en LinkedIn o WhatsApp. LinkedIn no acepta SVG para esto, por eso va tu PNG del símbolo blanco sobre negro.
- El texto "CÓDIGO NATIVO" de tu logo original usa una tipografía específica que no tenemos. En la web, el nombre va escrito con la tipografía de la página (Inter) al lado del símbolo.

## Paso 3. Crear la cuenta de Formspree (para el formulario de contacto)

1. Entrá a **formspree.io** y creá una cuenta gratis con `rodrigo.lauro@codigonativo.com.ar`.
2. Creá un formulario nuevo ("New form"). Ponele de nombre "Web Código Nativo".
3. Formspree te da una dirección parecida a `https://formspree.io/f/abcd1234`. **Copiala**: se la vas a dar a Claude.
4. El plan gratis alcanza para empezar: permite un número limitado de envíos por mes, más que suficiente para una landing B2B.

**Por qué Formspree:** una página HTML sola no puede mandar mails. Formspree recibe lo que la persona completa en el formulario y te lo reenvía a tu correo. No necesitás servidor ni programar nada del lado del servidor.

## Paso 4. Pedirle a Claude que construya la web

1. En VS Code: **Archivo → Abrir carpeta** y elegí `codigo-nativo-web`.
2. Abrí el panel de Claude Code.
3. Escribile algo así:

> Leé el archivo `brief-web-codigo-nativo.md` y construí la web siguiendo la Parte 2. Mi dirección de Formspree es `https://formspree.io/f/XXXX`. Antes de escribir código, contame en pocas líneas cómo la vas a armar y esperá mi OK.

4. Claude te va a pedir permiso para crear el archivo `index.html`. Leé qué va a hacer y aprobá.

## Paso 5. Ver la página

- Con **Live Server:** clic derecho sobre `index.html` → **"Open with Live Server"**. Se abre en el navegador.
- Sin Live Server: doble clic sobre `index.html` en el explorador de archivos.

Probá también cómo se ve en el celular: en Chrome, apretá F12 y después el ícono del teléfono arriba a la izquierda del panel que se abre.

## Paso 6. Pedir cambios

Pedile cambios a Claude de a uno y bien concretos. Por ejemplo:

- "El título del hero es muy grande en celular, achicalo."
- "Hacé el brillo del hero un poco más intenso."
- "Explicame qué hace esta parte del CSS."

## Paso 7. Publicar (con tu socio, que tiene acceso al dominio)

Hay dos caminos. Elegí uno con tu socio:

**A. Subirla al hosting que ya tienen.** Tu socio entra al panel del hosting (cPanel, el administrador de archivos o por FTP) y sube `index.html` y la carpeta `assets` a la carpeta pública del dominio (suele llamarse `public_html`). Reemplaza la página de "Próximamente".

**B. Netlify gratis.** Entrás a netlify.com, creás una cuenta y arrastrás la carpeta `codigo-nativo-web` a la página. En segundos te da una dirección de prueba. Después tu socio apunta el dominio a Netlify desde la configuración DNS (Netlify explica los pasos en "Domain settings").

Cuando esté publicada: **volvé a poner `codigonativo.com.ar` en la página de LinkedIn** (Editar página → Detalles → Sitio web).

## Pendientes que tenés que confirmar antes de publicar

Estos datos están en los textos y todavía no los confirmaste. Si alguno no es cierto, decile a Claude que lo saque:

1. **Unilever:** si la migración de Azure a GCP fue parte de los 4 años. El texto actual dice "incluida la migración", que asume que sí.
2. **Horario solapado con España:** que el equipo en Argentina pueda trabajar con varias horas en común con la jornada española.
3. **Teléfono:** no puse ninguno. Si tenés número español, se puede agregar en el contacto.
4. **Link a la página de LinkedIn de la empresa:** pasale a Claude la dirección pública (la que ves en "Ver como miembro").

---

# PARTE 2 — PARA CLAUDE

## Contexto

Código Nativo es una empresa argentina de 4 personas que ofrece **equipos de Data e IA a consultoras españolas** de desarrollo y datos (20 a 200 personas) que ganaron contratos y no tienen gente. El lector de la web es un Business Manager, Delivery Manager o responsable de práctica de una consultora. Su miedo no es técnico: es quedar mal frente a su propio cliente. La web tiene que transmitir seriedad, bajo riesgo y un equipo real.

## Cómo trabajar con Rodrigo (obligatorio)

- Rodrigo quiere **entender** lo que hacés, no solo recibir el resultado. Explicá cada paso en español rioplatense, de forma simple.
- El código tiene que ser **simple y fácil de entender por alguien que recién empieza a programar**. Nada de frameworks, librerías de JavaScript, herramientas de compilación ni npm.
- **Comentarios en español** dentro del código, explicando qué hace cada sección del HTML, cada bloque importante del CSS y cada función del JavaScript.
- Antes de ejecutar cualquier comando o crear archivos, decile qué vas a hacer y para qué, y recordale que también lo puede hacer a mano.
- Antes de escribir código, proponé en pocas líneas cómo vas a armar la página y esperá su OK.

## Requisitos técnicos

- **Un solo archivo `index.html`** con el CSS dentro de una etiqueta `<style>` y el JavaScript dentro de una etiqueta `<script>`. Las imágenes van en `assets/`.
- Única dependencia externa permitida: la tipografía **Inter** desde Google Fonts.
- **Responsive:** tiene que verse bien desde 360 px de ancho (celular) hasta pantallas grandes. Sin scroll horizontal.
- **Accesible:** contraste suficiente, `alt` en las imágenes, `label` en los campos del formulario, navegable con teclado, `lang` correcto en el `<html>`.
- Respetar `prefers-reduced-motion`: si el usuario pidió menos animación en su sistema, desactivar transiciones y animaciones.
- **SEO y vista previa al compartir:** `<title>`, `<meta name="description">` y etiquetas Open Graph (`og:title`, `og:description`, `og:image` apuntando a `assets/og-image.png`, `og:url`). Importante: la web se va a compartir en LinkedIn y tiene que mostrar una vista previa correcta.
- **Favicon:** usar `assets/logo-simbolo.svg` con `<link rel="icon" type="image/svg+xml">`.

## Diseño — Dirección "oscuro con brillos", monocromo

Referencia de estilo: **linear.app** (inspiración, no copia). Fondo casi negro, tipografía blanca grande con ligero degradado, brillos de luz suaves detrás de las secciones clave, tarjetas con bordes finos y semitransparentes.

**Paleta monocroma:** solo negro, blanco y grises. Los brillos son **blancos**, como en el banner de la marca (puntos y líneas de luz blanca sobre negro). La identidad de Código Nativo es blanco y negro, y la empresa tiene otra web para su producto de flota que usa violeta: esta web **no usa ningún color**, para respetar la marca y para que no se confundan.

### Variables de color (definilas en `:root`)

```css
--bg: #07080A;              /* fondo principal, casi negro */
--bg-elevated: #0E1014;     /* fondo de tarjetas */
--border: rgba(255, 255, 255, 0.08);        /* bordes finos */
--border-hover: rgba(255, 255, 255, 0.20);  /* bordes al pasar el mouse */
--text: #ECEDEE;            /* texto principal */
--text-muted: #9BA1A6;      /* texto secundario */
--accent: #FFFFFF;          /* acento: blanco puro */
--accent-soft: rgba(255, 255, 255, 0.10);   /* brillo blanco suave */
```

Todo el color de la página tiene que salir de estas variables, para que Rodrigo pueda cambiar el acento editando una sola línea.

Como no hay color, el contraste se logra con **intensidad**: blanco puro para lo importante (títulos, botón principal, números), gris para lo secundario. El botón principal es blanco con texto negro; el secundario, transparente con borde fino.

### Tipografía

- Inter, pesos 400, 500, 600 y 700.
- Título principal (h1): `font-size: clamp(2.5rem, 6vw, 4.5rem)`, `letter-spacing: -0.03em`, peso 700, con degradado de blanco a gris claro aplicado al texto.
- Títulos de sección (h2): `clamp(1.75rem, 4vw, 2.75rem)`, `letter-spacing: -0.02em`.
- Texto normal: 1rem a 1.125rem, `line-height: 1.6`, color `--text-muted`.
- Etiqueta pequeña sobre los títulos ("eyebrow"): mayúsculas, 0.8rem, `letter-spacing: 0.08em`, color `--accent`.

### Espaciado y layout

- Ancho máximo del contenido: 1120 px, centrado.
- Margen lateral: 24 px en escritorio, 16 px en celular.
- Separación entre secciones: unos 120 px en escritorio y 72 px en celular.
- Tarjetas: `border-radius: 16px`, borde de 1 px con `--border`, fondo `--bg-elevated` con un degradado muy sutil. Al pasar el mouse, el borde pasa a `--border-hover`.

### Efectos

- **Brillo del hero:** un degradado radial blanco muy suave (`--accent-soft`) arriba del título, que se desvanece hacia los costados.
- **Puntos de luz:** opcionalmente, algunos puntos blancos pequeños y tenues dispersos en el fondo del hero, evocando el banner de la marca. Con CSS simple, sin canvas ni librerías.
- **Grilla sutil:** detrás del hero, líneas finas de grilla casi invisibles que se desvanecen hacia los bordes (con `mask-image`).
- **Animación al hacer scroll:** las secciones aparecen con un fundido suave y un pequeño desplazamiento hacia arriba. Usar `IntersectionObserver` con código simple y comentado. Sin librerías.
- **Nada exagerado:** el brillo es un acompañamiento, no el protagonista. El contenido tiene que leerse perfecto.

### Header

- Fijo arriba (`position: sticky`), con fondo semitransparente y desenfoque (`backdrop-filter: blur`).
- A la izquierda: logo + "Código Nativo".
- Al centro (solo escritorio): enlaces a Cómo trabajamos, Perfiles, Casos y Contacto.
- A la derecha: botón **ES / EN** y botón principal "Contacto".
- En celular: se ocultan los enlaces del centro; quedan logo, ES/EN y el botón de contacto.

### Logo — crear `assets/logo-simbolo.svg`

El símbolo de la marca es un **óvalo vertical con una línea vertical que lo divide por la mitad**, de arriba abajo. Trazo blanco, sin relleno, con grosor de trazo de aproximadamente el 7% del ancho. Proporción aproximada: alto = 1,24 × ancho.

Crear el archivo `assets/logo-simbolo.svg` con algo equivalente a esto:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 124">
  <ellipse cx="50" cy="62" rx="46" ry="58" fill="none" stroke="#FFFFFF" stroke-width="7"/>
  <line x1="50" y1="4" x2="50" y2="120" stroke="#FFFFFF" stroke-width="7"/>
</svg>
```

- Explicale a Rodrigo línea por línea qué significa (`viewBox`, `ellipse`, `cx/cy`, `rx/ry`, `stroke`, `line`).
- Mostrale el resultado y preguntale si coincide con su logo; ajustar proporciones si hace falta.
- Usarlo en el header (unos 28-32 px de alto) y en el footer (más grande), siempre seguido del texto "Código Nativo" en Inter, peso 500.
- Usarlo también como favicon.

## Cambio de idioma español / inglés

Implementarlo de la forma **más simple de entender**:

- Cada texto existe dos veces: una con la clase `lang-es` y otra con la clase `lang-en`.
- El `<body>` tiene la clase `show-es` o `show-en`.
- Con CSS se oculta el idioma que no corresponde: `.show-es .lang-en { display: none; }` y `.show-en .lang-es { display: none; }`.
- El botón ES/EN cambia la clase del `<body>` y actualiza el atributo `lang` del `<html>`.
- Idioma por defecto: español.
- Opcional: recordar la elección con `localStorage`, siempre dentro de `try/catch` para que la página funcione aunque el navegador lo bloquee.

## Estructura de la página

Estructura inspirada en cómo **toptal.com** presenta su servicio: problema → por qué nosotros → qué ofrecemos → cómo empezamos → pruebas → contacto.

1. Header
2. Hero
3. Franja de clientes
4. Por qué nosotros
5. Formatos
6. Perfiles
7. Cómo empezamos
8. Casos
9. Quién responde (foto de Rodrigo)
10. Contacto (formulario)
11. Footer

## Textos

Español de España con tuteo (no voseo). No cambiar el sentido de los textos. Se pueden hacer ajustes menores de longitud si el diseño lo pide, avisando a Rodrigo.

### 1. Header

| | ES | EN |
|---|---|---|
| Enlaces | Cómo trabajamos · Perfiles · Casos · Contacto | How we work · Profiles · Case studies · Contact |
| Botón | Contacto | Contact |

### 2. Hero

**ES**
- Eyebrow: Equipos de Data e IA para consultoras
- Título: ¿Ganaste el contrato y te falta gente de datos?
- Subtítulo: Te damos un equipo de Data e IA que lleva años trabajando junto, con un responsable técnico como único interlocutor. Dentro de tus procesos y bajo tu marca.
- Botón principal: Cuéntanos qué perfiles necesitas → enlaza a `#contacto`
- Botón secundario: Ver casos → enlaza a `#casos`

**EN**
- Eyebrow: Data & AI teams for consultancies
- Título: Won the contract but short on data people?
- Subtítulo: We give you a Data & AI team that has worked together for years, with one technical lead as your single point of contact. Inside your processes and under your brand.
- Botón principal: Tell us which profiles you need
- Botón secundario: See case studies

### 3. Franja de clientes

Solo texto, **sin logos** (los logos de otras marcas no se usan sin permiso). Nombres en gris, separados por puntos medios.

- ES: Han trabajado con nosotros — Unilever · Whirlpool · Ayesa · Puma · Grupo Dota
- EN: Companies we have worked with — Unilever · Whirlpool · Ayesa · Puma · Grupo Dota

### 4. Por qué nosotros

**ES**
- Eyebrow: Por qué nosotros
- Título: Contratar lleva meses. Tu cliente no espera.
- Intro: Una bolsa de freelancers te deja a ti gestionando personas sueltas frente a tu cliente. Nosotros te damos un equipo.

Cuatro tarjetas:

1. **Un equipo, no personas sueltas.** Llevamos años trabajando juntos en los mismos proyectos. No pierdes semanas en que se conozcan.
2. **Un solo interlocutor técnico.** Un responsable técnico con nombre responde por el equipo y por la entrega.
3. **Reemplazos a nuestro cargo.** Si alguien sale, lo reemplazamos nosotros, sin coste para ti.
4. **Bajo tu marca.** Tu Jira, tu repositorio, tus code reviews, tu definición de terminado. Para tu cliente, somos parte de tu equipo.

**EN**
- Eyebrow: Why us
- Título: Hiring takes months. Your client won't wait.
- Intro: A pool of freelancers leaves you managing loose individuals in front of your client. We give you a team.

1. **A team, not individuals.** We have worked together on the same projects for years. No weeks lost getting to know each other.
2. **One technical point of contact.** A named technical lead is accountable for the team and the delivery.
3. **Replacements on us.** If someone leaves, we replace them at no cost to you.
4. **Under your brand.** Your Jira, your repo, your code reviews, your definition of done. To your client, we are part of your team.

### 5. Formatos

Dos tarjetas lado a lado. La primera, destacada (borde más claro y etiqueta "Principal" / "Main").

**ES**
- Eyebrow: Cómo trabajamos
- Título: Dos formas de trabajar con nosotros

1. **Equipo dedicado** — etiqueta: Principal. De 1 a 4 personas por mes, responsable técnico incluido. Mínimo 3 meses.
2. **Alcance cerrado.** Entregable definido, precio fijo y fecha. Ideal para un primer proyecto.

**EN**
- Eyebrow: How we work
- Título: Two ways to work with us

1. **Dedicated team** — label: Main. 1 to 4 people per month, technical lead included. 3-month minimum.
2. **Fixed scope.** Defined deliverable, fixed price and date. Ideal for a first project.

### 6. Perfiles

Tres tarjetas. Cada una con el nombre del perfil, una frase y el stack en "chips" (pastillas pequeñas con borde).

**ES**
- Eyebrow: Perfiles
- Título: Los perfiles que sumamos a tu proyecto

1. **Data Engineer.** Pipelines de datos fiables, de la ingesta al modelo listo para consumir. Chips: Python · SQL · Airflow · dbt · BigQuery · Cloud SQL
2. **Cloud / Data Architect.** Diseño de plataformas de datos, migraciones y gobierno del dato. Chips: GCP · Migraciones Azure → GCP · Kubernetes · Modelado · Gobierno del dato
3. **AI Engineer.** IA en producción sobre datos gobernados. Chips: RAG · Sistemas multi-agente · Vertex AI · Apps con LLM · Modelos predictivos

**EN**
- Eyebrow: Profiles
- Título: The profiles we add to your project

1. **Data Engineer.** Reliable data pipelines, from ingestion to consumption-ready models.
2. **Cloud / Data Architect.** Data platform design, migrations and data governance. Chips: GCP · Azure → GCP migrations · Kubernetes · Data modeling · Data governance
3. **AI Engineer.** Production AI on top of governed data. Chips: RAG · Multi-agent systems · Vertex AI · LLM apps · Predictive models

### 7. Cómo empezamos

Tres pasos numerados (estilo proceso, con el número grande en blanco, con degradado).

**ES**
- Eyebrow: Cómo empezamos
- Título: Sin riesgo para ti frente a tu cliente

1. **Nos cuentas el proyecto.** Contrato, stack, plazo y perfiles que te faltan.
2. **Tu arquitecto entrevista al equipo.** Antes de arrancar, conoces a quienes van a trabajar contigo.
3. **Arrancamos con una revisión a las dos semanas.** Empezamos por un alcance acotado. Si no encaja, lo dejamos ahí.

**EN**
- Eyebrow: How we start
- Título: No risk for you in front of your client

1. **Tell us about the project.** Contract, stack, timeline and the profiles you are missing.
2. **Your architect interviews the team.** Before we start, you meet the people who will work with you.
3. **We start with a two-week review.** We begin with a limited scope. If it is not a fit, we stop there.

### 8. Casos

`id="casos"`. Cinco tarjetas en grilla (Ayesa y Unilever más grandes, en la primera fila). Cada tarjeta: cliente, título, texto breve y chips de stack.

**ES**
- Eyebrow: Casos
- Título: Lo que hemos hecho

1. **Ayesa — Datos e IA para el sector público.** Plataforma de datos en GCP sobre fuentes muy distintas entre sí (webs, XML, APIs), con gobierno del dato por capas. Sobre ella, agentes de IA que responden preguntas en lenguaje natural, hoy en producción. Chips: BigQuery · Airflow · Dataproc/Spark · GKE · Vertex AI · Gemini
2. **Unilever — 4 años como equipo dedicado.** Un equipo de 5 personas sobre una base de 500 tablas alimentada por distintos proveedores, incluida la migración de su ETL de Azure a GCP. Es el mismo equipo que trabaja hoy en Código Nativo. Chips: Python · SQL · Airflow · BigQuery · Azure → GCP
3. **Banca — Sistema multi-agente en producción.** Para analistas de riesgo y negocio. Cada respuesta cita su fuente o dice que no tiene datos, solo lee datos curados y anonimizados, y todo queda auditado. Chips: Google ADK · Gemini · Vertex AI Agent Engine · BigQuery Vector Search
4. **Whirlpool — Sell out unificado.** Unificamos el sell out de sus clientes, que llegaba en formatos dispares, y lo cruzamos con las ventas de SAP. Pasaron de informes mensuales a ventas actualizadas cada hora. Chips: SAP · ETL · BI
5. **Grupo Dota — Modelos predictivos sobre 1.500 autobuses.** Predicción de consumo, stock y gastos, desgaste de neumáticos por marca y perfiles de riesgo de siniestralidad, sobre los datos operativos de la flota. Chips: Machine Learning · Regresión · Random Forest

**EN**
- Eyebrow: Case studies
- Título: What we have done

1. **Ayesa — Data and AI for the public sector.** A GCP data platform over highly heterogeneous sources (web, XML, APIs), with layered data governance. On top of it, AI agents that answer questions in natural language, now in production.
2. **Unilever — 4 years as a dedicated team.** A 5-person team on a 500-table database fed by multiple vendors, including the migration of their ETL from Azure to GCP. It is the same team working at Código Nativo today.
3. **Banking — Multi-agent system in production.** For risk and business analysts. Every answer cites its source or says there is no data, it only reads curated and anonymized data, and everything is audited.
4. **Whirlpool — Unified sell-out.** We unified their customers' sell-out data, which arrived in disparate formats, and joined it with SAP sales. They went from monthly reports to sales updated every hour.
5. **Grupo Dota — Predictive models on 1,500 buses.** Forecasting of fuel consumption, stock and costs, tire wear by brand and accident-risk profiles, on the fleet's operational data.

### 9. Quién responde

Dos columnas: foto a la izquierda (`assets/rodrigo-lauro.jpg`, recorte circular o con bordes redondeados, con un brillo blanco suave detrás) y texto a la derecha. En celular, foto arriba.

**ES**
- Eyebrow: Quién responde
- Nombre: Rodrigo Lauro
- Cargo: Cofundador y responsable técnico
- Texto: Ingeniero en Sistemas. Vivo en Madrid y puedo reunirme contigo en persona. El equipo trabaja desde Argentina con horario solapado con la jornada española.
- `alt` de la foto: Rodrigo Lauro, cofundador de Código Nativo

**EN**
- Eyebrow: Who is accountable
- Cargo: Co-founder and technical lead
- Texto: Systems engineer. I live in Madrid and can meet you in person. The team works from Argentina with hours that overlap the Spanish working day.
- `alt`: Rodrigo Lauro, co-founder of Código Nativo

### 10. Contacto

`id="contacto"`. Formulario con Formspree, centrado, dentro de una tarjeta.

- `<form action="https://formspree.io/f/XXXX" method="POST">` — reemplazar `XXXX` por la dirección que pase Rodrigo.
- Envío **simple** (el formulario se manda de forma normal y Formspree muestra su página de agradecimiento). No hace falta JavaScript para enviar.
- Campos (todos con `label` visible y `name`): nombre (obligatorio), empresa (obligatorio), email (obligatorio, `type="email"`), mensaje (obligatorio, `textarea`).
- Agregar un campo oculto `_subject` con el valor "Contacto desde la web".

**ES**
- Eyebrow: Contacto
- Título: Cuéntanos qué perfiles necesitas
- Texto: Te respondemos en menos de 24 horas laborables.
- Labels: Nombre · Empresa · Email · ¿Qué perfiles necesitas y para cuándo?
- Botón: Enviar

**EN**
- Eyebrow: Contact
- Título: Tell us which profiles you need
- Texto: We reply within one business day.
- Labels: Name · Company · Email · Which profiles do you need, and by when?
- Botón: Send

Como el formulario también existe en dos idiomas, alcanza con duplicar los textos (labels, título y botón) con las clases `lang-es` / `lang-en`. El formulario en sí puede ser uno solo.

### 11. Footer

- Logo + "Código Nativo"
- Email: rodrigo.lauro@codigonativo.com.ar (enlace `mailto:`)
- LinkedIn: enlace a la página de la empresa (Rodrigo te pasa la dirección)
- Ubicación — ES: Meco (Madrid) · Buenos Aires — EN: Meco (Madrid, Spain) · Buenos Aires, Argentina
- © 2026 Código Nativo

## Lo que NO hay que hacer

- No mencionar el producto de flota ni enlazar a su web.
- No poner precios ni tarifas.
- No inventar números, clientes, testimonios ni años de experiencia.
- No usar logos de clientes.
- No usar colores: solo negro, blanco y grises (en particular, nada de violeta).
- No usar frameworks, librerías de JavaScript ni herramientas de compilación.

## Cuando termines

1. Explicale a Rodrigo la estructura del archivo: qué hay en el `<head>`, en el `<style>`, en el `<body>` y en el `<script>`.
2. Decile cómo abrir la página con Live Server.
3. Pasale la lista de cosas que tiene que revisar: logo, foto, formulario de prueba (que envíe un mensaje a sí mismo para comprobar que llega) y la vista en celular.
