# Static Site Conversion - Summary

## CAN BE REMOVED (Backend)

### Complete Directory
- `backend/` - Entire Django backend directory including:
  - Django project files (`krapesto_backend/`)
  - Django apps (`menu/`, `bar/`, `kitchen/`, `inventory/`)
  - Python scripts (`*.py`)
  - Batch scripts (`*.bat`)
  - Django templates and static files
  - Database migrations
  - Django documentation (`*.md` files)

### Root-Level Django Documentation
- `DJANGO_SETUP.md`
- `INTEGRATION_GUIDE.md`

---

## CAN BE REMOVED (Build Tools / Frameworks)

### Next.js Configuration
- `next.config.mjs`
- `tsconfig.json`
- `postcss.config.mjs`
- `components.json`

### Package Management
- `package.json`
- `package-lock.json`
- `pnpm-lock.yaml`
- `node_modules/` directory

### Build Scripts
- `build-and-start.bat`
- `start-dev.bat`

### Build Output Directories
- `.next/` (Next.js build output)
- `out/` (static export output)
- `build/` (build artifacts)

---

## MUST BE KEPT (Static Assets)

### Images and Icons
- `public/` directory - All image files:
  - `*.jpg` files (restaurant photos)
  - `*.png` files (icons, logos)
  - `*.svg` files (favicons, logos)
  - `*.ico` files (favicons)
  - `public/images/` subdirectory

**Specific files to preserve:**
- `favicon.ico`
- `favicon-k.svg`
- `favicon-k-32x32.png`
- `apple-icon.png`
- `icon-dark-32x32.png`
- `icon-light-32x32.png`
- `icon.svg`
- All restaurant interior/food images
- Logo files (`logo0.png`, `logo0-green.png`, etc.)

### CSS (After Compilation)
- `app/globals.css` - Needs Tailwind compilation to pure CSS
- `styles/globals.css` - (if different, needs compilation)

### Data Files (After Conversion)
- `lib/translations.ts` - Convert to JSON format
- `lib/menu-data.ts` - Static menu data (if keeping menu functionality)

---

## PROPOSED FINAL DIRECTORY STRUCTURE

```
krapesto-static/
├── index.html                          # Home page
├── about/
│   └── index.html
├── contact/
│   └── index.html
├── gallery/
│   └── index.html
├── menu/
│   ├── index.html
│   ├── drinks/
│   │   └── index.html
│   └── friday-pizza/
│       └── index.html
├── events/
│   ├── cocktail-degustation/
│   │   └── index.html
│   ├── family-events/
│   │   └── index.html
│   ├── kids-birthdays/
│   │   └── index.html
│   ├── pizza-education/
│   │   └── index.html
│   └── valgyk-kiek-telpa/
│       └── index.html
├── css/
│   └── styles.css                      # Compiled CSS
├── js/
│   ├── main.js                         # Main JavaScript
│   ├── language.js                     # Language switching
│   ├── theme.js                        # Theme switching (if keeping)
│   └── menu.js                         # Menu display (if keeping)
├── images/                             # All from public/
│   ├── [all .jpg files]
│   ├── [all .png files]
│   ├── [all .svg files]
│   └── images/
│       └── wood-texture.jpg
├── favicon.ico
├── favicon-k.svg
├── favicon-k-32x32.png
├── apple-icon.png
├── manifest.json                       # Converted from app/manifest.ts
├── robots.txt                          # Converted from app/robots.ts
└── sitemap.xml                         # Converted from app/sitemap.ts
```

---

## CRITICAL CONVERSION NOTES

### Files Requiring Conversion (Not Deletion)
- All `.tsx` files → Convert to `.html` or vanilla `.js`
- All `.ts` files → Convert to vanilla `.js` or `.json`
- `app/globals.css` → Compile Tailwind to pure CSS
- React components → Convert to vanilla JS or static HTML

### Key Functionality Decisions Needed
1. **Menu System:** Currently fetches from Django API - use static data or remove?
2. **Dynamic Routes:** `/menu/[date]` pages - remove or pre-generate?
3. **Language Switching:** Keep bilingual support with vanilla JS?
4. **Theme Toggle:** Keep dark/light mode with vanilla JS?

---

## FILE COUNT SUMMARY

- **Backend files to remove:** ~50+ files/directories
- **Build tool files to remove:** ~10+ files/directories  
- **Frontend files to convert:** ~100+ files
- **Static assets to keep:** ~20+ image files

---

**Full detailed audit available in:** `STATIC_SITE_AUDIT.md`

