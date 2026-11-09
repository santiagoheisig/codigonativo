# Brief: Landing de Código Nativo (codigonativo.com.ar)

Este archivo tiene dos partes:

- **Parte 1, para Rodrigo:** cómo armar el proyecto desde cero en VS Code y cómo pasárselo a Claude.
- **Parte 2, para Claude:** qué construir, con qué diseño y con qué textos (español e inglés).

Versión 2: el mensaje pasa de "equipos de Data e IA para consultoras" a "agentes de IA y RAG en producción sobre GCP".

**Regla de escritura:** nunca usar el guion largo (el carácter de raya) en ningún texto, ni en la web, ni en comentarios, ni en este archivo.

---

# PARTE 1: PARA RODRIGO

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

1. **Formspree:** el formulario todavía apunta a `https://formspree.io/f/XXXX`. Hay que reemplazar `XXXX` por tu código.
2. **Unilever:** si la migración de Azure a GCP fue parte de los 4 años. El texto actual dice "incluida la migración", que asume que sí.
3. **Horario solapado con España:** que el equipo en Argentina pueda trabajar con varias horas en común con la jornada española.
4. **Teléfono:** no hay ninguno. Si tenés número español, se puede agregar en el contacto.

---

# PARTE 2: PARA CLAUDE

## Contexto

Código Nativo es una empresa argentina de 4 personas que se hace cargo de **una parte concreta de un proyecto de IA sobre GCP**: el agente, el RAG o los pipelines de datos que lo sostienen. El lector de la web es un Business Manager, Delivery Manager o responsable de práctica de una consultora española. Su miedo no es técnico: es quedar mal frente a su propio cliente. La web tiene que transmitir seriedad, bajo riesgo y que hay alguien que responde por el resultado.

## Cómo trabajar con Rodrigo (obligatorio)

- Rodrigo quiere **entender** lo que hacés, no solo recibir el resultado. Explicá cada paso en español rioplatense, de forma simple.
- El código tiene que ser **simple y fácil de entender por alguien que recién empieza a programar**. Nada de frameworks, librerías de JavaScript, herramientas de compilación ni npm.
- **Comentarios en español** dentro del código, explicando qué hace cada sección del HTML, cada bloque importante del CSS y cada función del JavaScript.
- Antes de ejecutar cualquier comando o crear archivos, decile qué vas a hacer y para qué, y recordale que también lo puede hacer a mano.
- Antes de escribir código, proponé en pocas líneas cómo vas a armar la página y esperá su OK.
- No hacer commit ni publicar nada sin preguntarle.
- Nunca usar el guion largo.

## Requisitos técnicos

- **Un solo archivo `index.html`** con el CSS dentro de una etiqueta `<style>` y el JavaScript dentro de una etiqueta `<script>`. Las imágenes van en `assets/`.
- Única dependencia externa permitida: la tipografía **Inter** desde Google Fonts.
- **Responsive:** tiene que verse bien desde 360 px de ancho (celular) hasta pantallas grandes. Sin scroll horizontal.
- **Accesible:** contraste suficiente, `alt` en las imágenes, `label` en los campos del formulario, navegable con teclado, `lang` correcto en el `<html>`.
- Respetar `prefers-reduced-motion`: si el usuario pidió menos animación en su sistema, desactivar transiciones y animaciones.
- **SEO y vista previa al compartir:** `<title>`, `<meta name="description">` y etiquetas Open Graph (`og:title`, `og:description`, `og:image` apuntando a `assets/og-image.png`, `og:url`). Importante: la web se va a compartir en LinkedIn y tiene que mostrar una vista previa correcta.
- **Favicon:** usar `assets/logo-simbolo.svg` con `<link rel="icon" type="image/svg+xml">`.

### Título y descripción

- Título ES: Código Nativo | IA y datos en GCP
- Título EN: Código Nativo | AI and data on GCP
- Description: Agentes de IA y RAG en producción sobre GCP. Nos hacemos cargo del agente, el RAG o los pipelines de datos que lo sostienen, con un solo interlocutor técnico en Madrid.

## Diseño: dirección "oscuro con brillos", monocromo

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
- Etiqueta pequeña sobre los títulos ("eyebrow"): mayúsculas (con CSS, el texto se escribe normal), 0.8rem, `letter-spacing: 0.08em`, color `--accent`.

### Espaciado y layout

- Ancho máximo del contenido: 1120 px, centrado.
- Margen lateral: 24 px en escritorio, 16 px en celular.
- Separación entre secciones: unos 120 px en escritorio y 72 px en celular.
- Tarjetas: `border-radius: 16px`, borde de 1 px con `--border`, fondo `--bg-elevated` con un degradado muy sutil. Al pasar el mouse, el borde pasa a `--border-hover`.

### Efectos

- **Brillo del hero:** un degradado radial blanco muy suave (`--accent-soft`) arriba del título, que se desvanece hacia los costados.
- **Puntos de luz:** algunos puntos blancos pequeños y tenues dispersos en el fondo del hero, evocando el banner de la marca. Con CSS simple, sin canvas ni librerías.
- **Grilla sutil:** detrás del hero, líneas finas de grilla casi invisibles que se desvanecen hacia los bordes (con `mask-image`).
- **Animación al hacer scroll:** las secciones aparecen con un fundido suave y un pequeño desplazamiento hacia arriba. Usar `IntersectionObserver` con código simple y comentado. Sin librerías.
- **Nada exagerado:** el brillo es un acompañamiento, no el protagonista. El contenido tiene que leerse perfecto.

### Header

- Fijo arriba (`position: sticky`), con fondo semitransparente y desenfoque (`backdrop-filter: blur`).
- A la izquierda: logo + "Código Nativo".
- Al centro (solo escritorio): enlaces a Cómo trabajamos, Qué hacemos, Casos y Contacto.
- A la derecha: botón **ES / EN** y botón principal "Contacto".
- En celular: se ocultan los enlaces del centro; quedan logo, ES/EN y el botón de contacto.

### Logo: `assets/logo-simbolo.svg`

El símbolo de la marca es un **óvalo vertical con una línea vertical que lo divide por la mitad**, de arriba abajo. Trazo blanco, sin relleno, con grosor de trazo de aproximadamente el 7% del ancho. Proporción aproximada: alto = 1,24 × ancho.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 124">
  <ellipse cx="50" cy="62" rx="46" ry="58" fill="none" stroke="#FFFFFF" stroke-width="7"/>
  <line x1="50" y1="4" x2="50" y2="120" stroke="#FFFFFF" stroke-width="7"/>
</svg>
```

- Usarlo en el header (unos 28 a 32 px de alto) y en el footer (más grande), siempre seguido del texto "Código Nativo" en Inter, peso 500.
- Usarlo también como favicon.

## Cambio de idioma español / inglés

Implementarlo de la forma **más simple de entender**:

- Cada texto existe dos veces: una con la clase `lang-es` y otra con la clase `lang-en`.
- El `<body>` tiene la clase `show-es` o `show-en`.
- Con CSS se oculta el idioma que no corresponde: `.show-es .lang-en { display: none; }` y `.show-en .lang-es { display: none; }`.
- El botón ES/EN cambia la clase del `<body>` y actualiza el atributo `lang` del `<html>`.
- Idioma por defecto: español.
- Recordar la elección con `localStorage`, siempre dentro de `try/catch` para que la página funcione aunque el navegador lo bloquee.

## Estructura de la página

1. Header
2. Hero
3. Franja de clientes
4. Por qué nosotros
5. Cómo trabajamos
6. Qué hacemos
7. Cómo empezamos
8. Casos
9. Quién responde (foto de Rodrigo)
10. Contacto (formulario)
11. Footer

## Textos

Español de España con tuteo (no voseo). No cambiar el sentido de los textos. Se pueden hacer ajustes menores de longitud si el diseño lo pide, avisando a Rodrigo. Los nombres de tecnologías y de clientes no se traducen.

### 1. Header

| | ES | EN |
|---|---|---|
| Enlaces | Cómo trabajamos · Qué hacemos · Casos · Contacto | How we work · What we do · Case studies · Contact |
| Botón | Contacto | Contact |

### 2. Hero

**ES**
- Eyebrow: IA y datos en GCP
- Título: Agentes de IA y RAG en producción sobre GCP. Respondemos por el resultado.
- Subtítulo: Nos hacemos cargo de una parte concreta de tu proyecto: el agente, el RAG o los pipelines de datos que lo sostienen. Un solo interlocutor técnico en Madrid, trabajo dentro de tus herramientas y un equipo que ejecuta desde Argentina con horario solapado.
- Botón principal: Cuéntanos el proyecto → enlaza a `#contacto`
- Botón secundario: Ver casos → enlaza a `#casos`

**EN**
- Eyebrow: AI and data on GCP
- Título: AI agents and RAG in production on GCP. We are accountable for the outcome.
- Subtítulo: We take ownership of a specific part of your project: the agent, the RAG system or the data pipelines behind it. One technical point of contact in Madrid, work inside your tools, and a team delivering from Argentina with overlapping hours.
- Botón principal: Tell us about the project
- Botón secundario: See case studies

### 3. Franja de clientes

Solo texto, **sin logos** (los logos de otras marcas no se usan sin permiso). Nombres separados por puntos medios.

- ES: Han trabajado con nosotros: Unilever · Whirlpool · Ayesa · Puma · Grupo Dota
- EN: Companies we have worked with: Unilever · Whirlpool · Ayesa · Puma · Grupo Dota

### 4. Por qué nosotros

Cuatro tarjetas en 2 columnas, sin párrafo de introducción.

**ES**
- Eyebrow: Por qué nosotros
- Título: Muchos proyectos de IA no pasan del piloto. Casi nunca es el modelo: son los datos que hay debajo.

1. **Un responsable, no personas sueltas.** Hablas con una persona que responde por la entrega. Quién la ejecuta es asunto nuestro.
2. **Dentro de tus procesos.** Tu Jira, tu repositorio, tus code reviews. Ves todo, todo el tiempo.
3. **Entregas cortas.** Algo demostrable cada semana y un reporte breve de avance y riesgos.
4. **Reemplazos a nuestro cargo.** Si alguien sale, lo cubrimos nosotros, sin coste para ti.

**EN**
- Eyebrow: Why us
- Título: Many AI projects never get past the pilot. It is rarely the model: it is the data underneath.

1. **One accountable lead, not loose individuals.** You talk to one person who is accountable for the delivery. Who does the work is our concern.
2. **Inside your processes.** Your Jira, your repo, your code reviews. You see everything, all the time.
3. **Short delivery cycles.** Something you can demo every week, plus a brief report on progress and risks.
4. **Replacements on us.** If someone leaves, we cover it, at no cost to you.

### 5. Cómo trabajamos

Tres tarjetas en 3 columnas (en celular, una debajo de otra). La primera, destacada (borde más claro y etiqueta "Para empezar" / "To start").

**ES**
- Eyebrow: Cómo trabajamos
- Título: Tres formas de trabajar con nosotros

1. **Paquete cerrado** (etiqueta: Para empezar). Entregable definido, precio fijo, fecha y pago por hito.
2. **Equipo dedicado.** De 1 a 3 personas por mes, con responsable técnico. Mínimo 3 meses.
3. **Soporte y evolución mensual.** Mantenemos tu plataforma de datos en marcha: monitorización, corrección de errores y cambios. Bolsa de horas mensual, sin depender de una sola persona.

**EN**
- Eyebrow: How we work
- Título: Three ways to work with us

1. **Fixed package** (label: To start). Defined deliverable, fixed price, set date and payment per milestone.
2. **Dedicated team.** 1 to 3 people per month, with a technical lead. 3-month minimum.
3. **Monthly support and evolution.** We keep your data platform running: monitoring, fixing failures and making changes. A monthly block of hours, without depending on a single person.

### 6. Qué hacemos

`id="que-hacemos"`. Cuatro tarjetas en 2 columnas. Cada una con un título, una frase y las tecnologías en "chips" (pastillas pequeñas con borde).

**ES**
- Eyebrow: Qué hacemos
- Título: De qué podemos hacernos cargo en tu proyecto

1. **Agentes de IA.** Agentes y sistemas multiagente con respuestas trazables y fuentes citadas. Chips: Vertex AI · Gemini · Google ADK · Sistemas multiagente
2. **RAG sobre tus datos.** Consulta en lenguaje natural sobre documentos y BigQuery, con evaluación de respuestas. Chips: RAG · BigQuery Vector Search · Python · Text-to-SQL
3. **Pipelines de datos.** Ingesta, orquestación y modelado, hasta el cuadro de mando en Looker, Power BI o Tableau: la base que necesita cualquier sistema de IA. Chips: Cloud Composer · Airflow · Dataflow · Pub/Sub · BigQuery · Looker · Power BI · Tableau
4. **Migración a GCP.** De on-premise o Azure a BigQuery, con infraestructura como código. Chips: Azure → GCP · Terraform · Kubernetes

**EN**
- Eyebrow: What we do
- Título: What we can take ownership of in your project

1. **AI agents.** Agents and multi-agent systems with traceable answers and cited sources. Chips: Vertex AI · Gemini · Google ADK · Multi-agent systems
2. **RAG on your data.** Natural-language queries over documents and BigQuery, with answer evaluation.
3. **Data pipelines.** Ingestion, orchestration and modeling, all the way to dashboards in Looker, Power BI or Tableau: the foundation every AI system needs.
4. **Migration to GCP.** From on-premises or Azure to BigQuery, with infrastructure as code.

### 7. Cómo empezamos

Tres pasos numerados (estilo proceso, con el número grande en blanco, con degradado).

**ES**
- Eyebrow: Cómo empezamos
- Título: Sin riesgo para ti frente a tu cliente

1. **Diagnóstico inicial.** Dos o tres días revisando tu caso, con un documento de hallazgos.
2. **Piloto de 4 semanas.** Revisión a los 15 días con un entregable definido por escrito. Si no encaja, lo dejamos ahí.
3. **Pago por hito.** Pagas lo que ya viste.

**EN**
- Eyebrow: How we start
- Título: No risk for you in front of your client

1. **Initial assessment.** Two or three days reviewing your case, with a findings document.
2. **4-week pilot.** A review at day 15, against a deliverable defined in writing. If it is not a fit, we stop there.
3. **Payment per milestone.** You pay for what you have already seen.

### 8. Casos

`id="casos"`. Cinco tarjetas en 2 columnas, todas del mismo ancho; la quinta ocupa el ancho completo. Cada tarjeta: cliente, título, texto breve y chips de stack. Orden: Ayesa, Banca, Unilever, Whirlpool, Grupo Dota.

**ES**
- Eyebrow: Casos
- Título: Lo que hemos hecho

1. **Ayesa: Datos e IA para el sector público.** Plataforma de datos en GCP sobre fuentes muy distintas entre sí (webs, XML, APIs), con gobierno del dato por capas. Sobre ella, agentes de IA que responden preguntas en lenguaje natural, hoy en producción. Chips: BigQuery · Airflow · Dataproc/Spark · GKE · Vertex AI · Gemini
2. **Banca: Sistema multiagente en producción.** Para analistas de riesgo y negocio. Cada respuesta cita su fuente o dice que no tiene datos, solo lee datos curados y anonimizados, y todo queda auditado. Chips: Google ADK · Gemini · Vertex AI Agent Engine · BigQuery Vector Search
3. **Unilever: 4 años como equipo dedicado.** Un equipo de 5 personas sobre una base de 500 tablas alimentada por distintos proveedores, incluida la migración de su ETL de Azure a GCP. Parte de ese equipo trabaja hoy en Código Nativo. Chips: Python · SQL · Airflow · BigQuery · Azure → GCP · Power BI
4. **Whirlpool: Sell out unificado.** Unificamos el sell out de sus clientes, que llegaba en formatos dispares, y lo cruzamos con las ventas de SAP. Pasaron de informes mensuales a ventas actualizadas cada hora. Chips: SAP · ETL · Tableau
5. **Grupo Dota: Modelos predictivos sobre 1.500 autobuses.** Predicción de consumo, stock y gastos, desgaste de neumáticos por marca y perfiles de riesgo de siniestralidad, sobre los datos operativos de la flota. Chips: Machine Learning · Regresión · Random Forest

**EN**
- Eyebrow: Case studies
- Título: What we have done

1. **Ayesa: Data and AI for the public sector.** A GCP data platform over highly heterogeneous sources (web, XML, APIs), with layered data governance. On top of it, AI agents that answer questions in natural language, now in production.
2. **Banking: Multi-agent system in production.** For risk and business analysts. Every answer cites its source or says there is no data, it only reads curated and anonymized data, and everything is audited.
3. **Unilever: 4 years as a dedicated team.** A 5-person team on a 500-table database fed by multiple vendors, including the migration of their ETL from Azure to GCP. Part of that team works at Código Nativo today.
4. **Whirlpool: Unified sell-out.** We unified their customers' sell-out data, which arrived in disparate formats, and joined it with SAP sales. They went from monthly reports to sales updated every hour.
5. **Grupo Dota: Predictive models on 1,500 buses.** Forecasting of fuel consumption, stock and costs, tire wear by brand and accident-risk profiles, on the fleet's operational data.

### 9. Quién responde

Dos columnas: foto a la izquierda (`assets/rodrigo-lauro.jpg`, con bordes redondeados y un brillo blanco suave detrás) y texto a la derecha. En celular, foto arriba.

**ES**
- Eyebrow: Quién responde
- Nombre: Rodrigo Lauro
- Cargo: Cofundador y responsable técnico
- Texto: Ingeniero en Sistemas, especialización en Inteligencia Artificial (UBA). Estoy en Madrid: cada proyecto empieza con una reunión en persona y respondo por cada entrega. Si tu arquitecto quiere entrevistarme antes de empezar, encantado. El equipo trabaja desde Argentina con horario solapado con la jornada española.
- `alt` de la foto: Rodrigo Lauro, cofundador de Código Nativo

**EN**
- Eyebrow: Who is accountable
- Cargo: Co-founder and technical lead
- Texto: Systems Engineer, specialized in Artificial Intelligence (UBA). I am based in Madrid: every project starts with an in-person meeting, and I am accountable for every delivery. If your architect wants to interview me before we start, I am happy to meet them. The team works from Argentina with hours that overlap the Spanish working day.
- `alt`: Rodrigo Lauro, co-founder of Código Nativo

### 10. Contacto

`id="contacto"`. Formulario con Formspree, centrado, dentro de una tarjeta.

- `<form action="https://formspree.io/f/XXXX" method="POST">`: reemplazar `XXXX` por la dirección que pase Rodrigo.
- Envío **simple** (el formulario se manda de forma normal y Formspree muestra su página de agradecimiento). No hace falta JavaScript para enviar.
- Campos (todos con `label` visible y `name`): nombre (obligatorio), empresa (obligatorio), email (obligatorio, `type="email"`), mensaje (obligatorio, `textarea`).
- Campo oculto `_subject` con el valor "Contacto desde la web".

**ES**
- Eyebrow: Contacto
- Título: Cuéntanos el proyecto
- Texto: Qué hay que construir, en qué plazo y con qué stack. Te respondemos en 24 horas.
- Labels: Nombre · Empresa · Email · ¿Qué hay que construir y para cuándo?
- Botón: Enviar

**EN**
- Eyebrow: Contact
- Título: Tell us about the project
- Texto: What needs to be built, by when and on which stack. We reply within 24 hours.
- Labels: Name · Company · Email · What needs to be built, and by when?
- Botón: Send

### 11. Footer

- Logo + "Código Nativo"
- Email: rodrigo.lauro@codigonativo.com.ar (enlace `mailto:`)
- LinkedIn: https://www.linkedin.com/company/codigo-nativo/
- Ubicación ES: Meco (Madrid) · Buenos Aires. EN: Meco (Madrid, Spain) · Buenos Aires, Argentina
- © 2026 Código Nativo

## Lo que NO hay que hacer

- No usar el guion largo en ningún texto.
- No mencionar dbt.
- No poner precios ni tarifas.
- No mencionar el producto de flota ni enlazar a su web.
- No inventar números, clientes, testimonios ni años de experiencia.
- No usar logos de clientes.
- No usar colores: solo negro, blanco y grises (en particular, nada de violeta).
- No usar frameworks, librerías de JavaScript ni herramientas de compilación.
