# 🚀 GUÍA DE IMPLEMENTACIÓN RÁPIDA - 2ª PREENTREGA

## PASO 1: PREPARAR GITHUB (5 minutos)

### En GitHub:
1. Ir a github.com y crear nuevo repositorio
   - Nombre: `dieter-rams` (o tu preferencia)
   - Descripción: "Sitio sobre Dieter Rams - 10 principios del diseño"
   - Público
   - NO agregar README (lo haremos nosotros)

2. Copiar el HTTPS URL (botón verde Clone)
   - Ejemplo: `https://github.com/tuusuario/dieter-rams.git`

### En tu computadora (Terminal/CMD):
```bash
# Navega a donde tengas tu proyecto
cd tu/carpeta/proyecto

# Inicializar git
git init

# Agregar archivos
git add .

# Primer commit
git commit -m "Estructura inicial - 2ª preentrega"

# Cambiar a main branch
git branch -M main

# Agregar repositorio remoto
git remote add origin https://github.com/tuusuario/dieter-rams.git

# Subir a GitHub
git push -u origin main
```

### Habilitar GitHub Pages:
1. En tu repositorio → Settings → Pages
2. Source: Main branch / (root directory)
3. Guardar
4. Esperar 1-2 minutos
5. Tu sitio estará en: `https://tuusuario.github.io/dieter-rams`

---

## PASO 2: ORGANIZAR CARPETAS (10 minutos)

### Estructura que debe quedar:
```
dieter-rams/
│
├── index.html                 (en raíz)
│
├── css/
│   └── style.css
│
├── pages/
│   ├── about.html
│   ├── designs.html
│   ├── principles.html
│   └── product.html
│
└── img/
    └── [todas tus imágenes]
```

### Cómo hacer la restructura:
1. Crear carpeta `/css` → mover `style.css` allí
2. Crear carpeta `/pages` → mover los 4 HTMLs allí
3. Crear carpeta `/img` → mover imágenes allí

### Actualizar enlaces en HTML:

**En index.html:**
```html
<!-- Cambiar esto -->
<link rel="stylesheet" href="css/style.css" />

<!-- Ya debe estar así -->
<a href="pages/about.html">Sobre</a>
<a href="pages/designs.html">Diseños</a>
<a href="pages/principles.html">Principios</a>
<a href="pages/product.html">Productos</a>
```

**En todos los HTMLs de /pages/:**
```html
<!-- Cambiar rutas de vuelta -->
<link rel="stylesheet" href="../css/style.css" />
<a href="../index.html">Inicio</a>

<!-- Imágenes -->
<img src="../img/foto.jpg" alt="Descripción">
```

---

## PASO 3: REEMPLAZAR ARCHIVOS (15 minutos)

### Opción A: Copiar-pegar código

1. **index.html**: Reemplazar contenido con `index_mejorado.html`
2. **css/style.css**: Reemplazar contenido con `style_mejorado.css`
3. **pages/about.html**: Reemplazar contenido con `about_mejorado.html`

### Opción B: Copiar de los archivos proporcionados
- Abre `index_mejorado.html` → copia todo
- Abre tu `index.html` → pega todo → guarda
- Repite con otros archivos

---

## PASO 4: VALIDAR ESTRUCTURA HTML

### En cada archivo HTML, verificar que tenga:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <!-- Meta tags -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="...">
    
    <!-- Bootstrap (opcional pero recomendado) -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    
    <!-- Tu CSS -->
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- HEADER con estructura semántica -->
    <header role="banner">
        <div class="header-content">
            <h1 class="logo">RAMS</h1>
            <nav role="navigation" aria-label="Navegación principal">
                <ul class="nav-list">
                    <li><a href="..." class="nav-link">...</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- MAIN -->
    <main role="main">
        <section>
            <!-- Contenido con <article>, <h2>, <p> -->
        </section>
    </main>

    <!-- FOOTER -->
    <footer role="contentinfo">
        <address>...</address>
        <p>&copy; 2025</p>
    </footer>

    <!-- Bootstrap JS (opcional) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

---

## PASO 5: VERIFICAR RESPONSIVE

### Abrir DevTools (F12 o Ctrl+Shift+I):
1. Presionar Ctrl+Shift+M (toggle device mode)
2. Probar en:
   - ✅ iPhone (375px)
   - ✅ iPad (768px)
   - ✅ Desktop (1024px+)

### Qué debe verse bien en MOBILE (al menos 2 páginas):
- [ ] Header se adapta
- [ ] Navegación legible
- [ ] Hero section no se desborda
- [ ] Timeline es vertical
- [ ] Botones/links tocables (44x44px mínimo)
- [ ] Texto legible (16px mínimo)
- [ ] Sin scroll horizontal

---

## PASO 6: AGREGAR BOOTSTRAP (5 minutos)

### En el `<head>` de CADA HTML:
```html
<!-- Después de charset y viewport -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- Tu CSS (DESPUÉS de Bootstrap) -->
<link rel="stylesheet" href="css/style.css">
```

### Al final del `<body>`:
```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```

### Usar Bootstrap MÍNIMAMENTE:
```html
<!-- BUENO: Usar solo para grid y utilidades -->
<div class="container">
    <div class="row">
        <div class="col-md-6">Columna 1</div>
        <div class="col-md-6">Columna 2</div>
    </div>
</div>

<!-- NO HAGAS: Sobrescribir todo tu diseño -->
<!-- Evita usar componentes como .btn, .card, etc. -->
```

---

## PASO 7: APLICAR CSS GRID (20 minutos)

### Ejemplo en principles.html:

**HTML:**
```html
<section class="principles-grid">
    <article class="principle-card">
        <h3>Principio 1</h3>
        <p>Descripción...</p>
    </article>
    <!-- Repetir para 10 principios -->
</section>
```

**CSS:**
```css
.principles-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
    margin-bottom: 80px;
}

.principle-card {
    padding: 30px;
    background-color: var(--grey-light);
    border: 1px solid var(--grey-mid);
}

@media (max-width: 768px) {
    .principles-grid {
        grid-template-columns: 1fr;
    }
}
```

---

## PASO 8: MEJORAR RESPONSIVO

### Puntos clave en 768px:

**Header:**
```css
@media (max-width: 768px) {
    .header-content {
        flex-direction: column;
        gap: 20px;
        padding: 20px;
    }

    .nav-list {
        gap: 15px;
        flex-wrap: wrap;
        justify-content: center;
    }

    .nav-link {
        font-size: 0.85rem;
    }
}
```

**Timeline - CONVERTIR A VERTICAL:**
```css
@media (max-width: 768px) {
    .timeline-horizontal {
        display: flex;
        flex-direction: column;
        gap: 40px;
        padding: 40px 20px;
        overflow-x: hidden;
    }

    .timeline-horizontal::before {
        display: none;
    }

    .timeline-item {
        width: 100%;
        min-width: auto;
    }

    .timeline-item::after {
        display: none;
    }

    .content {
        position: static !important;
        width: 100% !important;
        margin: 0 !important;
        margin-bottom: 20px !important;
    }

    .year {
        position: static !important;
        background: none !important;
        padding: 0 !important;
        margin-bottom: 20px;
        font-size: 1.2rem;
        font-weight: 600;
    }
}
```

### En 480px - AÚN MÁS PEQUEÑO:
```css
@media (max-width: 480px) {
    h1 { font-size: 1.5rem; }
    h2 { font-size: 1.1rem; }
    p { font-size: 0.95rem; }
    
    main {
        padding: 20px 15px;
    }

    .nav-link {
        font-size: 0.75rem;
    }
}
```

---

## PASO 9: BOX MODEL Y FLEXBOX

### Verificar que esté aplicado:

**Box Model visible:**
```css
.element {
    padding: 20px;        /* Espacio interno */
    margin: 20px;         /* Espacio externo */
    border: 1px solid;    /* Borde */
    box-sizing: border-box; /* Importante */
}
```

**Flexbox en Header:**
```css
.header-content {
    display: flex;
    justify-content: space-between;  /* Separar elementos */
    align-items: center;              /* Alinear verticalmente */
    gap: 30px;                        /* Espacio entre items */
    flex-wrap: wrap;                  /* Wrappear en mobile */
}
```

**Flexbox en Nav:**
```css
.nav-list {
    display: flex;
    gap: 30px;
    flex-wrap: wrap;
    justify-content: center;
}
```

---

## PASO 10: ÚLTIMOS AJUSTES

### Accesibilidad:
```html
<!-- En botones -->
<button aria-label="Diapositiva anterior">‹</button>

<!-- En links -->
<a href="..." aria-current="page">Activo</a>

<!-- En secciones -->
<section aria-label="Descripción clara">
```

### Performance:
- [ ] Imágenes optimizadas (max 2MB cada una)
- [ ] CSS minificado (opcional)
- [ ] Sin console errors

### Testing:
- [ ] Probar en Chrome, Firefox, Safari
- [ ] Verificar responsive en DevTools
- [ ] Validar HTML: https://validator.w3.org/
- [ ] Validar CSS: https://jigsaw.w3.org/css-validator/

---

## PASO 11: COMMIT Y PUSH A GITHUB

```bash
# En terminal, en la carpeta del proyecto
cd tu/carpeta/dieter-rams

# Ver cambios
git status

# Agregar todos los cambios
git add .

# Commit con mensaje descriptivo
git commit -m "2ª preentrega: responsive, Bootstrap, Grid, semántica"

# Subir a GitHub
git push origin main

# Verificar en GitHub
# Ir a https://github.com/tuusuario/dieter-rams
```

---

## PASO 12: ACTIVAR GITHUB PAGES

1. En tu repo → **Settings** → **Pages**
2. Source: **Main branch** / **(root)**
3. Esperar 1-2 minutos
4. Tu sitio estará en: `https://tuusuario.github.io/dieter-rams/`

**Verificar:**
- [ ] Sitio accesible
- [ ] Links funcionan
- [ ] CSS carga correctamente
- [ ] Responsive funciona

---

## CHECKLIST FINAL ANTES DE ENTREGAR

### Requisitos Técnicos ✅
- [ ] 5 HTML (index + 4 en /pages/)
- [ ] Carpeta /css con style.css
- [ ] Carpeta /img con imágenes
- [ ] Estructura semántica correcta
- [ ] Bootstrap CDN incluido
- [ ] CSS Grid aplicado
- [ ] Flexbox aplicado
- [ ] Box Model visible
- [ ] Responsive en al menos 2 páginas

### Responsive (768px + 480px) ✅
- [ ] Header adapta
- [ ] Navegación accesible
- [ ] Timeline es vertical (about.html)
- [ ] Principios en grid responsivo (principles.html)
- [ ] Sin scroll horizontal
- [ ] Botones tocables (44x44px min)
- [ ] Texto legible (16px min)

### GitHub ✅
- [ ] Repositorio público
- [ ] URL correcta
- [ ] GitHub Pages activo
- [ ] Link compartible (https://tuusuario.github.io/dieter-rams/)

### Código ✅
- [ ] Sin errores en consola
- [ ] HTML válido
- [ ] CSS bien estructurado
- [ ] Comentarios claros
- [ ] Nombres de clases semánticos

### UX/UI ✅
- [ ] Diseño minimalista coherente
- [ ] Colores consistentes
- [ ] Tipografía legible
- [ ] Espaciado proporcional
- [ ] Hover states claros
- [ ] Focus states accesibles
- [ ] Transiciones suaves

---

## 🎯 TIMELINE SUGERIDO PARA COMPLETAR TODO

| Día | Tiempo | Tarea |
|-----|--------|-------|
| Día 1 | 0.5h | Paso 1: GitHub setup |
| Día 1 | 0.5h | Paso 2: Organizar carpetas |
| Día 2 | 1h | Paso 3-4: Reemplazar archivos y validar |
| Día 3 | 1h | Paso 5: Verificar responsive |
| Día 4 | 0.5h | Paso 6: Bootstrap |
| Día 5 | 1h | Paso 7-8: Grid + Responsive |
| Día 6 | 0.5h | Paso 9-10: Ajustes finales |
| Día 7 | 0.5h | Paso 11-12: Push a GitHub + Pages |

**Total: ~5-6 horas**

---

## ⚠️ ERRORES COMUNES A EVITAR

### ❌ Rutas de archivo
```html
<!-- ❌ MAL -->
<link rel="stylesheet" href="style.css">
<link rel="stylesheet" href="/css/style.css">

<!-- ✅ BIEN -->
<link rel="stylesheet" href="css/style.css">  <!-- en index.html -->
<link rel="stylesheet" href="../css/style.css">  <!-- en pages/about.html -->
```

### ❌ Bootstrap sobrescribiendo
```css
/* ❌ No dejes que Bootstrap sobrescriba tus estilos */
/* ✅ Si Bootstrap interfiere, especifica más tu CSS */

/* O usa !important (último recurso) */
.mi-clase {
    color: var(--black) !important;
}
```

### ❌ Responsive no funciona
```html
<!-- ❌ FALTA viewport -->
<!-- ✅ BIEN -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### ❌ GitHub Pages no funciona
```
❌ Olvidar habilitar en Settings > Pages
❌ No tener index.html en raíz
❌ Carpeta /pages/ debe tener archivos relativos a ../
```

---

## 📞 REFERENCIAS RÁPIDAS

### Links útiles:
- **Bootstrap 5**: https://getbootstrap.com/docs/5.3/
- **CSS Grid**: https://www.cssgridgarden.com/
- **Responsive Design**: https://developer.mozilla.org/es/docs/Web/CSS/Media_Queries
- **GitHub Pages**: https://pages.github.com/
- **Validador HTML**: https://validator.w3.org/
- **Validador CSS**: https://jigsaw.w3.org/css-validator/

### Media Query Breakpoints (recomendados):
```css
/* Mobile First */
/* Estilos base para mobile */

/* Tablet pequeño */
@media (min-width: 480px) { }

/* Tablet grande */
@media (min-width: 768px) { }

/* Desktop */
@media (min-width: 1024px) { }
```

---

## ✨ CONSEJOS PARA ÓPTIMO CALIFICACIÓN

1. **Semántica HTML**: Usa `<section>`, `<article>`, `<header>`, `<footer>`, `<nav>` correctamente
2. **Responsive Real**: Prueba en DevTools con pantallas reales (no solo redimensionar)
3. **Grid y Flexbox Visible**: Asegúrate que estén realmente aplicados (no solo en CSS)
4. **Bootstrap Sutil**: Úsalo para estructura, no para estilos
5. **UX/UI Polish**: Detalles como hover states, transiciones, espaciado consistente
6. **Accesibilidad**: `aria-labels`, `role`, focus states
7. **Code Quality**: Código limpio, comentado, bien estructurado
8. **Testing Real**: Prueba en navegadores diferentes y dispositivos reales

---

¡Espero que esta guía te ayude a completar la 2ª preentrega de forma exitosa! 🚀
