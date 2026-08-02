# SyntaxLand 🐹

> El universo digital de **Johan Yahir Villalpando Ibarra** — software engineer, y su alter ego, **CapySyntax**.

Landing page personal construida como una historia por niveles: de perfil, a proyectos, a libro. Pensada para vivir como el hub central de todo lo que hago — desde ahí se ramifica hacia mi portafolio profesional y (pronto) hacia el universo de CapySyntax.

---

## 🧭 Qué es esto

Este no es un portafolio tradicional de una sola pantalla. Es una landing tipo *scrollytelling*: cada "piso" (`FirstLevel`, `SecondLevel`, `ThirdLevel`) cuenta una parte distinta de la historia mientras haces scroll.

- **Nivel 01 — Perfil:** quién soy, estética tipo blueprint/cuaderno de ingeniería.
- **Nivel 02 — Proyectos:** mis proyectos más grandes (Trabaja.io, BabyVault), con un efecto de luz/parábolas convergiendo.
- **Nivel 03 — Libro:** *Sintaxis Social*, mi libro, presentado literalmente como sintaxis de código.

Más adelante se suma un segundo layout con navbar propio para el **portafolio profesional** (pensado para reclutadores), y eventualmente un switch de identidad entre **Johan** y **CapySyntax**.

---

## 🛠️ Stack

| Área | Tecnología |
|---|---|
| Framework | [Astro](https://astro.build) |
| Tipado | TypeScript (`strict` / `strictest`) |
| Animación | GSAP + ScrollTrigger |
| Estilos | CSS con variables/Tailwind |
| Fuentes | IBM Plex Mono, Inter, Caveat |

No se usa React en la landing por ahora — el control de identidad (Johan ↔ CapySyntax) se resuelve con un script de TS y atributos `data-*`, no con `useState`/Context, para no cargar runtime innecesario en una página que Astro puede resolver estática. React queda reservado para piezas con estado real (ej. un explorador de proyectos con filtros).

---

## 📁 Estructura

```
src/
├── components/
│   └── landing/
│       └── johan/
│           ├── FirstLevel.astro
│           ├── SecondLevel.astro
│           └── ThirdLevel.astro
│       └── capy/            ← (futuro) espejo para CapySyntax
│
├── layouts/
│   └── LandingLayout.astro  ← navbar + slot + footer
│
├── pages/
│   ├── index.astro          ← ensambla los niveles dentro de LandingLayout
│   └── portafolio/          ← (futuro) layout y páginas para el lado profesional
│
├── styles/
│   └── landing/
│       └── johan/
│           ├── 1stLevel.css
│           ├── 2ndLevel.css
│           └── 3rdLevel.css
│
└── scripts/
    └── persona.ts           ← (futuro) toggle Johan / CapySyntax
```

Cada nivel es un componente autocontenido: su propio HTML y su propio CSS importado directamente en el componente (`import "../../../styles/..."`, **sin** asignarlo a una variable — importante para que Astro lo inyecte correctamente en el `<head>`).

---

## 🚀 Correr el proyecto

```bash
npm install
npm run dev
```

Se levanta en `http://localhost:4321`.

---

## 🗺️ Roadmap

- [x] `LandingLayout` con navbar y footer
- [x] `FirstLevel` — perfil / blueprint
- [ ] `SecondLevel` — proyectos (Trabaja.io, BabyVault) con animación de parábolas
- [ ] `ThirdLevel` — libro *Sintaxis Social*
- [ ] Migrar animaciones a GSAP + ScrollTrigger
- [ ] `PortfolioLayout` con su propio navbar, pensado para reclutadores
- [ ] Toggle de identidad Johan ↔ CapySyntax (`data-persona` + CSS, sin React)
- [ ] Evaluar rutas separadas (`/` vs `/capy`) con View Transitions como alternativa al toggle
- [ ] `data/projects.ts` como fuente única de proyectos, con campo `showIn` para filtrar por layout
---

*Aguascalientes, México — construido de noche, a punta de café y capybaras.* ☕🐹
