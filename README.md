## Next.js Tutorials Project

This repository is a **minimal tutorial-style Next.js 16 app** using the **App Router**, **TypeScript**, **React 19**, and **Tailwind CSS v4 (via PostCSS plugin)**. It demonstrates:

- **App routing** with route groups (`(root)`, `(dashboard)`)
- **Layout nesting** for a public site and a dashboard section
- **Dynamic routes** with URL params for user detail pages
- **Error boundaries** for route-level error handling
- **React Compiler** and modern Next.js tooling (ESLint, TypeScript) ⚙️

---

## Tech Stack

- **Framework**: Next.js `16.0.4` (App Router)
- **Language**: TypeScript
- **UI**: React `19.2.0`
- **Styling**: Tailwind CSS `^4` via `@tailwindcss/postcss` and `app/globals.css`
- **Fonts**: [`Geist`](https://vercel.com/font) via `next/font/google`
- **Linting**: ESLint `^9` with `eslint-config-next` (core-web-vitals + TypeScript)

---

## Project Structure (High Level)

- `app/layout.tsx` – Root HTML shell (global fonts + `<body>`)
- `app/globals.css` – Global styles, CSS variables, dark mode, Tailwind setup
- `app/(root)/layout.tsx` – Public layout with shared `Navbar`
- `app/(root)/page.tsx` – Home page: “Welcome to Next.js!”
- `app/(root)/about/page.tsx` – About page (intentionally throws an error to demo error handling)
- `app/(root)/error.tsx` – Client-side error boundary with “Try again” button
- `app/(dashboard)/layout.tsx` – Dashboard layout with `dashboard Navbar`
- `app/(dashboard)/dashboard/analytics/page.tsx` – Simple analytics page
- `app/(dashboard)/dashboard/users/page.tsx` – Users list with links to user details
- `app/(dashboard)/dashboard/users/[id]/page.tsx` – Dynamic route using `params.id`
- `app/loader.tsx` – Simple loader component (`__ Spinner __`)
- `next.config.ts` – Next config with `reactCompiler` and experimental dev cache
- `tsconfig.json` – TypeScript configuration (strict mode, path alias `@/*`)
- `eslint.config.mjs` – ESLint configuration for Next.js + TypeScript

---

## Getting Started

### 1. Install dependencies

```bash
npm install
```

> You can also use **pnpm**, **yarn**, or **bun** if you prefer, but the lockfile in this repo is for `npm`.

### 2. Run the dev server

```bash
npm run dev
```

Then open `http://localhost:3000` in your browser. 🔥  
Hot reloading is enabled, so changes are reflected immediately.

---

## Available Scripts

- **`npm run dev`** – Start the Next.js dev server
- **`npm run build`** – Create an optimized production build
- **`npm run start`** – Run the production server (after `npm run build`)
- **`npm run lint`** – Run ESLint using the Next.js + TypeScript config

---

## Routes & Navigation

- **Home**: `/`
  - Component: `app/(root)/page.tsx`
  - Shows “Welcome to Next.js!” with basic Tailwind styling.

- **About**: `/about`
  - Component: `app/(root)/about/page.tsx`
  - Currently **throws an error intentionally** (`throw new Error("Test error in about page")`) so you can see the error boundary in action.

- **Dashboard** (layout): `/dashboard/*`
  - Layout: `app/(dashboard)/layout.tsx`
  - Wraps dashboard pages with a `dashboard Navbar`.

- **Dashboard → Analytics**: `/dashboard/analytics`
  - Simple example page component `Analyticss`.

- **Dashboard → Users list**: `/dashboard/users`
  - Renders a list of links: `/dashboard/users/1`, `/dashboard/users/2`, etc.
  - Implemented with `next/link` for client-side navigation.

- **Dashboard → User details**: `/dashboard/users/[id]`
  - Dynamic route using the segment `[id]`.
  - Component receives `params` and displays `User Details for ID: #{id}`.

---

## Error Handling Demo

This project intentionally includes an error on the **About** page to demonstrate **route-level error boundaries** in the Next.js App Router:

- The `About` page throws an error.
- `app/(root)/error.tsx` catches it and renders a friendly message plus a **“Try again”** button.
- The error is also logged to the console for debugging.

This pattern is aligned with **modern production-grade error handling** in Next.js apps. ✅

---

## Styling & Theming

- Global styles live in `app/globals.css`.
- Uses CSS variables for `--background` and `--foreground`.
- Supports **dark mode** via the `prefers-color-scheme: dark` media query.
- Tailwind CSS v4 is enabled via the `@tailwindcss/postcss` plugin in `postcss.config.mjs`.
- Fonts are provided by `Geist` and `Geist_Mono` through `next/font/google`, following current best practices for **performance and CLS reduction**.

---

## Production Build & Deployment

To create a production build:

```bash
npm run build
npm run start
```

You can deploy the built app to any Node.js-capable host or use modern platforms like:

- **Vercel** (recommended for Next.js)
- **Netlify**
- **Render**

Just point the platform to:

- **Build command**: `npm run build`
- **Start command**: `npm run start`
- **Output**: Next.js default (`.next` directory)

---

## Conclusion

This project is a **compact, modern Next.js 16 tutorial** showcasing:

- App Router, layouts, and route groups
- Dynamic routing and dashboard-style navigation
- Error boundaries and basic loader component
- TypeScript, React 19, Tailwind v4, and React Compiler

Use it as a **starting point** to explore Next.js best practices, then extend it with your own pages, APIs, and UI components. 🚀
