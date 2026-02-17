# MBAR - McKnight Brain Aging Registry

The McKnight Brain Aging Registry (MBAR) is a website for researchers affiliated with the four McKnight Brain Research Foundation Institutes. Researchers who are part of those institutes can apply for access to the datasets.

- **GitHub Pages**: [https://uab-it.github.io/mbar/](https://uab-it.github.io/mbar/)
- **Netlify**: [https://mbar.netlify.app/](https://mbar.netlify.app/)

### Data Files

- [https://uab.box.com/v/mbarstudywebsite](https://uab.box.com/v/mbarstudywebsite)
- [https://uab.box.com/v/MBAR-data-dictionary](https://uab.box.com/v/MBAR-data-dictionary)

---

## Architecture

A static site using [htmx](https://htmx.org/) for client-side page loading and [Tailwind CSS](https://tailwindcss.com/) (CDN v2.2.19) for styling. No build step, bundler, or package manager.

- `index.html` — Main entry point and shell (header, footer, nav, banner)
- `pages/` — Content fragments loaded dynamically via htmx into the main content area
- `404.html` — Catch-all for GitHub Pages SPA routing
- `netlify.toml` — Rewrite rules for clean URL routing on Netlify
- `images/` — Static image assets (logos, photos)

## Development

Open `index.html` in a browser or use any static file server:

```
python3 -m http.server
```

## Deployment

- **GitHub Pages** deploys automatically from the `main` branch
- **Netlify** uses `netlify.toml` for SPA rewrite rules; deploy via `netlify deploy --dir=. --prod`
