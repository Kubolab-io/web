# Sistema de Diseño - Kubo Lab

Este documento contiene todos los componentes, estilos y variables CSS necesarios para replicar el diseño de este sitio web en otro proyecto.

---

## 📋 Tabla de Contenidos

1. [Variables CSS (Design Tokens)](#variables-css-design-tokens)
2. [Tipografía](#tipografía)
3. [Componentes de Botones](#componentes-de-botones)
4. [Componentes de Secciones](#componentes-de-secciones)
5. [Componentes de Formularios](#componentes-de-formularios)
6. [Componentes de Tarjetas (Case Studies)](#componentes-de-tarjetas-case-studies)
7. [Espaciado y Utilidades](#espaciado-y-utilidades)
8. [Breakpoints Responsive](#breakpoints-responsive)
9. [Animaciones y Transiciones](#animaciones-y-transiciones)

---

## 🎨 Variables CSS (Design Tokens)

### Colores Principales

```css
:root {
  /* Colores Base */
  --primary: #072032;        /* Color principal oscuro (títulos, textos importantes) */
  --secondary: #5C6972;      /* Color secundario (textos descriptivos) */
  --border: #EBEDEF;          /* Color de bordes */
  --theme: #FF845D;           /* Color de acento/tema (botones, enlaces hover) */
  
  /* Colores Adicionales */
  --black: #072032;           /* Negro principal */
  --black-2: #5C6972;        /* Negro secundario */
  --white: #fff;              /* Blanco */
  --white-2: #9BA0A3;        /* Gris claro */
  --action: #FFCD4D;          /* Color de acción (amarillo) */
}
```

### Fuentes

```css
:root {
  --font_primary: "DM Sans", sans-serif;
  --font_secondary: "DM Sans", sans-serif;
  --font_geist: "geist", sans-serif;
  --font_awesome: "Font Awesome 6 Free";
}
```

### Configuración de Fuente Geist (Custom)

Para usar la fuente Geist personalizada, necesitas:

1. **Archivos de fuente**: Coloca los archivos en `assets/fonts/Geist/static/`
   - `Geist-Regular.ttf`
   - `Geist-SemiBold.ttf`

2. **Declaración @font-face**:

```css
@font-face {
  font-family: "geist";
  src: url("../fonts/Geist/static/Geist-Regular.ttf") format("truetype");
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: "geist";
  src: url("../fonts/Geist/static/Geist-SemiBold.ttf") format("truetype");
  font-weight: 600;
  font-style: normal;
}

:root {
  --font_geist: "geist", sans-serif;
}
```

3. **Aplicar a títulos**:

```css
.font-heading-geist-semibold h1,
.font-heading-geist-semibold h2,
.font-heading-geist-semibold h3,
.font-heading-geist-semibold h4,
.font-heading-geist-semibold h5,
.font-heading-geist-semibold h6 {
  font-family: var(--font_geist);
  font-weight: 600;
  line-height: 1.2;
}

body {
  font-family: var(--font_geist);
}
```

---

## 📝 Tipografía

### Tamaños de Encabezados

```css
h1 {
  font-size: 48px;
  color: var(--primary);
  font-weight: 600; /* SemiBold para Geist */
}

h2 {
  font-size: 36px;
  color: var(--primary);
  font-weight: 600;
}

h3 {
  font-size: 32px;
  color: var(--primary);
  font-weight: 600;
}

h4 {
  font-size: 24px;
  color: var(--primary);
  font-weight: 600;
}

h5 {
  font-size: 20px;
  color: var(--primary);
  font-weight: 600;
}

h6 {
  font-size: 18px;
  color: var(--primary);
  font-weight: 600;
}
```

### Texto Base

```css
p {
  font-size: 18px;
  line-height: 1.44;
  font-weight: 400;
  color: var(--secondary);
  font-family: var(--font_geist);
}

strong {
  font-weight: 500;
}

.medium {
  font-weight: 600;
}

.bold {
  font-weight: 700;
}
```

### Clases de Título de Sección

```css
.section-title {
  font-size: 48px; /* Ajustable según contexto */
  font-weight: 600;
  color: var(--primary);
  line-height: 1.2;
  margin-bottom: 20px;
}

.text {
  font-size: 18px;
  line-height: 1.7;
  color: var(--secondary);
}
```

---

## 🔘 Componentes de Botones

### Botón Primario (Principal)

```css
.wc-btn {
  display: inline-block;
}

.wc-btn-primary {
  padding: 21px 30px;
  font-weight: 700;
  font-size: 16px;
  line-height: 1;
  color: var(--white);
  background-color: var(--primary);
  border: 1px solid var(--primary);
  border-radius: 15px;
  text-transform: capitalize;
  transition: all 0.3s;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  z-index: 1;
  gap: 30px;
  white-space: nowrap;
}

.wc-btn-primary:hover {
  color: var(--white);
  background-color: var(--primary);
  border-color: var(--primary);
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(7, 32, 50, 0.2);
}

/* Variante con borde */
.wc-btn-primary.bordered {
  border-color: var(--secondary);
  background-color: transparent;
  color: var(--primary);
}

.wc-btn-primary.bordered:hover {
  border-color: var(--primary);
  background-color: var(--primary);
  color: var(--white);
}

/* Responsive */
@media only screen and (max-width: 991px) {
  .wc-btn-primary {
    padding: 16px 25px;
  }
}
```

### Botón de Envío de Formulario (Gradiente)

```css
.project-intake-submit {
  width: min(100%, 380px);
  border: none;
  border-radius: 999px;
  background-image: linear-gradient(135deg, #ff7b7b 0%, #ff4848 100%);
  color: #ffffff;
  font-size: 18px;
  font-weight: 600;
  padding: 20px 40px;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project-intake-submit:hover {
  transform: translateY(-2px);
  box-shadow: 0 18px 35px rgba(255, 100, 100, 0.35);
}

@media only screen and (max-width: 575px) {
  .project-intake-submit {
    width: 100%;
  }
}
```

### Botón con Borde

```css
.wc-btn-border {
  gap: 10px;
  display: inline-flex;
  align-items: center;
  color: var(--white);
  font-size: 16px;
  font-weight: 500;
  line-height: 1.5;
  padding: 16px 30px;
  border: 1px solid var(--white);
  overflow: hidden;
  transition: all 0.3s;
  z-index: 1;
  position: relative;
}

.wc-btn-border:hover {
  color: var(--white);
}
```

---

## 📦 Componentes de Secciones

### Contenedor de Sección

```css
.section-spacing {
  padding-top: 120px;
  padding-bottom: 120px;
}

@media only screen and (max-width: 991px) {
  .section-spacing {
    padding-top: 80px;
    padding-bottom: 80px;
  }
}

@media only screen and (max-width: 767px) {
  .section-spacing {
    padding-top: 60px;
    padding-bottom: 60px;
  }
}
```

### Header de Sección

```css
.section-header {
  text-align: center; /* o left según diseño */
  margin-bottom: 60px;
}

.section-header .section-title {
  font-size: 42px; /* Ajustable */
  font-weight: 600;
  color: var(--primary);
  margin-bottom: 20px;
}

.section-header .text {
  font-size: 18px;
  line-height: 1.7;
  color: var(--secondary);
  margin-top: 16px;
}

.section-title-wrapper {
  margin-bottom: 20px;
}

.title-wrapper {
  display: inline-block;
}
```

### Contenedor Principal

```css
.container {
  max-width: 1320px;
  margin: 0 auto;
  padding: 0 15px;
}

@media only screen and (max-width: 1399px) {
  .container {
    max-width: 1140px;
  }
}

@media only screen and (max-width: 1199px) {
  .container {
    max-width: 960px;
  }
}

@media only screen and (max-width: 991px) {
  .container {
    max-width: 720px;
  }
}

@media only screen and (max-width: 767px) {
  .container {
    max-width: 540px;
  }
}
```

---

## 📋 Componentes de Formularios

### Formulario de Project Intake

```css
.project-intake-area {
  background-color: #f5f7fb;
}

.project-intake-inner {
  max-width: 900px;
  margin: 0 auto;
  background-color: #ffffff;
  border-radius: 28px;
  padding: 70px 60px;
  box-shadow: 0 24px 60px rgba(7, 32, 50, 0.08);
}

.project-intake-form {
  margin-top: 48px;
  display: flex;
  flex-direction: column;
  gap: 32px;
}

/* Grid de 2 columnas */
.project-intake-form .form-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 24px;
}

/* Campo de entrada */
.project-intake-form .input-field {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.project-intake-form label {
  font-weight: 600;
  color: var(--primary);
  font-size: 16px;
}

.project-intake-form input,
.project-intake-form select,
.project-intake-form textarea {
  width: 100%;
  border: 1px solid #d9dfe6;
  border-radius: 14px;
  background-color: #f9fbfd;
  padding: 16px 18px;
  font-size: 16px;
  color: var(--primary);
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  font-family: var(--font_geist);
}

.project-intake-form textarea {
  min-height: 140px;
  resize: vertical;
}

.project-intake-form input:focus,
.project-intake-form select:focus,
.project-intake-form textarea:focus {
  outline: none;
  border-color: var(--theme);
  box-shadow: 0 0 0 4px rgba(255, 132, 93, 0.15);
}

/* Opciones de presupuesto (Radio buttons estilizados) */
.budget-options {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.budget-label {
  font-weight: 600;
  color: var(--primary);
  font-size: 16px;
}

.budget-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

.budget-option {
  position: relative;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.budget-option input {
  position: absolute;
  opacity: 0;
  pointer-events: none;
}

.budget-option span {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 20px;
  border-radius: 999px;
  border: 1px solid #d9dfe6;
  background-color: #ffffff;
  font-weight: 600;
  font-size: 15px;
  color: var(--primary);
  transition: all 0.3s ease;
  cursor: pointer;
}

.budget-option input:checked + span,
.budget-option:hover span {
  border-color: var(--theme);
  background-color: var(--theme);
  color: #ffffff;
  box-shadow: 0 10px 25px rgba(255, 132, 93, 0.35);
}

/* Wrapper de envío */
.submit-wrapper {
  display: flex;
  flex-direction: column;
  gap: 12px;
  align-items: center;
}

.disclaimer {
  font-size: 14px;
  color: var(--secondary);
  text-align: center;
}

/* Responsive */
@media only screen and (max-width: 991px) {
  .project-intake-inner {
    padding: 50px 36px;
  }

  .project-intake-inner .section-header .section-title {
    font-size: 36px;
  }

  .project-intake-form .form-grid {
    grid-template-columns: 1fr;
  }
}

@media only screen and (max-width: 575px) {
  .project-intake-inner {
    padding: 40px 24px;
    border-radius: 22px;
  }

  .project-intake-inner .section-header .section-title {
    font-size: 30px;
  }

  .project-intake-submit {
    width: 100%;
  }
}
```

### Estructura HTML del Formulario

```html
<section id="project-intake" class="project-intake-area section-spacing">
  <div class="container">
    <div class="project-intake-inner">
      <div class="section-header text-center">
        <div class="section-title-wrapper">
          <div class="title-wrapper">
            <h2 class="section-title">¿Pensando en construir una app?</h2>
          </div>
        </div>
        <div class="text-wrapper">
          <p class="text">Cuéntanos sobre tu proyecto y te responderemos en menos de 24 horas.</p>
        </div>
      </div>
      
      <form class="project-intake-form" action="https://formspree.io/f/YOUR_FORM_ID" method="post">
        <div class="form-grid">
          <div class="input-field">
            <label for="project-name">Tu nombre *</label>
            <input type="text" id="project-name" name="name" placeholder="Escribe tu nombre" required>
          </div>
          <div class="input-field">
            <label for="project-email">Correo *</label>
            <input type="email" id="project-email" name="email" placeholder="Escribe tu correo" required>
          </div>
          <div class="input-field">
            <label for="project-phone">Teléfono *</label>
            <input type="tel" id="project-phone" name="phone" placeholder="Ej: +57 300 123 4567" required>
          </div>
          <div class="input-field">
            <label for="project-timeline">Fecha de lanzamiento deseada</label>
            <select id="project-timeline" name="timeline">
              <option value="" selected>Selecciona una opción</option>
              <option value="inmediato">Inmediatamente</option>
              <option value="1-3_meses">En 1 - 3 meses</option>
              <option value="3-6_meses">En 3 - 6 meses</option>
              <option value="6+_meses">Más de 6 meses</option>
            </select>
          </div>
        </div>
        
        <div class="input-field">
          <label for="project-vision">Cuéntanos sobre tu producto *</label>
          <textarea id="project-vision" name="vision" rows="4" placeholder="Estamos construyendo una app para..." required></textarea>
        </div>
        
        <div class="budget-options">
          <span class="budget-label">¿Cuál es tu presupuesto mensual de desarrollo?</span>
          <div class="budget-buttons">
            <label class="budget-option">
              <input type="radio" name="budget" value="10k_menos">
              <span>$10K o menos</span>
            </label>
            <label class="budget-option">
              <input type="radio" name="budget" value="10k_20k">
              <span>$10K - $20K / mes</span>
            </label>
            <label class="budget-option">
              <input type="radio" name="budget" value="20k_30k">
              <span>$20K - $30K / mes</span>
            </label>
            <label class="budget-option">
              <input type="radio" name="budget" value="prioridad_velocidad">
              <span>Prioridad: velocidad</span>
            </label>
          </div>
        </div>
        
        <div class="submit-wrapper">
          <button type="submit" class="project-intake-submit">Enviar solicitud</button>
          <p class="disclaimer">Al enviar aceptas que nos comuniquemos contigo para hablar de tu proyecto.</p>
        </div>
      </form>
    </div>
  </div>
</section>
```

---

## 🎴 Componentes de Tarjetas (Case Studies)

### Área de Case Studies

```css
.case-studies-area {
  background-color: #fff;
}

.case-studies-inner {
  max-width: 100%;
}

.case-studies-wrapper {
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.case-study-card {
  background-color: #F8F8F8;
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.04);
  transition: all 0.4s ease;
}

.case-study-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
}

.case-image-wrapper {
  width: 100%;
  height: 420px;
  overflow: hidden;
  background-color: #F0F2F5;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 30px;
}

.case-image-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
  transition: transform 0.5s ease;
}

.case-study-card:hover .case-image-wrapper img {
  transform: scale(1.05);
}

.case-text-content {
  padding: 70px 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.case-card-title {
  font-size: 38px;
  font-weight: 600;
  color: var(--primary);
  margin-bottom: 28px;
  line-height: 1.2;
}

.case-card-description {
  font-size: 17px;
  color: var(--secondary);
  line-height: 1.7;
  margin-bottom: 36px;
}

.case-card-metrics {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.metric-item {
  display: block;
  font-size: 16px;
  font-weight: 600;
  color: #E74C3C;
  line-height: 1.6;
}

/* Responsive */
@media only screen and (max-width: 1199px) {
  .case-text-content {
    padding: 50px 45px;
  }
  .case-card-title {
    font-size: 34px;
  }
  .case-card-description {
    font-size: 16px;
  }
  .case-image-wrapper {
    height: 380px;
    padding: 25px;
  }
}

@media only screen and (max-width: 991px) {
  .case-studies-wrapper {
    margin-top: 40px;
    gap: 30px;
  }
  .case-text-content {
    padding: 40px 35px;
  }
  .case-card-title {
    font-size: 30px;
    margin-bottom: 20px;
  }
  .case-card-description {
    font-size: 15px;
    margin-bottom: 28px;
  }
  .case-image-wrapper {
    height: 350px;
    padding: 20px;
  }
  .case-card-metrics {
    gap: 10px;
  }
}

@media only screen and (max-width: 767px) {
  .case-studies-wrapper {
    margin-top: 30px;
    gap: 24px;
  }
  .case-study-card {
    border-radius: 16px;
  }
  .case-text-content {
    padding: 35px 30px;
  }
  .case-card-title {
    font-size: 26px;
    margin-bottom: 16px;
  }
  .case-card-description {
    font-size: 14px;
    margin-bottom: 24px;
  }
  .case-card-metrics {
    gap: 10px;
  }
  .metric-item {
    font-size: 14px;
  }
  .case-image-wrapper {
    height: 280px;
    padding: 20px;
  }
}

@media only screen and (max-width: 575px) {
  .case-text-content {
    padding: 28px 24px;
  }
  .case-card-title {
    font-size: 22px;
  }
  .case-image-wrapper {
    height: 240px;
    padding: 15px;
  }
}
```

### Estructura HTML de Case Studies

```html
<section class="case-studies-area section-spacing">
  <div class="container">
    <div class="case-studies-inner">
      <div class="section-header">
        <div class="section-title-wrapper">
          <div class="title-wrapper">
            <h2 class="section-title">Lo que estamos construyendo...</h2>
          </div>
        </div>
      </div>
      
      <div class="case-studies-wrapper">
        <!-- Case Study Card 1 -->
        <div class="case-study-card">
          <div class="row g-0 align-items-center">
            <div class="col-lg-6">
              <div class="case-image-wrapper">
                <img src="path/to/image.png" alt="Case Study Image">
              </div>
            </div>
            <div class="col-lg-6">
              <div class="case-text-content">
                <h3 class="case-card-title">Título del Proyecto</h3>
                <p class="case-card-description">Descripción del proyecto...</p>
                <div class="case-card-metrics">
                  <span class="metric-item">⚡ 6 Meses de idea a MVP</span>
                  <span class="metric-item">30k+ Usuarios Mensuales</span>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Case Study Card 2 (imagen a la derecha) -->
        <div class="case-study-card">
          <div class="row g-0 align-items-center">
            <div class="col-lg-6 order-lg-2">
              <div class="case-image-wrapper">
                <img src="path/to/image.png" alt="Case Study Image">
              </div>
            </div>
            <div class="col-lg-6 order-lg-1">
              <div class="case-text-content">
                <h3 class="case-card-title">Título del Proyecto</h3>
                <p class="case-card-description">Descripción del proyecto...</p>
                <div class="case-card-metrics">
                  <span class="metric-item">Métrica 1</span>
                  <span class="metric-item">Métrica 2</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## 📏 Espaciado y Utilidades

### Clases de Espaciado

```css
/* Padding Bottom */
.pb-10 { padding-bottom: 10px; }
.pb-15 { padding-bottom: 15px; }
.pb-20 { padding-bottom: 20px; }
.pb-25 { padding-bottom: 25px; }
.pb-30 { padding-bottom: 30px; }
.pb-35 { padding-bottom: 35px; }
.pb-40 { padding-bottom: 40px; }
.pb-45 { padding-bottom: 45px; }

/* Padding Top */
.pt-10 { padding-top: 10px; }
.pt-15 { padding-top: 15px; }
.pt-20 { padding-top: 20px; }
.pt-25 { padding-top: 25px; }
.pt-30 { padding-top: 30px; }
.pt-35 { padding-top: 35px; }
.pt-40 { padding-top: 40px; }
.pt-45 { padding-top: 45px; }

/* Margin Bottom */
.mb-10 { margin-bottom: 10px; }
.mb-15 { margin-bottom: 15px; }
.mb-20 { margin-bottom: 20px; }
.mb-25 { margin-bottom: 25px; }
.mb-30 { margin-bottom: 30px; }

/* Margin Top */
.mt-10 { margin-top: 10px; }
.mt-15 { margin-top: 15px; }
.mt-20 { margin-top: 20px; }
.mt-25 { margin-top: 25px; }
.mt-30 { margin-top: 30px; }
```

### Clases de Utilidad

```css
.text-center { text-align: center; }
.text-left { text-align: left; }
.text-right { text-align: right; }

.b-radius { border-radius: 12px; }

.medium { font-weight: 600; }
.bold { font-weight: 700; }
```

---

## 📱 Breakpoints Responsive

```css
/* Extra Extra Large */
@media only screen and (min-width: 1920px) {
  /* Estilos para pantallas muy grandes */
}

/* Extra Large */
@media only screen and (max-width: 1919px) {
  /* Estilos para pantallas grandes */
}

/* Large */
@media only screen and (max-width: 1399px) {
  .container {
    max-width: 1140px;
  }
}

/* Medium Large */
@media only screen and (max-width: 1199px) {
  .container {
    max-width: 960px;
  }
}

/* Medium */
@media only screen and (max-width: 991px) {
  .container {
    max-width: 720px;
  }
  
  .section-spacing {
    padding-top: 80px;
    padding-bottom: 80px;
  }
}

/* Small */
@media only screen and (max-width: 767px) {
  .container {
    max-width: 540px;
  }
  
  .section-spacing {
    padding-top: 60px;
    padding-bottom: 60px;
  }
  
  h1 { font-size: 36px; }
  h2 { font-size: 30px; }
  h3 { font-size: 26px; }
}

/* Extra Small */
@media only screen and (max-width: 575px) {
  .container {
    max-width: 100%;
    padding: 0 15px;
  }
  
  h1 { font-size: 28px; }
  h2 { font-size: 24px; }
  h3 { font-size: 20px; }
}
```

---

## ✨ Animaciones y Transiciones

### Transiciones Base

```css
* {
  transition: all 0.3s ease;
}

a {
  transition: all 0.3s;
}

button {
  transition: all 0.3s ease;
}
```

### Animaciones de Fade (GSAP)

```css
.has_fade_anim {
  opacity: 0;
  transform: translateY(30px);
}

/* Estas animaciones se controlan con GSAP ScrollTrigger */
```

### Hover Effects

```css
/* Botones */
.wc-btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(7, 32, 50, 0.2);
}

/* Tarjetas */
.case-study-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
}

/* Enlaces */
a:hover {
  color: var(--primary);
}
```

---

## 🚀 Implementación Rápida

### Paso 1: Configurar Variables CSS

Copia las variables CSS en tu archivo principal de estilos.

### Paso 2: Configurar Fuentes

1. Descarga o incluye las fuentes necesarias
2. Agrega las declaraciones `@font-face`
3. Aplica las clases de fuente al `body` o elementos específicos

### Paso 3: Incluir Componentes

Copia los estilos de los componentes que necesites (botones, formularios, tarjetas, etc.)

### Paso 4: Estructura HTML

Usa la estructura HTML proporcionada para cada componente, ajustando el contenido según tus necesidades.

### Paso 5: Responsive

Asegúrate de incluir los breakpoints responsive para que el diseño se adapte a diferentes tamaños de pantalla.

---

## 📚 Dependencias Externas

Este diseño utiliza las siguientes librerías (opcionales para replicar el diseño básico):

- **Bootstrap 5** (para grid system)
- **GSAP** (para animaciones de scroll)
- **Font Awesome 6** (para iconos)
- **Swiper.js** (para sliders/carousel)

---

## 🎯 Notas Importantes

1. **Colores**: Ajusta los colores según tu marca, pero mantén la estructura de variables CSS para facilitar cambios futuros.

2. **Fuentes**: Si no tienes acceso a Geist, puedes usar "DM Sans" como alternativa, que es la fuente secundaria del sitio.

3. **Espaciado**: El espaciado está diseñado para crear una jerarquía visual clara. Ajusta según tus necesidades.

4. **Responsive**: Siempre prueba en diferentes tamaños de pantalla. Los breakpoints están optimizados para dispositivos móviles, tablets y desktop.

5. **Accesibilidad**: Asegúrate de mantener contraste adecuado entre texto y fondo, y de usar etiquetas semánticas en HTML.

---

## 📝 Licencia y Créditos

Este sistema de diseño está basado en el template "Sassly" de Crowdyflow, adaptado para Kubo Lab.

---

**Última actualización**: 2024

