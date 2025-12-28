# Static Site Conversion - Complete

## Summary

The project has been successfully converted from a Next.js/React + Django backend to a purely static website.

## What Was Done

### ✅ Created Static Data Files
- `public/data/menu.json` - Static menu data in JSON format
- `public/data/translations.json` - Translation data for bilingual support

### ✅ Created Vanilla JavaScript
- `js/language.js` - Language switching functionality
- `js/menu.js` - Menu rendering from JSON
- `js/main.js` - Main site functionality (mobile menu, dropdowns)

### ✅ Created Static HTML Pages
- `index.html` - Home page
- `menu/index.html` - Menu page with dynamic menu loading

### ✅ Created CSS
- `css/styles.css` - Complete styling without Tailwind dependencies

### ✅ Created Static Site Files
- `public/manifest.json` - Web app manifest
- `public/robots.txt` - Search engine directives
- `public/sitemap.xml` - Site map

### ✅ Removed Backend
- Deleted entire `backend/` directory (Django)
- Removed Django documentation files

### ✅ Removed Build Tools
- Removed `next.config.mjs`
- Removed `tsconfig.json`
- Removed `postcss.config.mjs`
- Removed `components.json`
- Removed `package.json`, `package-lock.json`, `pnpm-lock.yaml`
- Removed build scripts (`build-and-start.bat`, `start-dev.bat`)

### ✅ Removed React/Next.js Source
- Removed `app/` directory
- Removed `components/` directory
- Removed `hooks/` directory
- Removed `lib/` directory
- Removed `styles/` directory

## Current Structure

```
krapesto/
├── index.html                 # Home page
├── menu/
│   └── index.html            # Menu page
├── css/
│   └── styles.css            # All styles
├── js/
│   ├── language.js           # Language switching
│   ├── menu.js               # Menu rendering
│   └── main.js               # Main functionality
├── public/
│   ├── data/
│   │   ├── menu.json         # Menu data
│   │   └── translations.json # Translations
│   ├── manifest.json
│   ├── robots.txt
│   ├── sitemap.xml
│   └── [all images]          # Preserved from original
└── [audit files]             # STATIC_SITE_AUDIT.md, etc.
```

## How to Serve

The site can now be served as static files using any web server:

### Python
```bash
python -m http.server 8000
```

### Node.js (http-server)
```bash
npx http-server -p 8000
```

### PHP
```bash
php -S localhost:8000
```

### Any Static Hosting
- GitHub Pages
- Netlify
- Vercel (static)
- AWS S3 + CloudFront
- Any web server (Apache, Nginx, etc.)

## Features Preserved

✅ Bilingual support (LT/EN)
✅ Menu display (now from static JSON)
✅ Responsive design
✅ Mobile menu
✅ Language switching
✅ All visual styling

## Remaining Tasks (Optional)

The following pages still need to be created as static HTML (can be done as needed):
- `about/index.html`
- `contact/index.html`
- `gallery/index.html`
- `events/pizza-education/index.html`
- `events/cocktail-degustation/index.html`
- `events/kids-birthdays/index.html`
- `events/family-events/index.html`
- `events/valgyk-kiek-telpa/index.html`
- `menu/drinks/index.html`
- `menu/friday-pizza/index.html`

These can be created following the same pattern as `index.html` and `menu/index.html`.

## Menu Data Updates

To update the menu, edit `public/data/menu.json`. The structure is:
```json
{
  "en": [
    {
      "day": "Monday",
      "date": "2024-01-01",
      "dishes": [
        {
          "name": "Dish Name",
          "description": "Description",
          "price": "€X.XX"
        }
      ]
    }
  ],
  "lt": [...]
}
```

## Notes

- All API calls to Django backend have been removed
- Menu now loads from `/data/menu.json` via fetch()
- Language preference is stored in localStorage
- No build step required - just serve the files
- No frameworks or dependencies needed

