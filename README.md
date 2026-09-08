# Portfolio site

A minimal static portfolio: an about/index page linking out to individual
project pages, each embedding a PDF with a link back to the homepage.

## Structure

```
index.html              ← homepage: about section + list of project links
assets/style.css         ← all styling
projects/project-1.html  ← project page, embeds pdfs/project-1.pdf
projects/project-2.html
projects/project-3.html
pdfs/                     ← put your actual PDF files here
```

## Customize

1. **Edit `index.html`**
   - Replace `Your Name`, job title, bio, and contact links in the `.hero` section.
   - Replace each `.file` entry's title/description, and its `href`
     (e.g. `projects/project-1.html`).

2. **Add your PDFs**
   - Drop your PDF files into `pdfs/`, e.g. `pdfs/project-1.pdf`.

3. **Edit each project page** (`projects/project-1.html`, etc.)
   - Update the `<title>`, the doc number/title in the header, and the
     `src="../pdfs/project-1.pdf"` path to match your PDF filename.

4. **Add more project pages**
   - Copy `projects/project-1.html` to e.g. `projects/project-4.html`,
     update its title, doc number, and PDF path.
   - Add a matching `.file` entry in `index.html`.

## Run it locally

No build step needed — it's plain HTML/CSS. To preview with correct
relative paths, serve it rather than opening the file directly:

```
cd portfolio-site
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploy with GitHub Pages

1. Create a new GitHub repo (public), e.g. `yourname.github.io` for a
   root user site, or any name for a project site.
2. Push these files to the repo root:
   ```
   git init
   git add .
   git commit -m "Initial portfolio"
   git branch -M main
   git remote add origin https://github.com/yourusername/your-repo.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Build and deployment →
   Source**, select **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Your site will be live at:
   - `https://yourusername.github.io/` (if the repo is named `yourusername.github.io`), or
   - `https://yourusername.github.io/your-repo/` (any other repo name).
5. Link this URL from your CV.

## Notes

- PDFs are embedded via `<iframe>`. Most desktop browsers render this fine;
  some mobile browsers don't render embedded PDFs and will show the
  fallback "open it directly" link instead — this is expected and handled.
- Keep PDF file sizes reasonable (a few MB) so pages load quickly.
- Fonts (Fraunces, Inter, IBM Plex Mono) load from Google Fonts via CDN,
  so an internet connection is needed to see them styled as intended;
  they fall back to system fonts otherwise.
