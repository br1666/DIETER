# 📚 CONCEPTOS TÉCNICOS - EJEMPLOS APLICADOS

## 1️⃣ BOX MODEL (Modelo de Caja)

### ¿Qué es?
Cada elemento HTML es una caja con 4 capas:
- **Content**: El contenido
- **Padding**: Espacio DENTRO de la caja
- **Border**: Borde externo
- **Margin**: Espacio FUERA de la caja

### Visualización:
```
┌─────────────────────────────────────────┐
│         MARGIN (espacio afuera)         │
│  ┌───────────────────────────────────┐  │
│  │  BORDER (línea)                   │  │
│  │  ┌─────────────────────────────┐  │  │
│  │  │ PADDING (espacio dentro)    │  │  │
│  │  │  ┌───────────────────────┐  │  │  │
│  │  │  │   CONTENT             │  │  │  │
│  │  │  │   (texto, imágenes)   │  │  │  │
│  │  │  └───────────────────────┘  │  │  │
│  │  └─────────────────────────────┘  │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

### En tu proyecto:

#### HEADER con Box Model visible:
```css
header {
    background-color: var(--white);
    border-bottom: 1px solid var(--black);  /* BORDER */
    padding: 30px 40px;                     /* PADDING */
    margin: 0;                              /* MARGIN */
}

header h1 {
    margin: 0;                              /* Sin margen */
    padding: 10px 0;                        /* Espacio interno */
    font-size: 1.2rem;
}
```

#### PRINCIPIOS con Box Model aplicado:
```css
.principle-item {
    padding: 60px 0;           /* 60px arriba/abajo, 0 izq/der */
    margin: 0;                 /* Sin margen */
    border-bottom: 1px solid var(--grey-mid);  /* Borde inferior */
}

.principle-number {
    min-width: 80px;           /* Ancho mínimo */
    margin-right: 30px;        /* Espacio a la derecha */
    padding: 10px;             /* Espacio interno */
}
```

#### SOCIAL LINKS con Box Model:
```css
.social-link {
    width: 44px;               /* Ancho */
    height: 44px;              /* Alto */
    padding: 0;                /* Sin padding (contenido centrado) */
    margin: 5px;               /* Espacio entre links */
    border: 1px solid var(--black);  /* Borde */
    display: flex;
    align-items: center;
    justify-content: center;
}
```

### 🔑 Propiedades clave:
```css
/* Margen (espacio AFUERA) */
margin: 20px;           /* Todos lados */
margin: 10px 20px;      /* Arriba/abajo, izq/der */
margin: 10px 20px 30px 40px;  /* Arriba, derecha, abajo, izquierda */

/* Padding (espacio DENTRO) */
padding: 20px;          /* Todos lados */
padding: 10px 20px;     /* Arriba/abajo, izq/der */
padding: 10px 20px 30px 40px;

/* Border (borde) */
border: 1px solid #000;
border-top: 1px solid;
border-bottom: 1px solid;
border-left: none;
border-right: none;

/* Box sizing - IMPORTANTE */
box-sizing: border-box;  /* Incluir border/padding en el ancho total */
```

### EN TU CÓDIGO:
```css
* {
    box-sizing: border-box;  /* ✅ RECOMENDADO */
}
```

---

## 2️⃣ FLEXBOX (Caja Flexible)

### ¿Qué es?
Sistema de distribución de elementos en una línea (fila o columna). Ideal para:
- Barras de navegación
- Headers
- Alineaciones verticales
- Distribución de espacio

### Propiedades del CONTENEDOR:

```css
.flex-container {
    display: flex;              /* Activar flexbox */
    
    /* Dirección */
    flex-direction: row;        /* horizontal (default) */
    /* flex-direction: column;  vertical */
    
    /* Justificar en eje principal */
    justify-content: space-between;  /* Espacio entre items */
    /* justify-content: center;     centro */
    /* justify-content: flex-start; inicio */
    /* justify-content: flex-end;   fin */
    
    /* Alinear en eje secundario */
    align-items: center;        /* Centro vertical */
    /* align-items: flex-start;  inicio */
    /* align-items: flex-end;    fin */
    
    /* Espacio entre items */
    gap: 20px;                  /* Espacio entre elementos */
    
    /* Si no caben, wrappear */
    flex-wrap: wrap;            /* Pasar a siguiente línea */
}
```

### En tu proyecto:

#### HEADER con Flexbox:
```css
.header-content {
    display: flex;
    justify-content: space-between;  /* Logo a izq, nav a der */
    align-items: center;              /* Centrado vertical */
    gap: 40px;
    flex-wrap: wrap;                 /* Responsivo */
}
```

#### NAVEGACIÓN con Flexbox:
```css
.nav-list {
    list-style: none;
    display: flex;
    gap: 40px;                   /* Espacio entre links */
    flex-wrap: wrap;             /* Wrappear en mobile */
    justify-content: center;     /* Centrado */
}
```

#### HERO SLIDER con Flexbox:
```css
.hero-slider {
    display: flex;
    align-items: center;         /* Centrado vertical */
    gap: 40px;                   /* Espacio entre botones y contenido */
    justify-content: center;
    flex-wrap: wrap;             /* En mobile, se apilan */
}
```

#### FOOTER con Flexbox:
```css
.footer-content {
    display: flex;
    justify-content: space-around;  /* Distribuir espaciado */
    flex-wrap: wrap;                /* Responsive */
    gap: 40px;
}

footer li {
    display: flex;               /* Si necesitas alinear items */
    gap: 10px;
}
```

#### SOCIAL LINKS con Flexbox:
```css
.social-links {
    list-style: none;
    display: flex;
    justify-content: center;     /* Centrado */
    flex-wrap: wrap;             /* Wrappear en mobile */
    gap: 20px;                   /* Espacio entre botones */
}
```

### Propiedades de ITEMS (dentro del flex):

```css
.flex-item {
    flex: 1;                     /* Crecer igual */
    flex-shrink: 0;              /* No encogerse */
    flex-basis: 200px;           /* Ancho base */
    min-width: 44px;             /* Mínimo ancho (importante para touch) */
}
```

### EN TU CÓDIGO - VERIFICAR:
```css
/* ✅ Todos estos deben tener display: flex o similar */
.header-content { display: flex; }
.nav-list { display: flex; }
.hero-slider { display: flex; }
.timeline-wrapper { display: flex; }
.social-links { display: flex; }
.footer-content { display: flex; } /* o grid */
```

---

## 3️⃣ CSS GRID (Red de Columnas)

### ¿Qué es?
Sistema bidimensional (filas Y columnas). Ideal para:
- Layouts complejos
- Galerías
- Grillas de contenido
- Responsivo automático

### Propiedades del CONTENEDOR:

```css
.grid-container {
    display: grid;              /* Activar grid */
    
    /* Definir columnas */
    grid-template-columns: repeat(12, 1fr);    /* 12 columnas iguales */
    /* grid-template-columns: repeat(3, 1fr);  3 columnas iguales */
    /* grid-template-columns: 200px 1fr 200px; Ancho específico */
    
    /* Responsive auto-fit */
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    
    /* Espacio entre items */
    gap: 30px;
    
    /* Altura de filas (opcional) */
    grid-auto-rows: auto;
}
```

### En tu proyecto:

#### PRINCIPLES GRID - ⭐ EJEMPLO PERFECTO:
```html
<!-- HTML -->
<section class="principles-grid">
    <article class="principle-item">
        <h3>Principio 1</h3>
        <p>Es innovador...</p>
    </article>
    <!-- 9 artículos más -->
</section>
```

```css
/* CSS */
.principles-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 30px;
    max-width: 1200px;
    margin: 0 auto;
}

.principle-item {
    padding: 30px;
    background-color: var(--grey-light);
    border: 1px solid var(--grey-mid);
}

/* Responsive */
@media (max-width: 768px) {
    .principles-grid {
        grid-template-columns: 1fr;  /* Una sola columna */
    }
}

@media (max-width: 480px) {
    .principle-item {
        padding: 20px;  /* Menos padding */
    }
}
```

#### PRODUCTOS GRID:
```css
.products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 40px;
    margin-bottom: 80px;
}

@media (max-width: 768px) {
    .products-grid {
        grid-template-columns: 1fr;
    }
}
```

#### FOOTER GRID:
```css
.footer-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 40px;
    max-width: 1200px;
    margin: 0 auto;
}

@media (max-width: 768px) {
    .footer-content {
        grid-template-columns: 1fr;
    }
}
```

#### GRID TRADICIONAL DE 12 COLUMNAS:
```css
.grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 30px;
}

.col-12 { grid-column: span 12; }
.col-6 { grid-column: span 6; }
.col-4 { grid-column: span 4; }
.col-3 { grid-column: span 3; }

@media (max-width: 768px) {
    .col-6 { grid-column: span 12; }  /* Full width */
    .col-4 { grid-column: span 12; }
}
```

### Propiedades de ITEMS:

```css
.grid-item {
    grid-column: span 2;         /* Ocupar 2 columnas */
    grid-row: span 1;            /* Ocupar 1 fila */
    grid-column: 1 / 3;          /* Del 1 al 3 */
}
```

### EN TU CÓDIGO - APLICAR EN:
```css
/* ✅ Al menos uno de estos debe tener grid */
.principles-grid { display: grid; }          /* RECOMENDADO */
.products-grid { display: grid; }            /* Opcional */
.footer-content { display: grid; }           /* Opcional */
```

---

## 4️⃣ RESPONSIVE DESIGN (Diseño Adaptable)

### ¿Qué es?
Hacer que tu sitio se vea bien en todos los tamaños de pantalla:
- Mobile: 320px - 480px
- Tablet: 481px - 768px
- Desktop: 769px+

### Media Queries:

```css
/* Mobile First (recomendado) */

/* Estilos base para mobile */
body {
    font-size: 15px;
    padding: 20px;
}

h1 {
    font-size: 1.5rem;
}

/* Tablet pequeño (480px+) */
@media (min-width: 480px) {
    body { font-size: 16px; }
    h1 { font-size: 1.8rem; }
}

/* Tablet grande (768px+) */
@media (min-width: 768px) {
    body { padding: 40px; }
    h1 { font-size: 2.2rem; }
}

/* Desktop (1024px+) */
@media (min-width: 1024px) {
    h1 { font-size: 3rem; }
}
```

### EN TU PROYECTO:

#### INDEX.HTML - HERO RESPONSIVO:
```css
/* Mobile */
.hero-slider {
    flex-direction: column;
    gap: 20px;
}

.hero-image {
    width: 200px;
    height: 200px;
}

/* Tablet (768px+) */
@media (min-width: 768px) {
    .hero-slider {
        flex-direction: row;
        gap: 40px;
    }

    .hero-image {
        width: 250px;
        height: 250px;
    }
}
```

#### ABOUT.HTML - TIMELINE RESPONSIVO (IMPORTANTE):
```css
/* Mobile - Timeline VERTICAL */
.timeline-horizontal {
    display: flex;
    flex-direction: column;
    gap: 40px;
    padding: 40px 20px;
}

.timeline-horizontal::before {
    display: none;  /* Quitar línea horizontal */
}

.timeline-item {
    width: 100%;
    min-width: auto;
}

.timeline-item::after {
    display: none;  /* Quitar punto */
}

.content {
    position: static !important;  /* No absolute */
    width: 100% !important;
    margin: 0 !important;
}

.year {
    position: static !important;
    background: none !important;
    padding: 0 !important;
    font-size: 1.2rem;
    margin-bottom: 20px;
}

/* Tablet (768px+) - Timeline HORIZONTAL */
@media (min-width: 768px) {
    .timeline-horizontal {
        flex-direction: row;
        gap: 140px;
        overflow-x: auto;
        padding: 200px 60px;
    }

    .timeline-horizontal::before {
        display: block;  /* Mostrar línea */
    }

    .timeline-item {
        min-width: 220px;
        flex-shrink: 0;
    }

    .timeline-item::after {
        display: block;  /* Mostrar punto */
    }

    .content {
        position: absolute !important;
    }

    .year {
        position: absolute !important;
        background: white !important;
        padding: 8px 16px !important;
    }
}
```

#### PRINCIPLES.HTML - GRID RESPONSIVO:
```css
/* Mobile - 1 columna */
.principles-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
    padding: 20px;
}

/* Tablet (768px+) - 2 columnas */
@media (min-width: 768px) {
    .principles-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 30px;
        padding: 40px;
    }
}

/* Desktop (1024px+) - 3 columnas */
@media (min-width: 1024px) {
    .principles-grid {
        grid-template-columns: repeat(3, 1fr);
        gap: 40px;
        padding: 60px 40px;
    }
}
```

#### HEADER RESPONSIVO:
```css
/* Mobile */
.header-content {
    flex-direction: column;
    padding: 20px;
    gap: 15px;
}

.logo {
    font-size: 0.9rem;
}

.nav-list {
    gap: 15px;
    font-size: 0.8rem;
}

/* Tablet (768px+) */
@media (min-width: 768px) {
    .header-content {
        flex-direction: row;
        padding: 30px 40px;
        gap: 40px;
    }

    .logo {
        font-size: 1.2rem;
    }

    .nav-list {
        gap: 40px;
        font-size: 0.9rem;
    }
}
```

### Breakpoints recomendados (Mobile-First):
```css
/* Mobile (default) - 320px+ */
/* Estilos base aquí */

/* Tablet pequeño - 480px+ */
@media (min-width: 480px) { }

/* Tablet grande - 768px+ */
@media (min-width: 768px) { }

/* Desktop - 1024px+ */
@media (min-width: 1024px) { }

/* Large Desktop - 1440px+ */
@media (min-width: 1440px) { }
```

### Checklist de Responsive:
- [ ] Texto legible sin zoom (mín 16px)
- [ ] Botones tocables (mín 44x44px)
- [ ] Sin scroll horizontal
- [ ] Imágenes escalan correctamente
- [ ] Espaciado proporcional en todos los tamaños
- [ ] Touch targets accesibles
- [ ] Navegación funciona en mobile
- [ ] Videos/iframes responsivos

---

## 5️⃣ BOOTSTRAP (Framework CSS)

### ¿Qué es?
Librería CSS pre-hecha para construcción rápida. En tu proyecto lo usarás mínimamente.

### Cómo incluir:
```html
<!-- En <head> -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- Tu CSS DESPUÉS -->
<link rel="stylesheet" href="css/style.css">
```

### Usar SOLO para:

#### Grid System:
```html
<div class="container">
    <div class="row">
        <div class="col-md-6">Columna 1</div>
        <div class="col-md-6">Columna 2</div>
    </div>
</div>
```

#### Spacing (Margin/Padding):
```css
.mt-5 { margin-top: 3rem; }
.mb-3 { margin-bottom: 1rem; }
.p-4 { padding: 1.5rem; }
```

#### Typography:
```html
<h1 class="h1">Título</h1>
<p class="lead">Párrafo destacado</p>
```

### ❌ NO HACER:
```css
/* ❌ NO sobrescribas todo con Bootstrap */
/* Mantén tu estilo minimalista */

/* ❌ Evita componentes Bootstrap */
/* .btn, .card, .navbar, etc. */

/* ✅ SI Bootstrap interfiere, especifica tu CSS */
.mi-clase {
    color: var(--black) !important;
    background: var(--white) !important;
}
```

---

## RESUMEN RÁPIDO

| Concepto | Uso | Ejemplo |
|----------|-----|---------|
| **Box Model** | Espacio interior/exterior | `padding: 20px; margin: 10px;` |
| **Flexbox** | Distribución en línea | `display: flex; gap: 20px;` |
| **Grid** | Distribución en cuadrícula | `display: grid; grid-template-columns: repeat(3, 1fr);` |
| **Media Query** | Estilos por tamaño | `@media (max-width: 768px) { }` |
| **Bootstrap** | Framework CSS | `<link href="...bootstrap.min.css">` |

---

## VERIFICACIÓN EN TU CÓDIGO

### ✅ BUSCAR EN style.css:

**Box Model:**
```bash
Buscar: "padding:", "margin:", "border:", "box-sizing"
Resultado: Debe aparecer muchas veces
```

**Flexbox:**
```bash
Buscar: "display: flex"
Resultado: En header, nav, hero, footer, social-links
```

**Grid:**
```bash
Buscar: "display: grid"
Resultado: En principles, products, footer
```

**Media Query:**
```bash
Buscar: "@media"
Resultado: Mínimo en 768px y 480px
```

**Bootstrap:**
```html
Buscar: "bootstrap"
En archivo: Debe estar en <head>
```

---

¡Todos estos conceptos DEBEN estar en tu código para la 2ª preentrega! 🎯
