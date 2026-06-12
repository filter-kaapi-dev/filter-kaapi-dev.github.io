# How to Rate Your Neighborhood

A simple, static GitHub Pages site exported from the original Notion page.
Live at: **https://filter-kaapi-dev.github.io**

No build step, no framework, no JavaScript. Just three files.

## Files

| File              | What it is                                                        |
| ----------------- | ----------------------------------------------------------------- |
| `index.html`      | All the page **content** (text, toggles, lists, links).           |
| `styles.css`      | All the **design** (fonts, colors, layout). Edit here for looks.  |
| `assets/qr-code.png` | The "Rate Your Hood" survey QR image.                          |
| `.nojekyll`       | Tells GitHub Pages to serve the files as-is. Leave it alone.      |

---

## How to edit

### 1. Change colors, fonts, or layout
Open **`styles.css`** and edit the values in the `:root { … }` block at the very top.
Change a value once there and it updates everywhere.

| What you want to change            | Variable to edit         | Example                          |
| ---------------------------------- | ------------------------ | -------------------------------- |
| Body text color                    | `--color-text`           | `#37352f` → `#222222`            |
| Page background                    | `--color-bg`             | `#ffffff` → `#fafafa`            |
| Link / accent color (the purple)   | `--color-accent`         | `#3b2f8f` → `#0b6e4f`            |
| Grey callout box background        | `--color-callout-bg`     | `#f1f1ef` → `#fff4e5`            |
| Font for everything                | `--font-body`            | see "Using a custom font" below  |
| Base text size                     | `--font-size-body`       | `16px` → `18px`                  |
| Big title size                     | `--font-size-title`      | `40px` → `48px`                  |
| Line spacing                       | `--line-height`          | `1.6` → `1.8`                    |
| Width of the reading column        | `--content-width`        | `720px` → `820px`                |

Colors accept any CSS color: hex (`#3b2f8f`), `rgb(...)`, or names (`navy`).

#### Using a custom (Google) font
The site currently uses the system font stack (same neutral look as Notion, loads instantly).
To use a custom font instead, e.g. **Inter**:

1. Add this line inside `<head>` in `index.html`, above the existing `styles.css` link:
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
   ```
2. In `styles.css`, change:
   ```css
   --font-body: "Inter", ui-sans-serif, -apple-system, sans-serif;
   ```

### 2. Change the words
Open **`index.html`**. Each section is a labelled block, e.g.:

```html
<!-- ===== What is this? ===== -->
<details>
  <summary><span class="summary-emoji">⭐</span> What is this?</summary>
  <div class="toggle-content">
    <p>Your paragraph text goes here…</p>
  </div>
</details>
```

- A collapsible section = `<details>`. The clickable heading = `<summary>`.
- A paragraph = `<p>…</p>`.
- A numbered list = `<ol>` with `<li>…</li>` items.
- A grey highlight box = the `<div class="callout">…</div>` block.
- A link = `<a href="https://...">visible text</a>`.

### 3. Replace the placeholders
The original page had a few `[INSERT LINK]` / `[Insert link here]` / `[Insert Tutorial Video]`
markers. Search `index.html` for `[Insert` and swap them for real links when ready, e.g.:
```html
made public! <a href="https://filter-kaapi-dev.github.io/data">see the data</a>
```

### 4. Replace the QR code
Drop a new image at `assets/qr-code.png` (same name), or change the filename in this line of
`index.html`:
```html
<img class="qr" src="assets/qr-code.png" alt="...">
```
Adjust its on-screen size with `.qr { width: 240px; }` in `styles.css`.

---

## Preview locally
Just double-click `index.html` to open it in a browser. No server needed.
(Optional: `python -m http.server` then visit `http://localhost:8000`.)

## Publish
Commit and push to the `main` branch. GitHub Pages for a `*.github.io` repo serves the
`main` branch root automatically — your changes go live in a minute or two.
(Repo → Settings → Pages should show Source = `main` / `/root`.)
