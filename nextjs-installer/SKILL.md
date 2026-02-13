---
name: nextjs-installer
description: Installs and configures Next.js projects with various options including App Router, Pages Router, TypeScript, Tailwind CSS, ESLint, and src directory. Use when creating or setting up a new Next.js application.
---

# Next.js Installer

Skill untuk membuat dan mengkonfigurasi proyek Next.js dengan berbagai opsi.

## Penggunaan Dasar

Buat proyek Next.js baru dengan perintah:

```bash
npx create-next-app@latest <project-name>
```

## Opsi yang Tersedia

| Opsi          | Flag                    | Deskripsi                        |
| ------------- | ----------------------- | -------------------------------- |
| TypeScript    | `--typescript` / `--ts` | Menggunakan TypeScript           |
| JavaScript    | `--javascript` / `--js` | Menggunakan JavaScript (default) |
| Tailwind CSS  | `--tailwind`            | Menggunakan Tailwind CSS         |
| ESLint        | `--eslint`              | Menggunakan ESLint               |
| App Router    | `--app`                 | Menggunakan App Router (default) |
| Pages Router  | `--no-app`              | Menggunakan Pages Router         |
| Src Directory | `--src-dir`             | Menggunakan struktur `src/`      |
| Import Alias  | `--import-alias "@/*"`  | Mengatur import alias            |
| Turbopack     | `--turbopack`           | Menggunakan Turbopack untuk dev  |
| Skip Install  | `--no-install`          | Skip npm install                 |
| Skip Git      | `--no-git`              | Skip git initialization          |

## Contoh Penggunaan

### Proyek Minimal (Default)

```bash
npx create-next-app@latest my-app
```

### Dengan TypeScript + Tailwind + App Router

```bash
npx create-next-app@latest my-app --typescript --tailwind --app
```

### Dengan Semua Fitur (Recommended)

```bash
npx create-next-app@latest my-app --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
```

### Non-Interactive (Semua opsi ditentukan)

```bash
npx create-next-app@latest my-app \
  --typescript \
  --tailwind \
  --eslint \
  --app \
  --src-dir \
  --import-alias "@/*" \
  --turbopack
```

### Pages Router (Legacy)

```bash
npx create-next-app@latest my-app --typescript --tailwind --no-app
```

## Struktur Proyek

### App Router (Default)

```
my-app/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── public/
├── next.config.ts
├── package.json
└── tsconfig.json
```

### Dengan Src Directory

```
my-app/
├── src/
│   └── app/
│       ├── layout.tsx
│       ├── page.tsx
│       └── globals.css
├── public/
├── next.config.ts
├── package.json
└── tsconfig.json
```

## Setelah Instalasi

1. Masuk ke direktori proyek:

```bash
cd my-app
```

2. Jalankan development server:

```bash
npm run dev
# atau dengan turbopack
npm run dev --turbopack
```

3. Buka http://localhost:3000 di browser

## Dependencies Tambahan yang Sering Digunakan

### State Management

```bash
npm install zustand        # Lightweight state management
npm install @reduxjs/toolkit react-redux  # Redux Toolkit
```

### UI Components

```bash
npm install @radix-ui/react-dropdown-menu
npm install lucide-react   # Icons
npm install clsx tailwind-merge  # Utility for className
```

### Form & Validation

```bash
npm install react-hook-form
npm install zod
npm install @hookform/resolvers
```

### Data Fetching

```bash
npm install @tanstack/react-query
npm install axios
```

### Database & ORM

```bash
npm install prisma @prisma/client
npm install @planetscale/database
```

### Authentication

```bash
npm install next-auth
npm install @auth/prisma-adapter
```

## Tips

- Gunakan `--src-dir` untuk proyek yang lebih terorganisir
- TypeScript sangat direkomendasikan untuk proyek production
- Tailwind CSS mempercepat styling
- Aktifkan ESLint untuk kualitas kode
- App Router adalah cara modern dengan fitur terbaru
