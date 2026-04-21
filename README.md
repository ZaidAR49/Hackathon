# Hackathon Project

A [Next.js 16](https://nextjs.org) application built with React 19, TypeScript, and Tailwind CSS v4.

---

## Getting Started

Install dependencies and start the development server:

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Available Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start the local development server |
| `npm run build` | Build the production bundle |
| `npm run start` | Start the production server |
| `npm run lint` | Run ESLint across the project |

---

## Tech Stack

- **Framework** — Next.js 16 (App Router)
- **Language** — TypeScript 5
- **Styling** — Tailwind CSS v4
- **Animations** — Lottie React
- **Runtime** — Node.js

---

## Project Structure

```
hackathon/
├── src/
│   ├── app/                  # Next.js App Router pages & layouts
│   ├── actions/              # Next.js Server Actions
│   ├── components/
│   │   ├── layout/           # Layout-level components (Navbar, Footer, etc.)
│   │   └── ui/               # Reusable UI components (Button, Card, etc.)
│   ├── config/               # App-wide configuration constants
│   ├── lib/
│   │   ├── helpers/          # Pure utility/helper functions
│   │   ├── models/           # TypeScript types, interfaces & data models
│   │   └── services/         # External API & third-party service integrations
│   ├── public/               # Static assets served at the root URL
│   └── proxy.ts              # Next.js middleware proxy utility
├── next.config.ts            # Next.js configuration
├── tsconfig.json             # TypeScript configuration
├── postcss.config.mjs        # PostCSS / Tailwind CSS configuration
└── eslint.config.mjs         # ESLint configuration
```

---

## Folder Explanations

### `src/app/`
The **Next.js App Router** directory. Every file here maps directly to a URL route. This is where pages, layouts, loading states, and error boundaries live.

| File | Purpose |
|---|---|
| `layout.tsx` | Root layout wrapping every page (HTML shell, fonts, global providers) |
| `page.tsx` | Home page rendered at `/` |
| `loading.tsx` | Suspense-based loading skeleton shown while a page is fetching |
| `error.tsx` | Error boundary UI shown when an unhandled error is thrown |
| `not-found.tsx` | Custom 404 page |
| `globals.css` | Global CSS styles and Tailwind base imports |

> **Example:** To add an `/about` route, create `src/app/about/page.tsx`.

---

### `src/actions/`
Contains **Next.js Server Actions** — async functions that run exclusively on the server and are called directly from client or server components. Use this folder for form submissions, database mutations, and any server-side logic that shouldn't be exposed as a public API route.

> **Example:** A `submitContactForm.ts` action that validates input and sends an email via a third-party provider.

---

### `src/components/layout/`
Houses **layout-level components** that are shared across multiple pages and define the overall shell of the application.

> **Examples:** `Navbar.tsx`, `Footer.tsx`, `Sidebar.tsx`, `PageWrapper.tsx`

---

### `src/components/ui/`
Houses **reusable, generic UI components** — the building blocks used throughout the app. These components are presentational and have no knowledge of business logic.

> **Examples:** `Button.tsx`, `Card.tsx`, `Badge.tsx`, `Modal.tsx`, `Spinner.tsx`

---

### `src/config/`
Stores **app-wide configuration constants and settings** that are referenced in multiple places. Centralising them here avoids magic strings and makes updates easy.

> **Examples:**
> - `siteConfig.ts` — site name, base URL, SEO defaults
> - `navLinks.ts` — navigation link definitions
> - `apiConfig.ts` — base API URLs, timeout values

---

### `src/lib/helpers/`
Contains **pure utility and helper functions** — stateless, framework-agnostic functions that perform a single well-defined task and can be reused anywhere.

> **Examples:**
> - `cloudHelper.ts` — utilities for constructing cloud storage URLs, parsing bucket paths
> - `dateHelper.ts` — formatting and parsing dates (`formatDate`, `timeAgo`)
> - `stringHelper.ts` — truncating text, slugifying strings
> - `validationHelper.ts` — reusable input validation logic

---

### `src/lib/models/`
Contains **TypeScript types, interfaces, and data models** that describe the shape of data flowing through the application. Keeping all type definitions here ensures consistency and a single source of truth.

> **Examples:**
> - `User.ts` — `interface User { id: string; name: string; email: string; }`
> - `Product.ts` — product entity type
> - `ApiResponse.ts` — generic API response wrapper type

---

### `src/lib/services/`
Contains **service modules** that encapsulate all communication with external APIs and third-party integrations. Each service file is responsible for one external system, keeping the rest of the codebase decoupled from implementation details.

> **Examples:**
> - `cloudService.ts` — uploads/downloads files to/from a cloud storage provider (e.g. AWS S3, GCS)
> - `authService.ts` — wraps authentication API calls (login, logout, token refresh)
> - `emailService.ts` — sends transactional emails via a provider like SendGrid or Resend
> - `analyticsService.ts` — tracks events with an analytics provider

---

### `src/public/`
Static files that are served at the root of the domain without any processing. Lottie JSON animation files, images, fonts, and other assets go here.

> **Current contents:**
> - `lottie-notFound-error.json` — Lottie animation for the 404 page
> - `lottie-server-error.json` — Lottie animation for the 500 error page

---

### `src/proxy.ts`
A **Next.js middleware utility** that intercepts incoming requests before they reach a page or API route. Used for tasks like authentication guards, request rewrites, and header injection.

> **Example:** Redirecting unauthenticated users away from protected routes such as `/dashboard`.
