# AI Coding Agent Instructions - NextLvL Gaming Website

## Project Overview

**NextLvL Gaming Website** is a hybrid project combining:
- **Static HTML/CSS site** (root level): Home, About, Products, Contact, Enquiry pages with dark-themed gaming aesthetic
- **React + TypeScript + Vite application** (`next-app/`): Modern component-driven UI built with shadcn/ui and Tailwind CSS

The static site serves as the main website; the `next-app` is a separate development for modernizing/replacing parts with React components.

## Architecture & Key Directories

### Static Site (`root` directory)
- **HTML Pages**: `Index.HTML`, `About.html`, `Products.html`, `contact.html`, `enquiry.html`
- **Styling**: `styles.css` - Custom dark gaming theme with CSS variables (e.g., `--accent: #d9ff5c`, `--bg: #070b0d`)
- **Assets**: PNG logos and JPG product/feature images
- **Pattern**: Traditional multi-page site with semantic HTML and consistent navigation

### React Application (`next-app/`)
- **Build Tool**: Vite with React plugin
- **Styling**: Tailwind CSS + @tailwindcss/vite + shadcn/ui components
- **Entry Point**: `src/main.tsx` → `src/App.tsx`
- **Path Alias**: `@/` resolves to `src/` (configured in `vite.config.ts`)
- **Components**: 
  - `src/components/theme-provider.tsx` - Theme switching (light/dark/system) with localStorage persistence
  - `src/components/ui/` - shadcn/ui components (added via `npx shadcn@latest add <component>`)

## Development Workflows

### Static Site
- **Edit & View**: Direct browser open of `.html` files or use a local server
- **Styling**: Modify `styles.css` (uses CSS custom properties for consistent theming)

### React App
```bash
# Install dependencies
npm install

# Development server (hot reload)
npm run dev

# Build for production
npm run build

# Type checking
npm run typecheck

# Linting
npm run lint

# Code formatting
npm run format
```

## Project-Specific Conventions

### Design System
- **Color Theme** (in `styles.css`): Dark gaming aesthetic with neon lime accents
  - Primary background: `#070b0d`
  - Accent (lime): `#d9ff5c` (lighter: `#b9fb31`)
  - Text: `#f4f9ef` (light), Muted: `#d5e8d0`
- **Apply to React**: Reference CSS variables or replicate Tailwind equivalents in component classes

### React Components
- **Import Path**: Always use `@/components/...` alias, not relative paths
- **UI Components**: Imported from `@/components/ui/` (shadcn/ui)
- **Theme Integration**: Wrap app with `<ThemeProvider>` to enable dark/light mode toggle
- **Tailwind Styling**: Use Prettier plugin (`prettier-plugin-tailwindcss`) for class ordering

### Navigation
- **Static Site**: Common `<nav class="top-nav">` links all pages
- **React App**: Currently standalone; no routing configured yet
- **When adding routing**: Use component-based imports consistent with `@/` alias pattern

## Critical Integration Points

- **Theme Persistence**: `theme-provider.tsx` uses `localStorage` key (customizable via `storageKey` prop)
- **Component Addition**: Use `npx shadcn@latest add <name>` to add pre-built components
- **Type Safety**: TypeScript strict mode enabled (`typescript: ~6`)
- **Linting**: ESLint with React hooks plugin; formatting via Prettier

## Common Tasks

- **Add new React component**: Create in `src/components/`, export from `index.tsx` if re-exporting
- **Add shadcn/ui component**: `npx shadcn@latest add <component>` (generates in `src/components/ui/`)
- **Style updates**: For static site → `styles.css`; for React → Tailwind classes + CSS variables
- **Theme toggle**: User can press `d` key (see `App.tsx` comment) when using theme provider

## Important Notes

- **No routing configured**: React app is currently single-page; add React Router if expanding
- **Build before deploy**: `npm run build` required for production (outputs to `dist/`)
- **Keep both sites in sync**: If migrating static pages to React, maintain consistent branding/navigation
