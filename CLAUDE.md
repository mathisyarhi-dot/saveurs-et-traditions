# CLAUDE.md — Saveurs & Traditions

Référence de l'identité visuelle et des règles de développement pour le site vitrine de **Saveurs & Traditions**.

---

## Architecture des fichiers

```
/
├── index.html          ← Point d'entrée (HTML5 sémantique)
├── css/
│   └── style.css       ← Tout le design (mobile-first, sans framework)
├── js/
│   └── main.js         ← Toutes les interactions (ES6+, sans vulnérabilités)
└── assets/
    ├── logo.png        ← Logo circulaire (ne pas renommer)
    ├── croissant.svg   ← Icône viennoiseries (ne pas renommer)
    └── sandwich.svg    ← Icône snacking (ne pas renommer)
```

> **Règle absolue** : ne jamais renommer ni déplacer les fichiers dans `assets/`.

---

## Identité de la marque

| Champ        | Valeur |
|---|---|
| **Nom**      | Saveurs & Traditions |
| **Type**     | Boulangerie · Pâtisserie · Salon de thé |
| **Adresse**  | 12 Avenue Jean Lurçat, 78330 Fontenay-le-Fleury |
| **Repère**   | En face du commissariat |
| **Tél.**     | 01 34 62 48 91 |
| **Instagram**| @saveurs_et_traditions78 |
| **Note**     | 4,7 / 5 · Plus de 490 avis Google |
| **Horaires** | Mardi–Dimanche · 6 h 30 – 20 h 00 · Fermé le lundi |
| **Slogan**   | « Du pain, des pâtisseries et beaucoup de passion. » |

---

## Palette de couleurs

| Token CSS          | Valeur hex | Rôle |
|---|---|---|
| `--blanc-chaud`    | `#FCF8EE`  | Fond principal — jamais de blanc pur |
| `--creme`          | `#F8F2E8`  | Sections alternées |
| `--creme-fonce`    | `#EFE6D5`  | Zones neutres, placeholders photo |
| `--miel`           | `#B8832A`  | Couleur signature — boutons, accents, icônes clés |
| `--miel-clair`     | `#D4A855`  | Miel sur fonds sombres |
| `--miel-pale`      | `#F5E8CC`  | Fonds de badges et pills |
| `--brun-profond`   | `#2E1C0A`  | Hero, footer, sections sombres |
| `--brun-moyen`     | `#5C3A1E`  | Éléments secondaires |
| `--gris-chaud`     | `#7A6A58`  | Corps de texte — jamais de gris froid |

---

## Typographies

**Source** : Google Fonts CDN

| Famille                | Rôle                          | Poids        |
|---|---|---|
| Cormorant Garamond     | Titres, citations, ornements  | 300–600, italic |
| DM Sans                | Corps, UI, labels             | 300–500 |

**Règle absolue** : chaque `<h2>` doit contenir **un mot clé en italique doré** (`<em class="acc">`). C'est le cœur visuel de la marque — ne jamais l'omettre.

---

## Rayons de bordure

| Valeur | Contexte |
|---|---|
| `3px`  | Tous les blocs (cartes, boutons, inputs, photos) |
| `20px` | Pills et tags uniquement |
| `50%`  | Logos et avatars circulaires uniquement |

---

## Icônes

- **Bibliothèque** : Tabler Icons v3.19.0 webfont uniquement (classe `ti ti-*`)
- **Interdit** : émojis, glyphes Unicode comme icônes
- **Toléré** : `✦` pour l'ornement de séparation (opacité 0.32)
- **Cercle d'icône** : 36×36 px, fond `--miel-pale`, bordure `rgba(184,131,42,.35)`

---

## Animations & interactions

- **Easing** : `cubic-bezier(.4, 0, .2, 1)` sur tous les éléments interactifs
- **Durées** : rapide 160 ms · moyen 280 ms · lent 480 ms
- **Bouton hover** : fond s'assombrit de 6–8 % — pas d'ombre
- **Carte hover** : photo zoom `scale(1.03)`, bordure dorée subtile
- **Lien nav hover** : soulignement doré de gauche à droite (200 ms)
- **Zones photo hover** : overlay sombre + label « Ajouter »

---

## Règles de développement

### HTML
- Sémantique pure : `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- Attributs `aria-labelledby` sur chaque section
- `alt` descriptif sur toutes les images significatives
- `rel="noopener noreferrer"` sur les liens externes

### CSS
- **Mobile-first** : styles de base = mobile, `@media (min-width: 769px)` pour desktop
- Pas de framework externe — tout codé à la main
- Flexbox et CSS Grid uniquement (pas de float)
- Variables CSS (`--*`) pour tous les tokens — jamais de valeurs codées en dur

### JavaScript
- ES6+ strict (`'use strict'`)
- Pas d'`eval()`, pas de `document.write()`
- `textContent` pour injecter du texte (jamais `innerHTML` avec données utilisateur)
- `URL.createObjectURL()` pour les previews photo (safe, révoqué si nécessaire)
- Gestion des événements par `addEventListener` uniquement

---

## Structure des sections

| # | Section           | Fond           | Layout desktop       |
|---|---|---|---|
| 1 | Nav               | Blanc cassé (blur) | Sticky, flex row |
| 2 | Hero              | Brun profond   | Grid 50/50         |
| 3 | Bandeau passion   | Miel           | Centré             |
| 4 | Notre histoire    | Crème          | Grid 440px + 1fr   |
| 5 | Nos spécialités   | Blanc cassé    | Grid 3×2           |
| 6 | Salon de thé      | Brun profond   | Grid 1fr + 1fr     |
| 7 | Avis clients      | Blanc cassé    | Grid 3 colonnes    |
| 8 | Galerie           | Crème          | Grid 4col, tall ×2 |
| 9 | Contact & Horaires| Blanc cassé    | Grid 2 colonnes    |
| 10| Footer            | Brun profond   | Flex row           |
