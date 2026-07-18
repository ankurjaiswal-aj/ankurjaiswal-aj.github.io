# Personal website

Static site (plain HTML/CSS, no build step) for Ankur Jaiswal's academic homepage.

## Structure

- `index.html` — all page content, organized into anchor-linked sections
- `css/style.css` — all styling
- `assets/cv/` — downloadable CV PDF (linked from the "Download CV" button)

## Updating content

Edit `index.html` directly — each section (`#education`, `#research`, `#experience`,
`#publications`, `#awards`, `#skills`, `#contact`) is self-contained. To update the
downloadable CV, replace the PDF in `assets/cv/` and update the `href` in the
"Download CV" link in `index.html` if the filename changes.

## Previewing locally

Open `index.html` directly in a browser, or serve it locally:

```
python3 -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploying (GitHub Pages)

1. Push this repo to GitHub (e.g. `Ankur-Jaiswal-96.github.io` for a root personal
   site, or any repo name with Pages enabled on the `main` branch).
2. In the repo's Settings → Pages, set the source to the `main` branch, root folder.
3. The site will be live at the repo's Pages URL within a few minutes.
