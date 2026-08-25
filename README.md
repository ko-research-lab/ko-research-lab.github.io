# Ko Research Lab — Website

Static website for the **Ko Research Lab** at The University of Texas at Tyler
(Department of Civil & Construction Engineering and Management), led by
**Minhyeok Ko**.

**AI, Uncertainty, and Intelligent Infrastructure Systems.**

The site is intentionally simple: plain **HTML**, one **CSS** file, and a tiny
bit of **vanilla JavaScript** (only for the mobile menu). There is **no build
system, no framework, and no backend** — it works as-is on GitHub Pages.

---

## Repository structure

```text
/
├── index.html          # Home
├── research.html       # Research overview
├── people.html         # People (PI, students, alumni)
├── publications.html   # Publication list
├── news.html           # News
├── join.html           # Join Us
├── css/
│   └── style.css       # All styling (edit design tokens at the top)
├── js/
│   └── main.js         # Mobile navigation toggle only
├── assets/
│   ├── logo/           # Lab / university logos
│   ├── people/         # Member photos
│   └── research/       # Research & hero images
├── .nojekyll           # Tells GitHub Pages to serve files as-is
└── README.md
```

---

## 1. Preview the website locally

No tools are required — just open the files.

- **Simplest:** double-click `index.html` to open it in your browser.
- **Recommended (so paths behave exactly like the live site):** run a tiny local
  server from the project folder.

If you have Python installed:

```bash
python -m http.server 8000
```

Then visit <http://localhost:8000> in your browser. Press `Ctrl+C` to stop.

---

## 2. How to edit content

All content lives directly in the `.html` files as plain text. Open a page in
any text editor, find the text you want to change, edit it, and save. Look for
`<!-- comments -->` in each file — they mark where and how to add new items.

> **Note:** The navigation bar and footer are copied into every page. If you
> change a nav link or footer text, update it in **all** HTML files to keep them
> consistent.

Colors, fonts, and spacing are controlled by the variables at the top of
`css/style.css` (the `:root { ... }` block). For example, change
`--color-accent` to adjust the burnt-orange accent everywhere at once.

---

## 3. How to add a person

Open `people.html`. Each person uses a small `.person` block. A ready-to-copy
template is included as a comment in the file. Basic steps:

1. Add a photo to `assets/people/` (e.g. `jane-doe.jpg`). Square images work
   best.
2. In the appropriate group (Graduate Students, Undergraduate Researchers, or
   Alumni), paste a copy of this block:

```html
<div class="person">
  <img class="person-photo" src="assets/people/jane-doe.jpg" alt="Jane Doe">
  <h3>Jane Doe</h3>
  <p class="person-title">Ph.D. Student</p>
  <p class="person-interests">Research interests: ...</p>
  <p class="person-links">
    <a href="#">Website</a>
    <a href="#">Scholar</a>
    <a href="#">GitHub</a>
    <a href="#">LinkedIn</a>
  </p>
</div>
```

3. Make sure each `.person` block sits inside a `<div class="person-grid"> ...
   </div>` wrapper (the grid arranges cards in columns).
4. Delete any links (Website / Scholar / GitHub / LinkedIn) that do not apply.

---

## 4. How to add a publication

Open `publications.html`. Publications are grouped by year with
`<h2 class="year-heading">`. To add one:

1. Find the correct year heading, or add a new one for a new year.
2. Inside that year's `<ul class="pub-list">`, paste:

```html
<li class="pub">
  <p class="pub-title">Paper title goes here</p>
  <p class="pub-authors"><span class="me">Minhyeok Ko</span>, Coauthor A, Coauthor B</p>
  <p class="pub-venue">Journal or Conference Name, Year</p>
  <p class="pub-links">
    <a href="#">PDF</a>
    <a href="#">DOI</a>
    <a href="#">arXiv</a>
    <a href="#">Code</a>
    <a href="#">Project</a>
  </p>
</li>
```

3. Wrap the PI's name in `<span class="me">Minhyeok Ko</span>` so it is
   highlighted in the author list.
4. Keep only the links that exist; delete the rest.

---

## 5. How to add a news item

Open `news.html`. Add a new `<li>` at the **top** of the `<ul class="news-list">`
(newest first):

```html
<li>
  <span class="news-date">Sep 2026</span>
  <span class="news-text">Your news text here. Links are fine: <a href="#">link</a>.</span>
</li>
```

Optionally, mirror the newest item in the "Recent News" section of
`index.html`.

---

## 6. How to deploy through GitHub Pages

This repository is named to be served directly by GitHub Pages.

1. Commit and push your changes to the `main` branch.
2. On GitHub, go to the repository's **Settings → Pages**.
3. Under **Build and deployment**:
   - **Source:** *Deploy from a branch*
   - **Branch:** `main` and folder `/ (root)`
   - Click **Save**.
4. Wait a minute, then visit your site. For a repository named
   `<username>.github.io`, the URL is `https://<username>.github.io/`.

The included `.nojekyll` file tells GitHub Pages to serve the files exactly as
they are (no Jekyll processing needed).

---

## Design notes

- **Max content width:** ~1100px, with generous whitespace.
- **Colors:** white background, near-black navy text, a subtle burnt-orange
  accent (UT Tyler inspired), and a muted blue/teal used sparingly.
- **Fonts:** system sans-serif stack (no external font downloads).
- **Philosophy:** clean, readable, research-focused, and easy to maintain by
  hand. Prefer the simplest change that works.
