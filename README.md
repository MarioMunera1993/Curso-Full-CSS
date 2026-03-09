# Curso-CSS

## ¿Que es CSS?

CSS (Cascading Style Sheets) es el lenguaje que controla como se ve todo lo que estructuraste con HTML

si HTML es el esqueleto y CSS es:

- la piel y la ropa
- los colores y tipografía
- el tamaño y la posición de cada cosa
- las animaciones y transiciones

## 🔗 Las 3 formas de agregar CSS

```css
<!-- ❌ FORMA 1 — Inline: estilos directamente en el elemento -->
<!-- Evitar: difícil de mantener, no reutilizable -->
<p style="color: red; font-size: 20px;">Texto rojo</p>

<!-- ❌ FORMA 2 — Internal: dentro del HTML en etiqueta style -->
<!-- Solo para pruebas rápidas -->
<head>
  <style>
    p { color: red; }
  </style>
</head>

<!-- ✅ FORMA 3 — External: archivo .css separado (siempre esta) -->
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

## 🎯 Selectores CSS

Los selectores le dicen a CSS **a qué elementos** aplicar los estilos:

```css
/* ELEMENTO: afecta todos los <p> */
p {
  color: #1E293B;
}

/* CLASE: afecta todo lo que tenga class="tarjeta" */
.tarjeta {
  background: white;
}

/* ID: afecta el elemento con id="header" */
/* Úsalo poco — las clases son más flexibles */
#header {
  height: 80px;
}

/* DESCENDIENTE: <a> que estén dentro de <nav> */
nav a {
  text-decoration: none;
}

/* HIJO DIRECTO: solo <li> hijos directos de <ul> */
ul > li {
  list-style: none;
}

/* MÚLTIPLES: aplica a h1, h2 y h3 al mismo tiempo */
h1, h2, h3 {
  font-family: 'Courier New', monospace;
}

/* UNIVERSAL: afecta absolutamente todo */
* {
  box-sizing: border-box; /* Ya veremos esto */
}

/* ATRIBUTO: elementos con un atributo específico */
input[type="email"] {
  border: 2px solid #00FFB2;
}

a[target="_blank"] {
  color: #A78BFA;
}
```

## ## 📦 El Box Model — El concepto más importante de CSS

Todo en CSS es una caja.** Cada elemento HTML es una caja rectangular con 4 capas:

```html
┌─────────────────────────────────────┐
│              MARGIN                 │  ← Espacio FUERA del elemento
│  ┌───────────────────────────────┐  │
│  │            BORDER             │  │  ← El borde del elemento
│  │  ┌─────────────────────────┐  │  │
│  │  │         PADDING         │  │  │  ← Espacio DENTRO del elemento
│  │  │  ┌───────────────────┐  │  │  │
│  │  │  │                   │  │  │  │
│  │  │  │      CONTENT      │  │  │  │  ← El contenido real
│  │  │  │                   │  │  │  │
│  │  │  └───────────────────┘  │  │  │
│  │  └─────────────────────────┘  │  │
│  └───────────────────────────────┘  │
└─────────────────────────────────────┘
```

```css
.caja {
  /* CONTENT: tamaño del contenido */
  width: 300px;
  height: 200px;

  /* PADDING: espacio interior (entre contenido y borde) */
  padding: 20px;              /* todos los lados */
  padding: 10px 20px;         /* arriba/abajo  izquierda/derecha */
  padding: 10px 20px 15px 5px;/* arriba derecha abajo izquierda */
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 15px;
  padding-left: 5px;

  /* BORDER: el borde */
  border: 2px solid #00FFB2;
  border-radius: 8px;         /* esquinas redondeadas */
  border-top: 3px dashed red; /* solo un lado */

  /* MARGIN: espacio exterior (entre este elemento y los demás) */
  margin: 20px;
  margin: 0 auto;             /* centrar horizontalmente */
  margin-top: 40px;
}
```

## ⚠️ El problema del Box Model y cómo resolverlo

Por defecto CSS suma padding y border al width, lo que genera confusión:

```css
/* ❌ PROBLEMA: la caja mide 300 + 40 + 4 = 344px en total */
.caja {
  width: 300px;
  padding: 20px;   /* suma 40px (20 cada lado) */
  border: 2px solid black; /* suma 4px (2 cada lado) */
}

/* ✅ SOLUCIÓN: box-sizing: border-box */
/* El width INCLUYE padding y border. Siempre usa esto. */
* {
  box-sizing: border-box;
}

.caja {
  width: 300px;    /* ahora SÍ mide exactamente 300px en total */
  padding: 20px;
  border: 2px solid black;
}
```

## 💡 **Esta línea va en TODOS tus proyectos CSS:**

```css
 *{ box-sizing: border-box; }
```

## 🎨 Colores en CSS

```css
.elemento {
  /* NOMBRE: 140 colores con nombre */
  color: red;
  color: tomato;
  color: steelblue;

  /* HEX: el más usado */
  color: #FF6B6B;
  color: #fff;        /* shorthand de #ffffff */

  /* RGB */
  color: rgb(255, 107, 107);

  /* RGBA: con transparencia (0=transparente, 1=sólido) */
  color: rgba(255, 107, 107, 0.5);

  /* HSL: Hue Saturation Lightness — el más intuitivo */
  color: hsl(0, 100%, 71%);

  /* HSLA: con transparencia */
  color: hsla(0, 100%, 71%, 0.5);
}
```

## ✍️ Tipografía

```css
.texto {
  /* FAMILIA: fuente a usar */
  font-family: 'Courier New', Courier, monospace;
  /* Siempre incluir fuentes de respaldo */
  font-family: Georgia, 'Times New Roman', serif;
  font-family: Arial, Helvetica, sans-serif;

  /* TAMAÑO */
  font-size: 16px;     /* píxeles — fijo */
  font-size: 1rem;     /* relativo al root (html). 1rem = 16px por defecto */
  font-size: 1.2em;    /* relativo al padre */

  /* PESO */
  font-weight: normal;  /* 400 */
  font-weight: bold;    /* 700 */
  font-weight: 300;     /* light */
  font-weight: 900;     /* black */

  /* ESTILO */
  font-style: italic;
  font-style: normal;

  /* ALTURA DE LÍNEA: espacio entre líneas */
  line-height: 1.6;    /* sin unidad = relativo al font-size */
  line-height: 24px;

  /* ESPACIADO entre letras */
  letter-spacing: 2px;
  letter-spacing: -0.5px;

  /* ALINEACIÓN */
  text-align: left;
  text-align: center;
  text-align: right;
  text-align: justify;

  /* DECORACIÓN */
  text-decoration: none;       /* quita subrayado de enlaces */
  text-decoration: underline;
  text-decoration: line-through;

  /* TRANSFORMACIÓN */
  text-transform: uppercase;
  text-transform: lowercase;
  text-transform: capitalize;
}
```

## 🌐 Google Fonts — Fuentes externas

```html
<!-- En el <head> de tu HTML -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link 
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Fira+Code:wght@400;600&display=swap" 
  rel="stylesheet" 
/>
```

```css
/* En tu CSS */
body {
  font-family: 'Inter', sans-serif;
}

code {
  font-family: 'Fira Code', monospace;
}
```

## 🌊 La Cascada y Especificidad

**CSS = Cascading** significa que cuando dos reglas se contradicen, gana la más **específica** o la última en el archivo:

```css
/* Especificidad de menor a mayor: */

/* 1. Elemento        → especificidad: 0,0,1 */
p { color: blue; }

/* 2. Clase           → especificidad: 0,1,0 */
.texto { color: red; }

/* 3. ID              → especificidad: 1,0,0 */
#parrafo { color: green; }

/* 4. Inline style    → especificidad: máxima */
/* <p style="color: pink"> */

/* 5. !important      → rompe la cascada (EVITAR) */
p { color: purple !important; }
```

```html
<!-- ¿De qué color es este párrafo? -->
<p id="parrafo" class="texto" style="color: pink">
  ¿Qué color soy?
</p>
<!-- Respuesta: PINK — inline style gana -->
```

💡 **Regla práctica:** Usa siempre **clases**. Evita IDs para estilos y nunca uses `!important` salvo emergencias.

## ¿Qué es Flexbox y por qué cambió todo?

Antes de Flexbox, hacer layouts en CSS era un dolor. Centrar algo verticalmente requería trucos extraños. Flexbox llegó en 2009 y **resolvió el problema de distribución y alineación** de elementos de una vez por todas.

**Flexbox es unidimensional** — trabaja en una sola dirección a la vez: fila (horizontal) o columna (vertical).

## 🧠 El concepto base: contenedor e hijos

┌─────────────────────────────────────────┐
│         FLEX CONTAINER (padre)                                                                    │
│  ┌───────┐  ┌───────┐  ┌───────┐                                    │
│  │       hijo1      │  │      hijo2      │  │ hijo3           │                                    │
│  └───────┘  └───────┘  └───────┘                                    │
└─────────────────────────────────────────┘

- El **padre** recibe `display: flex` → se convierte en flex container
- Los **hijos directos** se convierten automáticamente en flex items
- Las propiedades de Flexbox se dividen en: las que van en el **padre** y las que van en los **hijos**

## PROPIEDADES DEL PADRE (flex container)

`display: flex` — Activar Flexbox

```css
.contenedor {
  display: flex; /* activa flexbox en este elemento */
}
```

```html
<div class="contenedor">
  <div>Hijo 1</div>
  <div>Hijo 2</div>
  <div>Hijo 3</div>
</div>
```

## `flex-direction` — Dirección del eje principal

```css
.contenedor {
  display: flex;

  flex-direction: row;            /* → izquierda a derecha (defecto) */
  flex-direction: row-reverse;    /* ← derecha a izquierda */
  flex-direction: column;         /* ↓ arriba hacia abajo */
  flex-direction: column-reverse; /* ↑ abajo hacia arriba */
}
```
```
row:             [hijo1] [hijo2] [hijo3]
row-reverse:     [hijo3] [hijo2] [hijo1]
column:          [hijo1]
                 [hijo2]
                 [hijo3]
```

## `justify-content` — Alineación en el eje principal

```css
/* Con flex-direction: row → controla el eje HORIZONTAL */
.contenedor {
  display: flex;

  justify-content: flex-start;    /* ← todos al inicio (defecto) */
  justify-content: flex-end;      /* → todos al final */
  justify-content: center;        /* → centrados */
  justify-content: space-between; /* primer y último en los extremos, resto distribuido */
  justify-content: space-around;  /* espacio igual alrededor de cada hijo */
  justify-content: space-evenly;  /* espacio exactamente igual entre todos */
}
```
```
flex-start:    [h1][h2][h3]·············
flex-end:      ·············[h1][h2][h3]
center:        ······[h1][h2][h3]······
space-between: [h1]·······[h2]·······[h3]
space-around:  ··[h1]····[h2]····[h3]··
space-evenly:  ···[h1]···[h2]···[h3]···
```

## `align-items` — Alineación en el eje secundario

```css
/* Con flex-direction: row → controla el eje VERTICAL */
.contenedor {
  display: flex;
  height: 200px; /* necesita altura para verse */

  align-items: stretch;     /* estira los hijos (defecto) */
  align-items: flex-start;  /* alinea arriba */
  align-items: flex-end;    /* alinea abajo */
  align-items: center;      /* centra verticalmente ← el famoso */
  align-items: baseline;    /* alinea por la línea base del texto */
}
```

## ⭐ El centrado perfecto — 3 líneas de código

```css
/* Esto era imposible de forma simple antes de Flexbox */
.centrado-perfecto {
  display: flex;
  justify-content: center; /* centra horizontal */
  align-items: center;     /* centra vertical */
}
```

## `flex-wrap` — Salto de línea

```css
.contenedor {
  display: flex;

  flex-wrap: nowrap;  /* todos en una línea aunque se salgan (defecto) */
  flex-wrap: wrap;    /* saltan a la siguiente línea si no caben */
  flex-wrap: wrap-reverse; /* saltan hacia arriba */
}
```

## `gap` — Espacio entre hijos

```css
.contenedor {
  display: flex;
  gap: 20px;          /* espacio entre todos los hijos */
  gap: 16px 24px;     /* gap-row gap-column */
  row-gap: 16px;      /* solo entre filas */
  column-gap: 24px;   /* solo entre columnas */
}
```

### 💡 `gap` reemplaza los viejos trucos con `margin`. Úsalo siempre.

## `flex-direction` + `justify-content` + `align-items` juntos

```css
/* Navbar típica: logo a la izquierda, links a la derecha */
nav {
  display: flex;
  justify-content: space-between; /* logo ←→ links */
  align-items: center;            /* alineados verticalmente */
  padding: 0 32px;
  height: 64px;
}
```

## PROPIEDADES DE LOS HIJOS (flex items)

### `flex` — Cómo crece y encoge cada hijo

```css
/* flex es shorthand de: flex-grow flex-shrink flex-basis */

.hijo {
  flex: 1;        /* crece para llenar el espacio disponible */
  flex: 2;        /* crece el doble que los de flex: 1 */
  flex: 0;        /* no crece ni encoge */
  flex: none;     /* tamaño fijo, no flexible */
}

/* Ejemplo: 3 columnas iguales */
.columna {
  flex: 1; /* cada una toma 1/3 del espacio */
}

/* Ejemplo: sidebar + contenido */
.sidebar  { flex: 0 0 280px; } /* ancho fijo de 280px */
.contenido { flex: 1; }        /* toma el resto del espacio */
```

## `align-self` — Alineación individual

```css
/* Sobreescribe align-items solo para este hijo */
.hijo-especial {
  align-self: flex-start; /* este hijo se va arriba */
  align-self: flex-end;   /* este hijo se va abajo */
  align-self: center;     /* este hijo se centra */
  align-self: stretch;    /* este hijo se estira */
}
```

## `order` — Orden visual

```css
/* Cambia el orden de visualización sin cambiar el HTML */
.primero  { order: -1; } /* aparece antes de todos */
.ultimo   { order: 10; } /* aparece después de todos */
/* El orden defecto de todos es 0 */
```

## 🛠️ MINI PROYECTO 7 — Layouts reales con Flexbox

Crea `flexbox.html` y `flexbox.css`. Vamos a construir **4 layouts** que usarás en todos tus proyectos:

## ✅ Lo que aprendiste en esta lección

**En el padre:**

- `display: flex` — activa Flexbox
- `flex-direction` — fila o columna
- `justify-content` — distribución en eje principal
- `align-items` — alineación en eje secundario
- `flex-wrap` — salto de línea
- `gap` — espacio entre hijos

**En los hijos:**

- `flex: 1` — crecimiento proporcional
- `flex: 0 0 Xpx` — tamaño fijo
- `align-self` — alineación individual
- `order` — orden visual

**Layouts reales construidos:**

- Navbar con logo, links y botones
- Hero centrado perfectamente
- Tarjetas flexibles con footer pegado abajo
- Sidebar fijo + contenido flexible