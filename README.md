# 🚀 Hackatón 0 – CS2031

¡Bienvenidos! 🎉
Desde el curso **CS2031** les damos una cordial bienvenida al ciclo **2026-1**. El foco sigue siendo el mismo que siempre: colaboración bajo presión, conflictos de Git y trabajo en equipo real.

## 🤔 ¿Qué trae esta Hackatón?

Esta **Hackatón 0** es una primera muestra del concepto de hackatones. Los equipos son de **exactamente 3 integrantes** y el proyecto tiene varios bugs intencionales para resolver. El foco es el mismo de siempre:

> **Git + GitHub + HTML + CSS + trabajo en equipo**

No es necesario saber programar en un lenguaje de backend. El reto está en **coordinar, resolver conflictos y desplegar** una página funcional.

Si aún no viste el video de introducción a Git y GitHub, este es el momento: [👉 Video de introducción a Git y GitHub](https://www.youtube.com/watch?v=8CmZysIzcbc)

---

## 👥 Trabajo en equipo

Los equipos son de **3 integrantes fijos**. Cada uno tendrá un rol claro:

- Habrá quienes sean buenos organizando 🗂️
- Otros que lideren 🧭
- Y otros que ejecuten rápido ⚡

Coordínense bien antes de empezar a pushear cambios. El repositorio incluye **GitHub Actions** que corren automáticamente: una valida el HTML y los enlaces en cada PR, y otra despliega la página en GitHub Pages en cada push a `main`.

---

## 📜 El reto

Un TA (que no diremos quién 🤫) volvió a meter mano en el repositorio y rompió varias cosas a la vez. El proyecto es una página web sobre **Estructuras de Datos & Algoritmos** para el curso CS2031.

🎯 **Tu objetivo:** corregir todos los bugs, completar los datos del equipo y desplegar la página en **GitHub Pages**.

---

## 👑 Organización del equipo

- Elijan un **líder de equipo** que cree el repositorio a partir de la plantilla `cs2031-2026-1-hackathon-0` (asegurándose de incluir **todas las ramas**).
- El líder da acceso de colaborador a los otros 2 integrantes.
- Cada integrante trabaja en **su propia rama** (`feat/member-nombre`) y abre un **PR** para que el líder lo revise y acepte.
- Los conflictos se resuelven en equipo, **no individualmente**.

---

## ✅ Checklist del equipo (issues a crear por el líder)

### #1 — Datos personales (1 PR por persona)

Cada integrante edita **su tarjeta** en `index.html` dentro de `<div class="team__grid">`.

Reemplaza en tu `<div class="team-card">`:
- **Foto de perfil** (`src` y `alt` en `<img>`)
- **Nombre completo** (`<h3 class="team-card__name">`)
- **Especialidad o rol** (`<p class="team-card__role">`)
- **Links** de GitHub y LinkedIn (`href`)

**Conflicto esperado:** los 3 editan secciones cercanas en el mismo archivo → deberán resolver el merge conflict conservando los 3 nombres.

Ejemplo de tarjeta correctamente completada:
```html
<div class="team-card__content">
  <h3 class="team-card__name">Sparky García</h3>
  <p class="team-card__role">Backend Developer</p>
  <div class="team-card__social">
    <a
      href="https://github.com/sparkygarcia"
      class="team-card__social-link team-card__social-link--github"
    >
      <i class="fab fa-github"></i>
    </a>
    <a
      href="https://www.linkedin.com/in/sparkygarcia"
      class="team-card__social-link team-card__social-link--linkedin"
    >
      <i class="fab fa-linkedin"></i>
    </a>
  </div>
</div>
```

---

### #2 — CSS modular (1 PR)

La rama `clean-css` tiene el CSS dividido en archivos modulares (`styles/footer.css`, `styles/header.css`, `styles/main.css`, etc.).

La rama `main` tiene todo el CSS en un único archivo monolítico `index.css`.

**Conflicto esperado:** al hacer merge de `clean-css` a `main`, tendrán dos versiones completamente distintas del sistema de estilos. Deben integrarlas correctamente.

El `index.html` de la rama `clean-css` importa los módulos así:
```html
<link rel="stylesheet" href="styles/page.css" />
<link rel="stylesheet" href="styles/header.css" />
<link rel="stylesheet" href="styles/nav.css" />
<link rel="stylesheet" href="styles/main.css" />
<link rel="stylesheet" href="styles/team.css" />
<link rel="stylesheet" href="styles/footer.css" />
```

Deben decidir en equipo **cuál arquitectura conservar** (o combinar ambas) y actualizar `index.html` en consecuencia.

---

### #3 — Navbar fix (1 PR)

Usando la rama `navbar-fix`, corrige los enlaces del `<nav>` en `index.html`.

Los 3 links del menú apuntan a IDs incorrectos:

| Link visible | href actual (roto) | href correcto |
|---|---|---|
| Inicio | `#inicio` | `#hero` |
| Acerca de | `#sobre` | `#about` |
| Equipo | `#integrantes` | `#team` |

---

### ✅ Publicado en GitHub Pages

El deploy es **automático** gracias al workflow `.github/workflows/deploy.yml`. Cada push a `main` despliega la página sin configuración manual.

Solo necesitan habilitarlo una vez en la configuración del repositorio:
1. Ir a **Settings → Pages**
2. En *Source* seleccionar **GitHub Actions**
3. A partir de ahí, cada merge a `main` despliega automáticamente

La URL del sitio aparece en la pestaña **Environments → github-pages** del repositorio.

---

## ⚡ Ejemplo de conflicto en `index.html`

Cuando dos integrantes editan líneas cercanas, Git genera algo así:

```html
<div class="team-card">
  <<<<<<< HEAD
  <h3 class="team-card__name">Ana Torres</h3>
  <p class="team-card__role">Frontend Developer</p>
  <a href="https://github.com/anatorres">GitHub</a>
  =======
  <h3 class="team-card__name">Luis Ríos</h3>
  <p class="team-card__role">Backend Developer</p>
  <a href="https://github.com/luisrios">GitHub</a>
  >>>>>>> feat/member-luis
</div>
```

La tarea del equipo es **resolver esto manualmente**, eliminando los marcadores y preservando los datos de ambos integrantes:

```html
<div class="team-card">
  <h3 class="team-card__name">Ana Torres</h3>
  <p class="team-card__role">Frontend Developer</p>
  <a href="https://github.com/anatorres">GitHub</a>
</div>
<div class="team-card">
  <h3 class="team-card__name">Luis Ríos</h3>
  <p class="team-card__role">Backend Developer</p>
  <a href="https://github.com/luisrios">GitHub</a>
</div>
```

---

## 🗂️ Resumen de ramas y PRs

| Rama | Responsable | Tipo | PR |
|---|---|---|---|
| `feat/member-nombre` | Cada integrante | Datos personales | 1 por persona |
| `clean-css` | 1 integrante | CSS modular | 1 PR |
| `navbar-fix` | 1 integrante | Corrección de enlaces | 1 PR |

> El líder puede asignar las ramas `clean-css`, `navbar-fix` como tareas a distintos integrantes del equipo.

## ⚙️ GitHub Actions incluidas

| Workflow | Archivo | Se ejecuta en |
|---|---|---|
| Validación HTML + links | `.github/workflows/validate.yml` | Cada PR hacia `main` |
| Deploy a GitHub Pages | `.github/workflows/deploy.yml` | Cada push a `main` |

**`validate.yml`** corre dos checks en cada PR:
- Valida que el HTML sea correcto según el estándar W3C
- Verifica que todos los `href="#..."` del HTML apunten a un `id` que realmente existe — el PR **no podrá mergearse** si el navbar tiene links rotos

**`deploy.yml`** despliega automáticamente la página en GitHub Pages tras cada merge a `main` (TODO).

---

💡 Recuerden: la página es **estática (HTML + CSS)**. No hay JavaScript ni backend. El desafío está en **coordinar, resolver conflictos y documentar todo con ramas y PRs**.

¡Éxito equipo! 💪 Con cariño, el equipo docente de CS2031.
