# Fotos By Don — website source

A static, single-page marketing site. No build step — upload the folder as-is to any static host (Netlify, Vercel, GitHub Pages, cPanel, etc).

## Structure

```
index.html            Homepage (semantic HTML, SEO meta, JSON-LD)
404.html               Branded not-found page
robots.txt              Crawler rules + sitemap reference
sitemap.xml             XML sitemap (update <lastmod> when you edit the site)
site.webmanifest        PWA / home-screen icon manifest
favicon.ico             Legacy favicon fallback
css/
  style.css             All site styles
js/
  main.js               Hero aperture animation, scroll parallax,
                         card reveals, and the click-to-expand lightbox
images/
  icons/                Favicons and touch icons, plus favicon.svg
  portfolio/             Photos, each exported as three files:
                          *-thumb.jpg / .webp / .avif  (grid, ~760px, lazy-loaded)
                          *-large.jpg / .webp           (lightbox, ~1500px)
```

## Before you publish — replace these placeholders

The domain used throughout (`https://www.fotosbydon.co.bw/`) is a placeholder.
Search the project for it and replace with your real domain once you have one:

- `index.html` — canonical link, Open Graph/Twitter tags, JSON-LD `url`/`image`
- `404.html` — canonical link
- `robots.txt` — Sitemap line
- `sitemap.xml` — `<loc>`

Also:
- **Google Search Console** — `index.html` has a placeholder
  `<meta name="google-site-verification" content="REPLACE_WITH_YOUR_VERIFICATION_CODE">`.
  Verify the domain in Search Console (Settings → Ownership verification → HTML tag),
  paste the code it gives you into that `content` value, then submit
  `sitemap.xml` from the Sitemaps section once the site is live.

## Notes on the images

Each photo has AVIF, WebP, and JPEG versions; the `<picture>` elements let
the browser pick the smallest format it supports, and browsers that don't
support `<picture>` fall back to the plain `.jpg`. Grid photos use
`loading="lazy"`; the four "featured" photos near the top load eagerly since
they're visible on load. Clicking any gallery photo opens it larger in a
lightbox (`js/main.js`), pulling from the `*-large` files.

## Local preview

Any static server works, e.g. from this folder:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.
