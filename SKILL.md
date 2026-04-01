---
name: csf-bg-static-site
description: >
  Build and extend pages for the Bulgarian Cybersecurity Foundation website (CSF.bg).
  A fully static, dependency-free HTML/CSS/JS site with a defined design system,
  component library, and bilingual (BG/EN) content architecture.
  Use this skill whenever adding new pages, sections, or components to csf.bg.
---

## Project overview

CSF.bg is a **fully static single-codebase website** — no build tools, no frameworks, no npm.
Every page is a self-contained `.html` file that imports two Google Fonts and nothing else.
All interactivity is vanilla JS. All styling is CSS custom properties.

---

## Design system

### Color palette (CSS variables)

```css
/* Blues — primary brand */
--navy:      #0D1F3C   /* darkest bg, navbar, footer */
--navy-mid:  #162B52   /* cards on dark bg */
--royal:     #1E3E7A   /* gradients, shield fill */
--blue:      #2B5BB5   /* primary CTAs, links, accents */
--sky:       #4A7EC5   /* hover states, dots */
--sky-light: #A8C4E8   /* light text on dark bg, labels */

/* Neutrals — background & text */
--beige:     #F4EFE4   /* section backgrounds, card bases */
--cream:     #FAF8F3   /* page background */
--sand:      #D8CEBC   /* borders, dividers */
--tan:       #C4B49A   /* hover borders */

/* Text — espresso to brown */
--espresso:  #1C120A   /* primary body text */
--brown:     #4A3020   /* secondary text, chips */
--bark:      #7A5C3C   /* muted text, descriptions */

--white:     #FFFFFF
```

### Typography

- **Display / Headlines:** `Cormorant Garamond` (Google Fonts) — weights 300, 400, 500, 600, 700; italic variants used for hero emphasis
- **UI / Body:** `DM Sans` (Google Fonts) — weights 300, 400, 500, 600

```css
/* Usage pattern */
h1, h2, h3        → font-family: 'Cormorant Garamond', serif
body, nav, buttons → font-family: 'DM Sans', sans-serif
.display class     → force Cormorant on any element
```

### Type scale

```
--fs-xs:   0.75rem   /* badges, labels, meta */
--fs-sm:   0.875rem  /* body small, nav links, tags */
--fs-base: 1rem      /* default body */
--fs-md:   1.125rem  /* descriptions, subtitles */
--fs-lg:   1.375rem  /* card titles */
--fs-xl:   1.75rem   /* section subheads */
--fs-2xl:  2.5rem    /* section titles (mobile) */
--fs-3xl:  3.5rem    /* section titles (desktop) */
--fs-4xl:  5rem      /* hero h1 */
```

### Spacing & geometry

```
--radius-sm: 4px    /* buttons, small chips */
--radius:    8px    /* dropdowns, standard cards */
--radius-lg: 16px  /* section cards, large elements */

--shadow-sm: 0 2px 8px rgba(13,31,60,0.08)
--shadow:    0 6px 24px rgba(13,31,60,0.12)
--shadow-lg: 0 16px 48px rgba(13,31,60,0.18)

--transition: 0.28s cubic-bezier(0.4, 0, 0.2, 1)
```

---

## Component library

### Buttons

```html
<!-- Primary (blue fill) -->
<a href="#" class="btn btn-primary">
  <svg>…arrow icon…</svg>
  Label
</a>

<!-- Outline (white border, dark bg) -->
<a href="#" class="btn btn-outline">Label</a>

<!-- Dark (navy fill, sand border) -->
<a href="#" class="btn btn-dark">Label</a>
```

### Section header pattern

```html
<div class="section-header">
  <div class="section-header-left">
    <div class="section-label">Категория</div>          <!-- uppercase label with left line -->
    <h2 class="section-title">Заглавие на секцията</h2>
    <p class="section-desc">Описание…</p>
  </div>
  <a href="#" class="btn btn-dark">CTA бутон →</a>      <!-- optional -->
</div>
```

### Cards

**Area card** (white, hover lift + blue top border):
```html
<div class="area-card reveal">
  <span class="area-number">01</span>
  <div class="area-icon"><svg>…</svg></div>
  <h3 class="area-title">Заглавие</h3>
  <p class="area-desc">Описание…</p>
  <div class="area-tags">
    <span class="tag">Таг</span>
  </div>
  <a href="#" class="area-link">Разгледай <svg>→</svg></a>
</div>
```

**Career card** (salary + demand badge + progress bar):
```html
<div class="career-card reveal">
  <div class="career-card-header">
    <div class="career-icon-wrap"><svg>…</svg></div>
    <span class="career-demand demand-v-high">Най-търсено</span>
    <!-- demand classes: demand-high (green), demand-mid (amber), demand-v-high (blue) -->
  </div>
  <h3 class="career-title">Роля</h3>
  <div class="career-roles">Job title · Job title</div>
  <div class="career-salary">€X,XXX–X,XXX <span>EUR/мес · нето</span></div>
  <div class="career-bar"><div class="career-bar-fill" style="width:75%"></div></div>
  <div class="career-skills">
    <span class="tag">CERT</span>
  </div>
</div>
```

**Event card** (with `.featured` variant for dark navy bg):
```html
<div class="event-card [featured]">
  <div class="event-card-img">
    <div class="event-badge-wrap">
      <span class="event-type-badge">Тип</span>
    </div>
  </div>
  <div class="event-body">
    <div class="event-date">Дата</div>
    <h3 class="event-title">Събитие</h3>
    <div class="event-meta"><svg>…</svg> Локация</div>
    <p class="event-desc">Описание</p>
    <a href="#" class="event-cta">Научи повече <svg>→</svg></a>
  </div>
</div>
```

**Threat card** (dark bg, stat + description):
```html
<div class="threat-card reveal">
  <div class="threat-icon">🔒</div>
  <div class="threat-name">Тип заплаха</div>
  <div class="threat-stat">€12M</div>
  <div class="threat-stat-label">Контекст на статистиката</div>
  <p class="threat-desc">Описание…</p>
</div>
```

**Partner item** (footer partners grid):
```html
<a href="https://…" class="partner-item">
  <div class="partner-icon"><svg>…</svg></div>
  <div class="partner-name">Партньор</div>
  <div class="partner-type">Тип</div>
</a>
```

### Tags / Chips

```html
<span class="tag">CompTIA</span>           <!-- beige bg, brown text -->
<div class="company-chip">
  <span class="company-chip-dot"></span>
  AMATAS
</div>                                      <!-- white pill with blue dot -->
```

### Hero floating card

```html
<div class="hero-card">
  <div class="hero-card-icon"><svg>…</svg></div>
  <div class="hero-card-text">
    <span class="hero-card-title">Заглавие</span>
    <span class="hero-card-sub">Подзаглавие</span>
  </div>
</div>
```

**Important:** Hero cards must be **direct children of `.hero-visual`**, placed **after** the closing `</div>` of `.shield-container`. They are positioned absolute relative to `.hero-visual`, not `.shield-container`.

---

## Navigation structure

```
За нас
Ресурси ▾
  Директория: Организации · Личности · Форуми · Хаклор · Фишинг · Инструменти
  Учебни материали: Терминология · CTF · Книги · Видео ресурси
Обучение ▾
  Университетски програми · Онлайн курсове · Сертификации · Платформи
Кариера ▾
  Менторство · Компании · Обяви · Кариерен компас · Професионални пътеки · Заплати
Събития
Включи се  ← CTA button (class: nav-cta)
```

The mobile menu mirrors this structure exactly with accordion sub-sections.

---

## JavaScript patterns

### Dropdown toggle

```js
function toggleDropdown(id) {
  const item = document.getElementById(id);
  const isOpen = item.classList.contains('open');
  document.querySelectorAll('.has-dropdown').forEach(el => el.classList.remove('open'));
  if (!isOpen) item.classList.add('open');
}
// Close on outside click and Escape key — already wired in index.html
```

### Scroll reveal

Add class `reveal` (and optionally `reveal-delay-1` through `reveal-delay-4`) to any element.
The IntersectionObserver adds `.visible` when the element enters viewport.

```html
<div class="reveal reveal-delay-2">…</div>
```

### Navbar scroll effect

The `#navbar` element automatically gets class `.scrolled` after 60px scroll,
triggering backdrop-blur and stronger shadow.

### Counter animation

Stat elements with class `.stat-number` containing a plain integer auto-animate
when the `.hero-stats` block enters the viewport.

### Career bar animation

`.career-bar-fill` elements with inline `style="width:XX%"` animate from 0 to target
when `.careers-grid` enters the viewport.

### Marquee (companies strip)

```html
<div class="companies-marquee-wrap">
  <div class="companies-marquee" id="marquee">
    <!-- items × 2 for seamless loop -->
  </div>
</div>
```
Animation pauses on hover. Items must be duplicated to fill the loop.

---

## Page sections — order in index.html

1. `<nav class="navbar">` — fixed, z-index 1000
2. `#mobile-menu` — fixed below navbar on mobile
3. `<section class="hero">` — full-viewport, navy bg
4. `<div class="mission-strip">` — 3-column dark band
5. `<section class="areas">` — 4-card grid, beige bg
6. `<section class="events">` — 3-column event cards, cream bg
7. `<section class="careers">` — 6-card grid, beige bg
8. `<section class="threats">` — 4-card grid, navy bg
9. `<section class="companies">` — marquee strip, cream bg
10. `<div class="mentor-band">` — full-width CTA gradient band
11. `<section class="partners-section">` — partner logos, beige bg
12. `<footer>` — 4-column, espresso bg

**Background alternation pattern:** navy → beige → cream → beige → navy → cream → navy → beige → espresso

---

## Adding a new page

1. Copy `index.html` as starting template
2. Keep the `<head>` fonts import unchanged
3. Keep the entire `<nav>` and `#mobile-menu` blocks unchanged (they are identical across all pages)
4. Keep the `<footer>` block unchanged
5. Replace only the content between mission-strip and partners-section
6. Add `class="active"` to the relevant nav `<a>` for current-page highlighting

---

## Informational page format

Inner pages (e.g. organizacii.html) follow an **article-style** layout with no hero section.
Use this format for all resource, directory, and informational pages.

### Page skeleton

```html
<div class="page-content">          <!-- padding-top: 68px to clear fixed navbar -->
  <div class="article-section">     <!-- max-width: 1280px, margin: 0 auto, padding: 3.5rem 2rem 2rem -->

    <!-- 1. Breadcrumb -->
    <nav class="breadcrumb reveal">
      <a href="index.html">Начало</a>
      <svg>…chevron-right…</svg>
      <span>Раздел</span>
      <svg>…chevron-right…</svg>
      <span class="current">Текуща страница</span>
    </nav>

    <!-- 2. Article header (no hero, goes directly here) -->
    <div class="article-header reveal">
      <h1>Заглавие на <em>акцент</em></h1>       <!-- em tag → color: var(--blue) -->
      <p class="article-lead">Кратко описание…</p>  <!-- max-width: 720px -->
    </div>

    <!-- 3. Repeating category blocks -->
    <div class="section-divider"></div>           <!-- 1px sand line, margin 2.5rem 0 -->

    <div class="category-heading reveal">
      <div class="cat-icon"><svg>…</svg></div>    <!-- 40×40 navy square, white icon -->
      <h2>Име на категория</h2>
    </div>
    <p class="category-desc reveal">Описание…</p>

    <div class="org-grid">                        <!-- auto-fill, minmax(340px, 1fr) -->
      <div class="org-card reveal [reveal-delay-N]">
        <div class="org-card-header">
          <div class="org-name">Име</div>
          <span class="org-type-badge badge-ngo">Тип</span>
        </div>
        <p class="org-desc">Описание…</p>
        <div class="org-meta">
          <span class="org-meta-item"><svg>…</svg> ЕИК 123456789</span>
        </div>
        <div class="org-links">
          <a href="…" class="org-link"><svg>…</svg> website.bg</a>
        </div>
      </div>
    </div>

    <!-- 4. Optional info callout at the end -->
    <div class="info-callout reveal">
      <svg>…info-circle…</svg>
      <p><strong>Заглавие</strong> Текст с призив за допълване…</p>
    </div>

  </div>
</div>

<!-- 5. Below article: mentor-band → partners-section → footer (identical to index.html) -->
```

### Key components

**Breadcrumb** (`nav.breadcrumb`): flex row, `--fs-sm`, links in `--blue`, chevron-right SVG separators, `.current` span in `--espresso`.

**Article header** (`div.article-header`): `h1` uses `clamp(2rem, 4vw, --fs-3xl)`, `<em>` in `--blue` italic. `.article-lead` is `--fs-md`, `--brown`, `max-width: 720px`.

**Category heading** (`div.category-heading`): flex row with `.cat-icon` (40px navy square with white SVG) + `h2` in `--fs-2xl`.

**Organization card** (`div.org-card`): white bg, sand border, `--radius-lg`, flex column. Hover lifts 2px + shadow + sky-light border. Contains:
- `.org-card-header` — flex between name + badge
- `.org-name` — Cormorant Garamond `--fs-lg` bold navy
- `.org-type-badge` — pill badge, variants: `.badge-ngo` (blue), `.badge-gov` (royal), `.badge-eu` (sky), `.badge-community` (bark)
- `.org-desc` — `--fs-sm`, `--brown`, weight 300
- `.org-meta` — flex wrap of `.org-meta-item` chips (beige bg, `--fs-xs`, small SVG icon + text)
- `.org-links` — flex wrap of `.org-link` buttons (blue border pill, hover fills blue)

**Info callout** (`div.info-callout`): beige bg, sand border, 4px blue left border. Info SVG + paragraph. Use `<strong>` for emphasis and inline `<a>` for links.

**People links** (`div.org-people`): flex wrap of `.org-person` links inside org-cards. Each links to a LinkedIn profile with a person SVG icon. Used in organizacii.html to show key people per organization.

---

## Dynamic table pages (kompanii.html, lichnosti.html)

These pages use a **filterable table** pattern with sticky filter bar and chip-based filters.

### SEO: Inline HTML requirement

**Critical:** All table data must be rendered as **inline HTML `<tr>` rows** in the `<tbody>`, not generated by JavaScript. Search engines cannot execute JS, so content rendered via JS arrays + DOM injection is invisible to crawlers.

- `lichnosti.html` — **already migrated** to inline `<tr>` rows. JS is only used for filtering/searching the pre-rendered rows.
- `kompanii.html` — still uses a JS `const COMPANIES` array with `renderTable()`. **Should be migrated** to inline HTML in the future.

When adding new entries to `lichnosti.html`, insert `<tr>` rows directly in the HTML with `data-role`, `data-name`, and `data-search` attributes. Keep rows sorted A-Z by Bulgarian Cyrillic first name.

### Periodic update workflow (lichnosti.html)

When performing a bulk update of the people directory:
1. Visit each person's LinkedIn profile to verify their **current job title and company**
2. Update the title (`col-title`) and association (`col-assoc`) cells if they've changed roles
3. Update the `data-search` attribute to match the new content
4. Keep the sort order A-Z by Cyrillic first name
5. Remove people who are no longer active in the Bulgarian cybersecurity community

### Data structure (kompanii.html — legacy JS pattern)

```js
const COMPANIES = [
  { name: 'Company', size: 'Малка', category: 'Услуги', origin: 'Българска', focus: 'Description', url: 'https://...' },
];
```

### lichnosti.html — inline row format

```html
<tr data-role="Лидер" data-name="име фамилия" data-search="име фамилия title association">
  <td><div class="company-name-cell"><span class="company-name"><a href="LINKEDIN_URL" target="_blank" rel="noopener" style="color:var(--navy);text-decoration:none;border-bottom:1px solid var(--sand);transition:border-color 0.2s">Име Фамилия</a></span></div></td>
  <td class="col-title" style="color:var(--brown);font-weight:300;font-size:var(--fs-sm)">Title / Role</td>
  <td class="col-assoc" style="color:var(--brown);font-weight:400;font-size:var(--fs-sm)">Company / Organization</td>
  <td><span class="badge badge-leader">Лидер</span></td>
  <td><a href="LINKEDIN_URL" target="_blank" rel="noopener noreferrer" class="site-link"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>LinkedIn</a></td>
</tr>
```

### lichnosti.html — role categories

| Role | Badge class | Description |
|------|------------|-------------|
| `Лидер` | `.badge-leader` | Organization leaders, CISOs, CEOs, board members |
| `Организатор` | `.badge-organizer` | Event and community organizers |
| `Експерт` | `.badge-expert` | Consultants, researchers, speakers, advisors |
| `Държавен` | `.badge-gov` | Government officials, policy experts, national coordinators |

### kompanii.html — filter dimensions

- **Категория:** Услуги, Продукт, Дистрибуция, Обучения
- **Произход:** Българска, Международна
- **Размер:** Малка (≤50), Средна (50–500), Голяма (500+)

### Pattern: adding new entries

**lichnosti.html (inline HTML):**
1. Create a new `<tr>` row using the inline row format above
2. Insert it in the correct A-Z sorted position in the `<tbody>`
3. The JS filter/search works automatically on the pre-rendered rows
4. Names link to LinkedIn in both the name cell and the profile column

**kompanii.html (legacy JS):**
1. Add the object to the `const COMPANIES` array in the appropriate comment section
2. The table re-renders automatically — no HTML changes needed
3. The results counter updates via `applyFilters()`

### Navigation links for inner pages

All `href` values in the navbar, mobile menu, and footer must be prefixed with `index.html` when on a subpage (e.g. `index.html#about` instead of `#about`). The logo links to `index.html`. The "Организации" link points to `organizacii.html`.

### Footer structure for inner pages

Everything below and including the `.mentor-band` is the shared footer block. For inner pages, copy this exact sequence:
1. `div.mentor-band#mentoring` — mentoring CTA gradient band
2. `section.partners-section#partners` — partner logos grid
3. `<footer>` — 4-column footer with socials, links, legal

### Responsive behavior

- At 640px: `.org-grid` collapses to 1 column, article padding reduces
- At 860px: desktop nav hidden, hamburger shown
- At 1100px: footer grid becomes 2 columns

---

## File structure

```
csf-bg/
├── index.html            ← Homepage
├── za-nas.html           ← About page
├── organizacii.html      ← Organizations directory (cards with people links)
├── lichnosti.html        ← People directory (inline HTML table, JS filtering only)
├── kompanii.html         ← Companies directory (dynamic JS table, filterable)
├── forumi.html           ← Forums & communities
├── haklor.html           ← Threat awareness (Haklor)
├── phishing.html         ← Phishing awareness
├── instrumenti.html      ← Tools directory
├── terminologiq.html     ← Terminology glossary
├── ctf.html              ← CTF resources
├── knigi.html            ← Books directory
├── video.html            ← Video resources
├── universiteti.html     ← University programmes
├── kursove.html          ← Online courses
├── sertifikacii.html     ← Certifications
├── platformi.html        ← Learning platforms
├── mentoring.html        ← Mentoring programme
├── obqvi.html            ← Job listings
├── compass.html          ← Career compass
├── profesionalni-pateki.html ← Career paths
├── zaplati.html          ← Salary data
├── sabitia.html          ← Events
├── logo_csf.png
├── README.md
├── SKILL.md
└── .claude/
    └── launch.json       ← Dev server config (python3 http.server :8080)
```

All inner pages sit flat in the root directory (no subdirectories).

---

## Content rules

- **All salaries in EUR** (never BGN). Format: `€X,XXX–X,XXX EUR/мес · нето`
- **Primary language: Bulgarian.** English reserved for technical terms and international org names
- **Stats must be real and sourced** — from CERT.BG, cybercrime.bg, ENISA, or the job market research gist
- **Company directory:** 55+ entries — Bulgarian firms + international with BG offices
- **Career paths:** 6 tracks (Имплементиране, Опериране, Риск, Тестване, Анализ, Лидерство)
- **Partners footer:** XaKeP.bg, CyberSecurityTalks.bg, Cybercrime.bg, BSides Sofia, ISSA Bulgaria, ISACA Sofia Chapter

---

## Known quirks

- The `.dropdown` `min-width` is 220px. For the Ресурси dropdown (7 items) set it to `260px` via inline style or extend the CSS if items wrap
- `.hero-visual` is hidden on mobile (`display:none` at 860px breakpoint) — hero cards are desktop-only
- The companies marquee requires items duplicated ×2 in the HTML for the CSS animation loop to be seamless
- `.career-bar-fill` width is set inline and animated by JS — do not set it in CSS
- `overflow-x: hidden` on `body` — do not add elements that intentionally extend beyond viewport width except the marquee wrapper
