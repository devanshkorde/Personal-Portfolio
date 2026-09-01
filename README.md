<div align="center">

# Devansh Korde — Personal Portfolio

**Building things that matter.**

A hand-built, dependency-free portfolio site with a custom cursor, an interactive constellation particle field, and a typewriter tagline — written in plain HTML, CSS, and JavaScript.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-devanshkordeportfolio.netlify.app-d7b414?style=for-the-badge&logo=netlify&logoColor=black)](https://devanshkordeportfolio.netlify.app/)
[![GitHub](https://img.shields.io/badge/Source-devanshkorde-111111?style=for-the-badge&logo=github&logoColor=white)](https://github.com/devanshkorde/Personal-Portfolio)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/devansh-korde-6a6846333/)

<a href="https://devanshkordeportfolio.netlify.app/">
  <img src="assets/preview.gif" alt="Preview of the Devansh Korde portfolio — click to open the live site" width="100%">
</a>

<sub>☝️ Click the preview to open the live site</sub>

</div>

---

## Overview

This is my personal portfolio — a single-page site that introduces who I am, what I work with, and what I've built. It's intentionally written without frameworks or build tools: no React, no bundler, no `node_modules`. Just three files, a canvas element, and about 1,200 lines of code you can read top to bottom.

The design leans on a mustard-and-black palette, oversized Bebas Neue display type, and a hand-drawn SVG sketch frame around the profile photo — deliberately imperfect, so it reads as drawn rather than generated.

**Live at → [devanshkordeportfolio.netlify.app](https://devanshkordeportfolio.netlify.app/)**

---

## Features

| | Feature | What it does |
|---|---|---|
| 🖱️ | **Custom cursor** | A solid dot tracks the pointer exactly, while a larger ring trails behind with eased interpolation (`0.12` lerp factor) for a soft magnetic feel. |
| ✨ | **Interactive particle field** | 90 canvas particles drift and pulse independently. Any two within 100px are joined by a line whose opacity fades with distance, and every particle within 140px of your cursor connects to it — so the constellation reshapes itself as you move. |
| ⌨️ | **Typewriter tagline** | Cycles three taglines with character-by-character typing (70ms), deletion (35ms), and a 2.2s hold at the end of each line. |
| 🎯 | **Scroll-spy navigation** | Nav links highlight the section currently in view, and all in-page anchors scroll smoothly instead of jumping. |
| 👁️ | **Reveal on scroll** | An `IntersectionObserver` adds an `in-view` class at 12% visibility, so sections animate in once as you reach them — no scroll-event thrashing. |
| ✏️ | **Hand-drawn SVG frame** | Two offset wobbly bézier circles plus a deliberate gap stroke at the bottom, giving the profile photo a sketched, unfinished outline. |
| 📱 | **Responsive layout** | Below 768px the hero stacks and centers, the about and project grids collapse to one column, and CTAs go vertical. |
| 🪶 | **Zero dependencies** | Only two external requests: Google Fonts and the Font Awesome icon CDN. Nothing to install, nothing to build. |

---

## Tech Stack

<div align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Canvas API](https://img.shields.io/badge/Canvas_API-FF6B6B?style=flat-square&logo=html5&logoColor=white)
![Netlify](https://img.shields.io/badge/Netlify-00C7B7?style=flat-square&logo=netlify&logoColor=white)

</div>

- **Markup** — Semantic HTML5, one page, five sections
- **Styling** — Vanilla CSS with custom properties, Flexbox, and CSS Grid
- **Behaviour** — ES6 JavaScript, `requestAnimationFrame` render loops, `IntersectionObserver`
- **Graphics** — Canvas 2D for particles, inline SVG for the sketch frame
- **Type** — Bebas Neue (display), DM Sans (body), Crimson Pro (italic accents)
- **Icons** — Font Awesome 6.5
- **Hosting** — Netlify

---

## Project Structure

```
Personal-Portfolio/
├── Portfolio/
│   ├── index.html          # All five sections: hero, about, skills, projects, contact
│   ├── style.css           # ~817 lines — design tokens, layout, animations, responsive rules
│   ├── main.js             # ~206 lines — cursor, particles, scroll-spy, typewriter, reveal
│   └── assets/
│       └── images/
│           └── FormalPhoto.png
├── assets/
│   └── preview.gif         # Demo recording used in this README
└── README.md
```

### Sections

| # | Section | Contents |
|---|---------|----------|
| 00 | **Hero** | Name, animated tagline, sketch-framed photo, primary CTAs |
| 01 | **About** | Background, interests, and a stat card (years coding, projects built, curiosity) |
| 02 | **Skills** | Split into Development (HTML, CSS, JS, Python, Java, SQL) and Creative Tools (Photography, Filmmaking, Photoshop, CapCut) |
| 03 | **Projects** | EzGrind, this portfolio, and Code Escape Room — each with stack tags and links |
| 04 | **Contact** | Email CTA plus GitHub, LinkedIn, and Instagram links |

---

## Getting Started

No build step, no package manager. Clone it and open it.

```bash
git clone https://github.com/devanshkorde/Personal-Portfolio.git
cd Personal-Portfolio/Portfolio
```

Then either open `index.html` directly in a browser, or serve it locally:

```bash
# Python
python -m http.server 8000

# Node
npx serve .
```

Visit `http://localhost:8000`.

> A local server isn't strictly required, but it's the better habit — `file://` blocks some browser APIs and makes relative paths behave inconsistently.

### Deploying

The site is static, so any static host works. On Netlify, point the publish directory at `Portfolio/` and leave the build command empty.

---

## Customising

Everything visual is driven by CSS custom properties at the top of `style.css`:

```css
:root {
  --bg:            #d7b414;   /* mustard background        */
  --bg-2:          #0f0f0d;   /* near-black surface        */
  --border:        #b89a0e;   /* muted gold border         */
  --font-display:  'Bebas Neue', sans-serif;
  --font-body:     'DM Sans', sans-serif;
}
```

Common tweaks:

| To change | Edit |
|---|---|
| Colour scheme | The `:root` block in `style.css` |
| Rotating taglines | The `lines` array in `main.js` |
| Particle count / link distance | `PARTICLE_COUNT` and the `100` / `140` distance thresholds in `main.js` |
| Typing speed | The `delay` values inside `typeEffect()` |
| Profile photo | Replace `Portfolio/assets/images/FormalPhoto.png` |
| Projects | The `.project-card` blocks in `index.html` |

---

## Notes & Known Issues

Honest list of things worth fixing:

- **`FormalPhoto.png` is 6.3 MB.** That's the single biggest thing hurting load time. Compressing it and serving WebP would likely cut it by 90%+.
- **The Portfolio project card links to `#`.** In the projects section, project 02's "View Code" link is still a placeholder — it should point at this repo.
- **`cursor: none` is set globally.** The custom cursor doesn't exist on touch devices, so the native cursor is hidden with nothing replacing it. Worth gating behind `@media (hover: hover)`.
- **No mobile nav menu.** Below 768px the social icons hide, but the nav links stay in a row rather than collapsing into a hamburger.
- **The particle link check is O(n²).** At 90 particles that's ~4,000 comparisons per frame — fine on desktop, but it's the first thing to optimise if the count ever grows.
- **No `prefers-reduced-motion` handling.** The particle loop, typewriter, and reveal animations all run regardless of the user's motion preference.

---

## Other Projects

| Project | Description |
|---------|-------------|
| **[EzGrind](https://github.com/devanshkorde/EzGrind)** | Full-stack fitness tracker — workout logging, sets with weight/reps/time-under-tension, session auth, and a progress dashboard. Flask + MySQL. |
| **[Code Escape Room](https://github.com/devanshkorde/Code-Escape-Room)** | Gamified web escape room using NVIDIA NIM to adapt puzzle difficulty from user performance. Improved average completion rates by 12%. |
| **[TruthLens AI](https://github.com/devanshkorde/TruthLens-AI)** | Real-time fake news and deepfake detection across text and images, with explanations and a credibility score. |

---

## Contact

<div align="center">

**Devansh Korde** — B.Tech Information Technology, Medicaps University · Indore, India

[![Email](https://img.shields.io/badge/Email-devanshkorde195@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:devanshkorde195@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-devansh--korde-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/devansh-korde-6a6846333/)
[![GitHub](https://img.shields.io/badge/GitHub-devanshkorde-111111?style=flat-square&logo=github&logoColor=white)](https://github.com/devanshkorde)
[![Instagram](https://img.shields.io/badge/Instagram-devansh__korde-E4405F?style=flat-square&logo=instagram&logoColor=white)](https://www.instagram.com/devansh_korde/)

Open to opportunities.

<br>

⭐ **If you found this useful, consider starring the repo.**

</div>
