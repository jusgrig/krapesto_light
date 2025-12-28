# Static Site Conversion Audit Report

## Executive Summary

This project is a Next.js/React frontend with a Django backend. The frontend makes API calls to Django for dynamic menu data. To convert to a purely static website, we need to:

1. **Remove** all Django backend code
2. **Remove** Next.js build-time dependencies and framework
3. **Extract** static assets (HTML, CSS, JS, images)
4. **Replace** dynamic API calls with static data or remove dynamic features

---

## 1. BACKEND-RELATED FILES (Can be Removed)

### Django Backend Directory (`backend/`)
**Status:** ✅ **CAN BE REMOVED** - Entire directory

```
backend/
├── manage.py                          # Django management script
├── requirements.txt                   # Python dependencies
├── krapesto_backend/                  # Django project settings
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── menu/                              # Django menu app
│   ├── models.py                      # Database models
│   ├── views.py                       # API views
│   ├── serializers.py                 # API serializers
│   ├── urls.py                        # API URL routing
│   ├── user_views.py                  # User-facing views
│   ├── user_urls.py                   # User URL routing
│   ├── admin.py                       # Django admin config
│   ├── forms.py                       # Django forms
│   ├── context_processors.py          # Template context
│   ├── templatetags/                  # Django template tags
│   ├── templates/                     # Django HTML templates
│   └── migrations/                    # Database migrations
├── bar/                               # Django bar app
├── kitchen/                           # Django kitchen app
├── inventory/                         # Django inventory app
├── static/                            # Django static files (admin)
├── templates/                         # Django templates
├── *.py                               # Python utility scripts
├── *.bat                              # Windows batch scripts for Django
└── *.md                               # Django documentation
```

**Files:**
- `backend/manage.py`
- `backend/requirements.txt`
- `backend/check-menus.py`
- `backend/check-server.bat`
- `backend/create-admin.bat`
- `backend/create-blue-favicon.py`
- `backend/create-default-admin.py`
- `backend/create-drinks-subcategories.py`
- `backend/create-tomorrow-menu.py`
- `backend/setup-django.bat`
- `backend/start-django.bat`
- `backend/test-admin-access.py`
- `backend/ADMIN_USER_SEPARATION.md`
- `backend/API_EXAMPLES.md`
- `backend/PERMISSIONS_GUIDE.md`
- `backend/QUICK_START.md`
- `backend/README.md`

### Root-Level Django Documentation
- `DJANGO_SETUP.md`
- `INTEGRATION_GUIDE.md`

---

## 2. NEXT.JS / REACT / BUILD-TOOL DEPENDENCIES (Can be Removed)

### Next.js Configuration Files
**Status:** ✅ **CAN BE REMOVED** - Build-time only

- `next.config.mjs` - Next.js configuration
- `tsconfig.json` - TypeScript configuration (build-time)
- `postcss.config.mjs` - PostCSS configuration (build-time)
- `components.json` - shadcn/ui configuration (build-time)

### Package Management Files
**Status:** ✅ **CAN BE REMOVED** - Build dependencies

- `package.json` - Node.js dependencies
- `package-lock.json` - Lock file
- `pnpm-lock.yaml` - pnpm lock file

### Build Scripts
**Status:** ✅ **CAN BE REMOVED** - Build automation

- `build-and-start.bat` - Build and start script
- `start-dev.bat` - Development server script

### Next.js App Router Files (Need Conversion)
**Status:** ⚠️ **NEED CONVERSION** - Convert to static HTML

These files use Next.js features but can be converted to static HTML:

#### Server-Side Metadata Files (Need Static Conversion)
- `app/manifest.ts` → Convert to `public/manifest.json`
- `app/robots.ts` → Convert to `public/robots.txt`
- `app/sitemap.ts` → Convert to `public/sitemap.xml`

#### Page Files (Need Static HTML Conversion)
- `app/page.tsx` → Convert to `index.html`
- `app/about/page.tsx` → Convert to `about/index.html`
- `app/about/layout.tsx` → Merge metadata into HTML
- `app/contact/page.tsx` → Convert to `contact/index.html`
- `app/contact/layout.tsx` → Merge metadata into HTML
- `app/gallery/page.tsx` → Convert to `gallery/index.html`
- `app/gallery/layout.tsx` → Merge metadata into HTML
- `app/menu/page.tsx` → Convert to `menu/index.html`
- `app/menu/layout.tsx` → Merge metadata into HTML
- `app/menu/[date]/page.tsx` → **PROBLEM:** Dynamic route - needs static pages or removal
- `app/menu/drinks/page.tsx` → Convert to `menu/drinks/index.html`
- `app/menu/friday-pizza/page.tsx` → Convert to `menu/friday-pizza/index.html`
- `app/events/cocktail-degustation/page.tsx` → Convert to `events/cocktail-degustation/index.html`
- `app/events/family-events/page.tsx` → Convert to `events/family-events/index.html`
- `app/events/kids-birthdays/page.tsx` → Convert to `events/kids-birthdays/index.html`
- `app/events/pizza-education/page.tsx` → Convert to `events/pizza-education/index.html`
- `app/events/valgyk-kiek-telpa/page.tsx` → Convert to `events/valgyk-kiek-telpa/index.html`

#### Root Layout
- `app/layout.tsx` → Convert to base HTML template
- `app/globals.css` → Keep as CSS (needs Tailwind compilation)

### Node Modules
**Status:** ✅ **CAN BE REMOVED** - Dependencies

- `node_modules/` - All npm packages

### Build Output Directories
**Status:** ✅ **CAN BE REMOVED** - Generated files

- `.next/` - Next.js build output
- `out/` - Static export output (if exists)
- `build/` - Build artifacts

---

## 3. MUST BE KEPT (Static Assets)

### Public Assets Directory (`public/`)
**Status:** ✅ **MUST KEEP** - Static files

```
public/
├── *.jpg, *.png, *.svg, *.ico        # All image files
└── images/                            # Image subdirectory
```

**Files to Keep:**
- All image files (`.jpg`, `.png`, `.svg`, `.ico`)
- Favicon files
- Logo files
- Placeholder images

### CSS Files
**Status:** ⚠️ **NEED PROCESSING** - Tailwind needs compilation

- `app/globals.css` - Contains Tailwind directives, needs compilation to pure CSS
- `styles/globals.css` - (if different from app/globals.css)

### JavaScript Components (Need Conversion)
**Status:** ⚠️ **NEED CONVERSION** - React components need vanilla JS or removal

#### Components Directory (`components/`)
- `components/header.tsx` → Convert to vanilla JS or static HTML
- `components/footer.tsx` → Convert to vanilla JS or static HTML
- `components/gallery-grid.tsx` → Convert to vanilla JS
- `components/event-card.tsx` → Convert to vanilla JS or static HTML
- `components/weekly-menu.tsx` → **CRITICAL:** Currently fetches from Django API - needs static data or removal
- `components/language-aware-layout.tsx` → Convert to vanilla JS
- `components/performance-hints.tsx` → Convert to vanilla JS or remove
- `components/structured-data.tsx` → Convert to static JSON-LD
- `components/theme-provider.tsx` → Convert to vanilla JS or remove
- `components/ui/` → All UI components need conversion or replacement

#### Hooks Directory (`hooks/`)
- `hooks/use-mobile.ts` → Convert to vanilla JS or remove
- `hooks/use-toast.ts` → Convert to vanilla JS or remove

#### Library Files (`lib/`)
- `lib/utils.ts` → Convert to vanilla JS
- `lib/translations.ts` → Keep as data source (convert to JSON)
- `lib/language-context.tsx` → Convert to vanilla JS
- `lib/seo.ts` → Convert to static meta tags
- `lib/menu-api.ts` → **REMOVE** - Django API calls
- `lib/menu-data.ts` → **KEEP** - Contains static menu data (deprecated but has data)

---

## 4. CRITICAL ISSUES FOR STATIC CONVERSION

### Issue 1: Dynamic Menu Data from Django API
**Location:** `lib/menu-api.ts`, `components/weekly-menu.tsx`, `app/menu/[date]/page.tsx`

**Problem:**
- `fetchTodayMenu()` - Calls Django API
- `fetchDateMenu()` - Calls Django API  
- `fetchWeekMenu()` - Calls Django API
- `getMenuData()` - Calls Django API

**Solution Options:**
1. **Use static data** from `lib/menu-data.ts` (already exists, marked deprecated)
2. **Remove menu functionality** entirely
3. **Pre-generate static HTML pages** for each menu date

### Issue 2: Dynamic Route `app/menu/[date]/page.tsx`
**Problem:** Next.js dynamic route that fetches menu by date from Django API

**Solution Options:**
1. **Remove** dynamic date pages
2. **Pre-generate** static HTML for specific dates
3. **Convert** to client-side routing with static data

### Issue 3: Next.js Image Optimization
**Location:** All pages using `next/image`

**Problem:** `next/image` component requires Next.js server

**Solution:** Replace with standard `<img>` tags

### Issue 4: Next.js Font Loading
**Location:** `app/layout.tsx` - `Geist` and `Geist_Mono` fonts

**Problem:** Next.js font optimization requires build-time processing

**Solution:** Use standard web fonts or self-hosted fonts

### Issue 5: Vercel Analytics
**Location:** `app/layout.tsx` - `@vercel/analytics`

**Problem:** Requires Next.js runtime

**Solution:** Remove or replace with static analytics script

### Issue 6: Client-Side Language Switching
**Location:** `lib/language-context.tsx`, `components/language-aware-layout.tsx`

**Problem:** React Context API requires JavaScript framework

**Solution:** Convert to vanilla JavaScript with localStorage or URL parameters

### Issue 7: Theme Provider (Dark/Light Mode)
**Location:** `components/theme-provider.tsx`

**Problem:** React Context API

**Solution:** Convert to vanilla JavaScript

---

## 5. PROPOSED STATIC DIRECTORY STRUCTURE

```
krapesto-static/
├── index.html                          # Home page (from app/page.tsx)
├── about/
│   └── index.html                      # About page
├── contact/
│   └── index.html                      # Contact page
├── gallery/
│   └── index.html                      # Gallery page
├── menu/
│   ├── index.html                      # Menu page
│   ├── drinks/
│   │   └── index.html                  # Drinks page
│   └── friday-pizza/
│       └── index.html                  # Friday pizza page
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
│   └── styles.css                      # Compiled CSS (from Tailwind)
├── js/
│   ├── main.js                         # Main JavaScript
│   ├── language.js                     # Language switching
│   ├── theme.js                        # Theme switching
│   └── menu.js                         # Menu display (if keeping)
├── images/                             # All images from public/
│   ├── *.jpg
│   ├── *.png
│   └── *.svg
├── favicon.ico
├── favicon-k.svg
├── favicon-k-32x32.png
├── apple-icon.png
├── manifest.json                       # Converted from app/manifest.ts
├── robots.txt                          # Converted from app/robots.ts
├── sitemap.xml                         # Converted from app/sitemap.ts
└── data/
    └── translations.json               # Converted from lib/translations.ts
```

---

## 6. SUMMARY BY CATEGORY

### ✅ CAN BE REMOVED (Backend)

**Complete Directory:**
- `backend/` - Entire Django backend

**Documentation:**
- `DJANGO_SETUP.md`
- `INTEGRATION_GUIDE.md`

**Total:** ~50+ files/directories

---

### ✅ CAN BE REMOVED (Build Tools / Frameworks)

**Configuration Files:**
- `next.config.mjs`
- `tsconfig.json`
- `postcss.config.mjs`
- `components.json`

**Package Files:**
- `package.json`
- `package-lock.json`
- `pnpm-lock.yaml`

**Build Scripts:**
- `build-and-start.bat`
- `start-dev.bat`

**Build Output:**
- `node_modules/`
- `.next/`
- `out/`
- `build/`

**Total:** ~10+ files/directories

---

### ⚠️ NEED CONVERSION (Frontend Code)

**React/Next.js Files:**
- All `.tsx` files in `app/` → Convert to `.html`
- All `.tsx` files in `components/` → Convert to vanilla JS or static HTML
- All `.ts` files in `lib/` → Convert to vanilla JS or JSON
- All `.ts` files in `hooks/` → Convert to vanilla JS or remove

**CSS:**
- `app/globals.css` → Compile Tailwind to pure CSS
- `styles/globals.css` → (if exists)

**Total:** ~100+ files need conversion

---

### ✅ MUST BE KEPT (Static Assets)

**Images:**
- All files in `public/` directory
- All image formats (`.jpg`, `.png`, `.svg`, `.ico`)

**Total:** ~20+ image files

---

## 7. CONVERSION COMPLEXITY ASSESSMENT

### High Complexity (Requires Significant Work)
1. **Menu System** - Currently fully dynamic via Django API
2. **Language Switching** - React Context needs vanilla JS conversion
3. **Theme Switching** - React Context needs vanilla JS conversion
4. **Component Library** - 57+ UI components need conversion
5. **Image Optimization** - Next.js Image → standard img tags

### Medium Complexity
1. **Page Conversion** - TSX → HTML (straightforward but time-consuming)
2. **CSS Compilation** - Tailwind → Pure CSS
3. **Routing** - Next.js routing → Static file structure

### Low Complexity
1. **Static Assets** - Already in `public/`, just copy
2. **Metadata Files** - Simple conversion (manifest, robots, sitemap)
3. **Removal** - Delete backend and build files

---

## 8. RECOMMENDATIONS

### Immediate Actions (Analysis Complete)
1. ✅ **Backend Removal:** Safe to remove entire `backend/` directory
2. ✅ **Build Tools Removal:** Safe to remove Next.js config and package files
3. ⚠️ **Frontend Conversion:** Requires careful conversion to preserve functionality

### Critical Decisions Needed
1. **Menu Data:** Use static data from `lib/menu-data.ts` or remove menu functionality?
2. **Dynamic Routes:** Remove `/menu/[date]` pages or pre-generate specific dates?
3. **Language Support:** Keep bilingual support with vanilla JS or simplify?
4. **Theme Support:** Keep dark/light mode or remove?

### Next Steps (After Decisions)
1. Extract static menu data (if keeping menus)
2. Convert React components to vanilla JS or static HTML
3. Compile Tailwind CSS to pure CSS
4. Convert all TSX pages to HTML
5. Set up static file structure
6. Test all pages and functionality

---

## END OF AUDIT REPORT

**Date:** Generated during analysis
**Status:** Analysis complete - Ready for conversion planning

