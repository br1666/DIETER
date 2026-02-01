# 📋 PLAN ESTRATÉGICO - 2ª PREENTREGA | Dieter Rams Website

---

## ✅ CHECKLIST DE REQUISITOS

### Estructura de Carpetas (OBLIGATORIO)
```
dieter-rams-project/
├── index.html
├── css/
│   └── style.css
├── pages/
│   ├── about.html
│   ├── designs.html
│   ├── principles.html
│   └── product.html
└── img/
    └── [todas tus imágenes]
```

### Requisitos Técnicos
- ✅ **5 HTML**: index.html + 4 en carpeta pages/
- ✅ **Responsive en al menos 2 páginas**: desktop + mobile (320px, 768px, 1024px)
- ✅ **Media Queries**: @media (max-width: 768px) y @media (max-width: 480px)
- ✅ **Bootstrap**: Incluir y usar en al menos una página
- ✅ **Flexbox**: Ya aplicado, mantener y mejorar
- ✅ **Grid CSS**: Aplicar en al menos una sección (propias grillas)
- ✅ **Box Model**: Margin, padding, border visibles
- ✅ **Estructura semántica**: header, nav, main, section, article, footer
- ✅ **GitHub**: Repositorio público con GitHub Pages activo

---

## 🎯 ESTADO ACTUAL vs OBJETIVOS

### LO QUE TIENES BIEN ✅
1. **Estructura HTML base**: Todos los archivos existen
2. **Diseño minimalista**: Coherente con Dieter Rams
3. **CSS organizado**: Variables, comentarios, estructura clara
4. **Media queries**: Ya hay responsive (768px, 480px)
5. **Flexbox**: Usado en nav, footer, timeline-wrapper
6. **Timeline**: Componente complejo y bien hecho

### LO QUE NECESITA MEJORA 🔧

#### 1. ESTRUCTURA DE CARPETAS
**Situación actual**: Todos los archivos en la raíz
**Acción**: Crear estructura correcta (ver arriba)

#### 2. HTML SEMÁNTICO
**Problemas actuales**:
- index.html: El header no usa `<div class="header-content">` como el CSS espera
- Falta estructura semántica en algunas secciones
- Social links no tiene estructura clara

**Mejoras necesarias**:
```html
<!-- ❌ ACTUAL -->
<header>
  <h1>RAMS</h1>
  <nav>...</nav>
</header>

<!-- ✅ DEBE SER -->
<header>
  <div class="header-content">
    <h1>RAMS</h1>
    <nav>...</nav>
  </div>
</header>
```

#### 3. RESPONSIVE MEJORADO
**Páginas para hacer responsive (al menos 2)**:
1. **index.html** - Hero slider + social links
2. **about.html** - Timeline horizontal
3. **principles.html** - Lista de principios (opcional, mejor)

**Puntos clave**:
- Header colapsable en mobile (hamburguesa)
- Timeline horizontal → vertical en mobile
- Grid de productos → stack en mobile
- Social links → mejorar spacing

#### 4. BOOTSTRAP (RECOMENDADO)
**Usar solo para**:
- Grid system (responsive columns)
- Helpers de spacing/typography
- Media query breakpoints
- **NO**: Overwrite todo el diseño (mantener tu estética minimalista)

#### 5. CSS GRID PROPIO
**Dónde aplicar**:
- Sección de principios (10 items en grid)
- Sección de productos (galería)
- Footer multi-columna

**Ejemplo**:
```css
.principles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 40px;
}
```

#### 6. BOX MODEL VISIBLE
**Asegurar**:
- Padding interno consistente
- Margin externo bien distribuido
- Borders strategically placed
- Alturas y anchos controladas

---

## 🚀 PASOS DE ACCIÓN (ORDEN RECOMENDADO)

### PASO 1: Preparar Repositorio (1 hora)
```bash
# En tu máquina local
git init
git add .
git commit -m "Estructura inicial - 2ª preentrega"
git branch -M main
git remote add origin https://github.com/tuusuario/dieter-rams.git
git push -u origin main
```

**Luego habilitar GitHub Pages**:
- Ir a Settings → Pages
- Source: main branch / root directory
- Tu sitio estará en: https://tuusuario.github.io/dieter-rams

### PASO 2: Reorganizar Carpetas (30 min)
1. Crear carpeta `/css` → mover style.css
2. Crear carpeta `/img` → mover imágenes
3. Crear carpeta `/pages` → mover about.html, designs.html, principles.html, product.html
4. Actualizar rutas en HTML:
   - `href="css/style.css"`
   - `href="pages/about.html"`
   - `src="img/producto.jpg"`

### PASO 3: Mejorar HTML Semántico (1.5 horas)
**En TODOS los archivos**:
- [ ] Verificar header con `.header-content`
- [ ] Asegurar nav dentro de header
- [ ] Usar `<main>` correctamente
- [ ] Usar `<section>` para agrupaciones
- [ ] Usar `<article>` para contenido independiente
- [ ] Usar `<footer>` semánticamente
- [ ] Agregar `<address>` en footer

### PASO 4: Aplicar Bootstrap (1 hora)
```html
<!-- En el <head> de cada HTML -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
```

**Usar solo para**:
- Grid: `<div class="container"><div class="row"><div class="col-md-6"></div></div></div>`
- Spacing: `.mt-5`, `.mb-3` (si lo necesitas)
- Typography: `.h1`, `.lead` (opcional)

**Importante**: NO sobrescribe todo tu CSS. Mantén tu estilo minimalista.

### PASO 5: Mejorar Responsive (2-3 horas)

#### 5.1 Index.html - Hero + Social
```css
/* Mobile first approach */
@media (max-width: 768px) {
  header { padding: 20px; }
  .hero-slider { flex-direction: column; }
  .slider-btn { width: 40px; height: 40px; }
  .social-links nav ul { gap: 15px; }
}
```

#### 5.2 About.html - Timeline Responsive
```css
@media (max-width: 768px) {
  .timeline-horizontal {
    display: flex;
    flex-direction: column;
    gap: 40px;
    padding: 40px 20px;
  }
  
  .timeline-item::after { display: none; }
  .timeline-horizontal::before { display: none; }
  
  .content { width: 100%; position: static; }
  .content.top, .content.bottom { margin: 0; }
  
  .year { position: static; background: none; padding: 0; }
}
```

#### 5.3 Principles.html - Grid Responsivo
```css
.principles-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 40px;
}

@media (max-width: 768px) {
  .principles-list { grid-template-columns: 1fr; }
  .principle-number { font-size: 2rem; }
}
```

### PASO 6: CSS Grid Propio (1.5 horas)
**En principles.html o product.html**:
```css
/* Ejemplo: Grid de principios */
.principles-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .principles-container {
    grid-template-columns: 1fr;
  }
}
```

### PASO 7: UX/UI Polish (1.5 horas)
1. **Colores**:
   - Mantener minimalismo (blanco, negro, grises)
   - Alto contraste para accesibilidad
   
2. **Tipografía**:
   - Tamaños claros en mobile (mínimo 16px)
   - Line-height adecuado (1.6 mínimo)
   
3. **Espaciado**:
   - Padding/margin consistente (8px, 16px, 24px, 40px)
   - Responsive: reducir en mobile
   
4. **Interactividad**:
   - Hover states claros
   - Focus states accesibles
   - Transiciones suaves
   
5. **Mobile**:
   - Touch targets mínimo 44x44px
   - Buttons y links tappable
   - Sin horizontal scroll

### PASO 8: Optimizaciones Finales (1 hora)
- [ ] Verificar enlaces internos funcionan
- [ ] Probar responsive en DevTools (320px, 768px, 1024px)
- [ ] Verificar que Bootstrap no sobrescribe tu CSS
- [ ] Que GitHub Pages esté activo
- [ ] Tests en navegadores (Chrome, Firefox, Safari, Edge)

---

## 📊 DISTRIBUCIÓN DE RESPONSIVE

**Mínimo 2 páginas, recomendadas 3+**:

| Página | Desktop | Mobile | Técnica |
|--------|---------|--------|---------|
| index.html | ✅ | ✅ | Media queries + Flexbox |
| about.html | ✅ | ✅ | Media queries + Timeline vertical |
| principles.html | ✅ | ✅ | CSS Grid responsive |
| designs.html | ✅ | - | Bootstrap grid (opcional) |
| product.html | ✅ | - | Contenido de relleno |

---

## 🎨 APLICACIÓN DE CONCEPTOS

### Box Model (ya hecho, validar)
```css
/* Elemento con Box Model visible */
.principle-item {
  padding: 60px 0;        /* Espacio interno */
  margin: 0;              /* Sin margen externo */
  border-bottom: 1px solid var(--grey-mid);  /* Borde inferior */
  box-sizing: border-box; /* Incluir border en ancho total */
}
```

### Flexbox (ya hecho, mejorar)
```css
/* Header con flexbox */
.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 40px;
}

/* Nav con flexbox */
nav ul {
  list-style: none;
  display: flex;
  gap: 40px;
  flex-wrap: wrap;  /* Agregar para responsive */
}
```

### CSS Grid (AGREGAR)
```css
/* Nuevo: Grid para principios */
.principles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
}

/* Nuevo: Grid para footer */
.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 40px;
}
```

### Media Queries (mejorar)
```css
/* Breakpoints recomendados */
@media (max-width: 1024px) { /* Tablets grandes */ }
@media (max-width: 768px)  { /* Tablets pequeños */ }
@media (max-width: 480px)  { /* Móviles */ }
```

---

## 📝 ARCHIVO HTML MEJORADO - EJEMPLO (index.html)

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Dieter Rams | Inicio</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="css/style.css" />
</head>
<body>
    <header role="banner">
        <div class="header-content">
            <h1>RAMS</h1>
            <nav role="navigation" aria-label="Principal">
                <ul>
                    <li><a href="index.html" class="active">Inicio</a></li>
                    <li><a href="pages/about.html">Sobre</a></li>
                    <li><a href="pages/designs.html">Diseños</a></li>
                    <li><a href="pages/principles.html">Principios</a></li>
                    <li><a href="pages/product.html">Productos</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main role="main">
        <!-- Hero Section con Slider -->
        <section class="hero-slider" aria-label="Presentación de Dieter Rams">
            <button class="slider-btn prev" aria-label="Diapositiva anterior">›</button>
            <div class="slider-content">
                <div class="hero-image-placeholder"></div>
                <h2>Dieter Rams</h2>
                <p>Pionero del diseño funcional y creador de los 10 principios del buen diseño.</p>
            </div>
            <button class="slider-btn next" aria-label="Diapositiva siguiente">›</button>
        </section>

        <!-- Redes Sociales -->
        <section class="social-section" aria-label="Redes Sociales">
            <nav aria-label="Redes sociales">
                <ul class="social-links">
                    <li><a href="https://facebook.com/dieter.rams" target="_blank" rel="noopener noreferrer" title="Facebook">F</a></li>
                    <li><a href="https://tiktok.com/@dieter" target="_blank" rel="noopener noreferrer" title="TikTok">T</a></li>
                    <li><a href="https://www.instagram.com/dieter.rams" target="_blank" rel="noopener noreferrer" title="Instagram">I</a></li>
                    <li><a href="mailto:info@dieter-rams.com" title="Email">Mail</a></li>
                    <li><a href="https://www.x.com/dieter" target="_blank" rel="noopener noreferrer" title="X">X</a></li>
                    <li><a href="https://www.linkedin.com/in/dieter-rams" target="_blank" rel="noopener noreferrer" title="LinkedIn">L</a></li>
                    <li><a href="https://www.youtube.com/@dieter" target="_blank" rel="noopener noreferrer" title="YouTube">Y</a></li>
                    <li><a href="https://www.pinterest.com/dieter.rams" target="_blank" rel="noopener noreferrer" title="Pinterest">P</a></li>
                </ul>
            </nav>
        </section>
    </main>

    <footer role="contentinfo">
        <address>Lago Puelo, Chubut, Argentina</address>
        <p>&copy; 2025 Dieter Rams. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
```

---

## 🔗 LINKS DE REFERENCIA

### GitHub Pages Setup
- Guía oficial: https://pages.github.com/
- Validar: Ir a Settings > Pages y ver el URL generado

### Bootstrap
- CDN Link: https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css
- Documentación: https://getbootstrap.com/docs/5.3/

### CSS Grid
- MDN Guide: https://developer.mozilla.org/es/docs/Web/CSS/CSS_Grid_Layout
- Ejemplos: https://www.cssgridgarden.com/

### Responsive Design
- Mobile-first approach: https://developer.mozilla.org/es/docs/Mobile
- Breakpoints: 320px, 480px, 768px, 1024px, 1440px

---

## ✨ TIPS PARA ÓPTIMO CALIFICACIÓN

### Óptimo ⭐⭐⭐
- [ ] 3+ páginas con responsive activo
- [ ] Bootstrap integrado SIN sobrescribir diseño
- [ ] CSS Grid aplicado de forma clara
- [ ] Flexbox y Box Model bien utilizados
- [ ] HTML semántico en todos los archivos
- [ ] UX/UI pulido (espaciado, colores, tipografía)
- [ ] GitHub Pages funcionando perfectamente
- [ ] Código limpio y bien comentado

### Correcto ⭐⭐
- [ ] 2 páginas con responsive
- [ ] Bootstrap presente (aunque sea básico)
- [ ] CSS Grid en al menos una sección
- [ ] Media queries funcionando
- [ ] HTML semántico básico
- [ ] GitHub Pages activo

### Bajo ⭐
- [ ] Falta estructura de carpetas
- [ ] Poco o nada de responsive
- [ ] No usa Bootstrap
- [ ] HTML no semántico
- [ ] GitHub Pages no funciona

---

## 📅 CRONOGRAMA SUGERIDO

| Día | Tarea | Duración |
|-----|-------|----------|
| Día 1 | Pasos 1-2: Repo + Carpetas | 1.5h |
| Día 2-3 | Paso 3: HTML Semántico | 3h |
| Día 4 | Paso 4: Bootstrap | 1h |
| Día 5-6 | Paso 5: Responsive | 3h |
| Día 7 | Pasos 6-8: Grid + Polish | 2h |
| Día 8+ | Testing + Refinamiento | 2h |

**Total: ~12-15 horas de trabajo**

---

## 🎯 RESUMEN FINAL

Tu proyecto tiene una **excelente base**. Solo necesitas:

1. ✅ Reorganizar en carpetas
2. ✅ Mejorar HTML semántico (pequeños ajustes)
3. ✅ Integrar Bootstrap (sutilmente)
4. ✅ Expandir responsive a 2-3 páginas
5. ✅ Aplicar CSS Grid en al menos una sección
6. ✅ Pulir UX/UI (espaciado, móvil)
7. ✅ Activar GitHub Pages
8. ✅ Entregar antes del 02/02 22:30

**¡Vamos a hacerlo! 🚀**
