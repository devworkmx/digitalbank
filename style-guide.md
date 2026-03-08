# Landing Page – Development Guide

Este documento define las reglas y estándares que seguiremos para desarrollar la landing page.  
El objetivo es mantener un **código limpio, consistente, accesible y optimizado para SEO**.

---

# 1. Principios del Proyecto

El desarrollo seguirá las siguientes prácticas:

- HTML semántico
- Accesibilidad básica (a11y)
- Optimización SEO
- Mobile-First Workflow
- Metodología BEM para CSS
- GitFlow para control de versiones
- Conventional Commits

---

# 2. HTML Semántico, SEO y Accesibilidad

El HTML debe usar **etiquetas semánticas siempre que sea posible** para mejorar:

- SEO
- Accesibilidad
- Mantenibilidad del código

## Estructura semántica recomendada

```html
<header class="header">
  <nav class="nav"></nav>
</header>

<main>
  <section class="hero"></section>
  <section class="features"></section>
  <section class="articles"></section>
</main>

<footer class="footer"></footer>
```

Evitar usar `<div>` cuando exista una etiqueta semántica apropiada.

### Etiquetas semánticas comunes

```
header
nav
main
section
article
aside
footer
figure
figcaption
```

---

## Buenas prácticas de SEO y accesibilidad

### Texto alternativo en imágenes

Todas las imágenes deben incluir `alt`.

```html
<img src="team.jpg" alt="Equipo de desarrollo trabajando en laptops" />
```

---

### Atributos de accesibilidad

Cuando sea necesario usar:

```
alt
aria-label
title
role
```

Ejemplo:

```html
<button aria-label="Abrir menú de navegación"></button>
```

---

# 3. Mobile-First Workflow

El desarrollo se realiza **primero para móviles**.

Resolución base:

```
390px
```

Solo utilizaremos **dos breakpoints** adicionales.

```
md → 768px
lg → 1024px
```

Ejemplo:

```css
.hero {
  padding: 20px;
}

/* tablet */
@media (min-width: 768px) {
  .hero {
    padding: 40px;
  }
}

/* desktop */
@media (min-width: 1024px) {
  .hero {
    padding: 60px;
  }
}
```

Regla importante:

> Primero se escribe el CSS para **mobile**, luego se escalan estilos para pantallas más grandes.

---

# 4. Metodología BEM

BEM es una convención para nombrar clases CSS que hace que el código sea **escalable, reutilizable y fácil de entender**.

BEM significa:

```
Block
Element
Modifier
```

---

## Block

El **block** es un componente independiente de la interfaz.

Ejemplos:

```
card
button
navbar
hero
footer
```

```html
<div class="card"></div>
```

---

## Element

Un **element** es una parte del bloque que depende de él.

Se escribe con:

```
block__element
```

Ejemplo:

```html
<div class="card">
  <h3 class="card__title"></h3>
  <p class="card__description"></p>
  <button class="card__button"></button>
</div>
```

---

## Modifier

Un **modifier** cambia la apariencia o comportamiento de un bloque o elemento.

Se escribe con:

```
block--modifier
block__element--modifier
```

Ejemplo:

```html
<button class="button button--primary"></button>
<button class="button button--secondary"></button>
```

---

## Ejemplo completo

```html
<div class="card card--featured">
  <img class="card__image" src="img.jpg" alt="Tarjeta destacada" />

  <h3 class="card__title">Servicio Premium</h3>

  <p class="card__description">Accede a beneficios exclusivos.</p>

  <button class="card__button card__button--primary">Más información</button>
</div>
```

---

## Reglas importantes de BEM

✔ Usar nombres descriptivos  
✔ Evitar clases genéricas  
✔ No depender del selector del HTML

Evitar:

```
.red-button
.box
.title1
```

Preferir:

```
button
button--primary
card__title
hero__button
```

---

# 5. GitFlow

Usaremos un flujo de trabajo basado en ramas.

## Ramas principales

```
main
develop
```

- **main** → versión final / producción
- **develop** → integración del desarrollo

---

## Ramas de trabajo

Las nuevas funcionalidades se desarrollan en ramas `feature`.

Formato:

```
feature/nombre-feature
```

Ejemplos:

```
feature/hero-section
feature/navigation-menu
feature/articles-grid
```

Correcciones:

```
fix/nombre-fix
```

---

# 6. Pull Requests

Flujo de trabajo:

1. Crear una rama desde `develop`

```
feature/nombre-feature
```

2. Desarrollar la funcionalidad.

3. Subir la rama al repositorio.

```
git push origin feature/hero-section
```

4. Crear un **Pull Request hacia `develop`**.

```
feature/hero-section → develop
```

No hacer push directo a:

```
main
develop
```

---

# 7. Conventional Commits

Los commits deben seguir el formato:

```
tipo: descripción
```

Tipos principales:

```
feat     → nueva funcionalidad
fix      → corrección de bug
style    → cambios de estilos
refactor → mejora de código
docs     → documentación
```

Ejemplos:

```
feat: add hero section
style: improve navbar layout
fix: mobile spacing issue
docs: update development guide
```

---

# 8. Design System

## Colors

### Primary

```
Blue 950: hsl(233, 26%, 24%)
Green 500: hsl(136, 64%, 51%)
Cyan 400: hsl(192, 69%, 51%)
```

### Neutral

```
Gray 600: hsl(233, 8%, 62%)
Gray 100: hsl(220, 16%, 96%)
Gray 50: hsl(0, 0%, 98%)
White: hsl(0, 100%, 100%)
```

---

# 9. Typography

## Body Copy

```
Font size: 18px
```

---

## Font

```
Font Family: Public Sans
```

[Descarga Aqui](https://fonts.google.com/specimen/Public+Sans)

Weights:

```
300
400
700
```

Ejemplo:

```css
body {
  font-family: 'Public Sans', sans-serif;
  font-size: 18px;
}
```

---

# 10. Reglas generales

✔ Código limpio y legible  
✔ Evitar estilos inline  
✔ Usar HTML semántico  
✔ Usar BEM para las clases  
✔ Mobile-first siempre

---
