# Krapesto Restaurant Website

A modern restaurant website built with Next.js, React, and Tailwind CSS.

## Prerequisites

Before running this website locally, make sure you have the following installed:

- **Node.js** (version 18 or higher) - [Download here](https://nodejs.org/)
- **npm** (comes with Node.js) or **pnpm** (optional, but recommended)

To check if you have Node.js installed, run:
```bash
node --version
npm --version
```

## Installation

1. **Install dependencies:**
   
   If you have `pnpm` installed:
   ```bash
   pnpm install
   ```
   
   Or using `npm`:
   ```bash
   npm install
   ```

   This will install all required packages listed in `package.json`.

## Running Locally

### Development Mode (Recommended for testing)

Run the development server:
```bash
npm run dev
# or
pnpm dev
```

The website will be available at:
- **Local:** http://localhost:3000
- **Network:** http://[your-ip]:3000 (accessible from other devices on your network)

The development server includes:
- Hot reloading (changes appear instantly)
- Error messages in the browser
- Fast refresh for React components

### Production Build (For final testing)

1. **Build the production version:**
   ```bash
   npm run build
   # or
   pnpm build
   ```

2. **Start the production server:**
   ```bash
   npm start
   # or
   pnpm start
   ```

The production build will be available at http://localhost:3000

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm start` - Start production server
- `npm run lint` - Run ESLint to check code quality

## Project Structure

```
krapesto-restaurant-website/
├── app/                 # Next.js app directory (pages)
│   ├── about/          # About page
│   ├── contact/        # Contact page
│   ├── events/         # Events pages
│   ├── gallery/        # Gallery page
│   └── menu/           # Menu page
├── components/          # React components
│   ├── ui/             # UI components (buttons, cards, etc.)
│   └── ...             # Other components
├── public/             # Static assets (images, icons)
├── lib/                # Utility functions and data
└── styles/             # Global styles
```

## Features

- 🌐 Multi-language support
- 🎨 Dark/Light theme toggle
- 📱 Responsive design
- 🍕 Menu display
- 📸 Gallery
- 📅 Events pages
- 📧 Contact form

## Troubleshooting

### Port 3000 already in use

If port 3000 is already in use, you can specify a different port:
```bash
npm run dev -- -p 3001
```

### Installation issues

If you encounter issues during installation:
1. Delete `node_modules` folder (if it exists)
2. Delete `package-lock.json` or `pnpm-lock.yaml`
3. Run `npm install` again

### Build errors

The project is configured to ignore TypeScript build errors (`ignoreBuildErrors: true` in `next.config.mjs`), so the build should complete even with minor type issues.

## Accessing from Other Devices

To access the website from other devices on your local network:

1. Find your computer's IP address:
   - Windows: Run `ipconfig` in Command Prompt and look for IPv4 Address
   - Mac/Linux: Run `ifconfig` or `ip addr`

2. Start the dev server:
   ```bash
   npm run dev
   ```

3. Access from another device using:
   ```
   http://[your-ip-address]:3000
   ```

## Notes

- Images are configured as unoptimized for easier local deployment
- The website uses Next.js 16 with React 19
- Tailwind CSS is used for styling
- The project includes Vercel Analytics (can be removed if not needed)

## Support

For issues or questions, check the Next.js documentation: https://nextjs.org/docs


