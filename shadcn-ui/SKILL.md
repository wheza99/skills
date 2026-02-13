---
name: shadcn-ui
description: Installs and configures shadcn/ui components for Next.js projects. Use when adding shadcn/ui to a Next.js application or installing specific UI components like button, dialog, dropdown, form, table, etc.
---

# shadcn/ui Installer

Skill untuk menginstal dan mengkonfigurasi shadcn/ui di proyek Next.js.

## Prasyarat

Pastikan proyek Next.js sudah dibuat dengan:

- TypeScript
- Tailwind CSS
- App Router

```bash
npx create-next-app@latest my-app --typescript --tailwind --app
```

## Instalasi Awal

### 1. Inisialisasi shadcn/ui

```bash
npx shadcn@latest init
```

Opsi interaktif akan muncul, atau gunakan flags:

```bash
npx shadcn@latest init -d  # Menggunakan defaults
```

### 2. Konfigurasi Manual (jika diperlukan)

```bash
npx shadcn@latest init --style default --base-color neutral --css-variables
```

| Opsi          | Values                                      | Deskripsi             |
| ------------- | ------------------------------------------- | --------------------- |
| Style         | `default`, `new-york`                       | Gaya komponen         |
| Base Color    | `slate`, `gray`, `zinc`, `neutral`, `stone` | Warna dasar           |
| CSS Variables | `yes`, `no`                                 | Gunakan CSS variables |

## Struktur Setelah Instalasi

```
my-app/
├── components/
│   └── ui/           # Komponen shadcn akan di sini
├── lib/
│   └── utils.ts      # Utility functions (cn, dll)
├── app/
├── components.json   # Konfigurasi shadcn
└── ...
```

## Menginstal Komponen

### Instal Komponen Individual

```bash
npx shadcn@latest add button
npx shadcn@latest add dialog
npx shadcn@latest add dropdown-menu
npx shadcn@latest add form
npx shadcn@latest add input
npx shadcn@latest add table
```

### Instal Multiple Komponen

```bash
npx shadcn@latest add button dialog input
```

### Instal Semua Komponen

```bash
npx shadcn@latest add --all
```

## Daftar Komponen Tersedia

| Komponen          | Deskripsi                  |
| ----------------- | -------------------------- |
| `accordion`       | Collapsible content panels |
| `alert`           | Alert messages             |
| `alert-dialog`    | Modal alert dialogs        |
| `aspect-ratio`    | Aspect ratio container     |
| `avatar`          | User avatars               |
| `badge`           | Badges and tags            |
| `breadcrumb`      | Navigation breadcrumbs     |
| `button`          | Buttons                    |
| `calendar`        | Date calendar              |
| `card`            | Card containers            |
| `carousel`        | Image/content carousel     |
| `chart`           | Charts (recharts)          |
| `checkbox`        | Checkbox inputs            |
| `collapsible`     | Collapsible sections       |
| `combobox`        | Combo dropdown             |
| `command`         | Command palette            |
| `context-menu`    | Right-click menu           |
| `data-table`      | Advanced data tables       |
| `date-picker`     | Date picker                |
| `dialog`          | Modal dialogs              |
| `drawer`          | Slide-out drawer           |
| `dropdown-menu`   | Dropdown menus             |
| `form`            | Form with validation       |
| `hover-card`      | Hover card popups          |
| `input`           | Text inputs                |
| `input-otp`       | OTP input fields           |
| `label`           | Form labels                |
| `menubar`         | Menu bar                   |
| `navigation-menu` | Navigation menus           |
| `pagination`      | Pagination controls        |
| `popover`         | Popover overlays           |
| `progress`        | Progress bars              |
| `radio-group`     | Radio button groups        |
| `resizable`       | Resizable panels           |
| `scroll-area`     | Custom scroll areas        |
| `select`          | Select dropdowns           |
| `separator`       | Visual separators          |
| `sheet`           | Side sheet panels          |
| `skeleton`        | Loading skeletons          |
| `slider`          | Range sliders              |
| `sonner`          | Toast notifications        |
| `switch`          | Toggle switches            |
| `table`           | Data tables                |
| `tabs`            | Tab navigation             |
| `textarea`        | Multiline text input       |
| `toast`           | Toast messages             |
| `toggle`          | Toggle buttons             |
| `toggle-group`    | Toggle button groups       |
| `tooltip`         | Tooltips                   |

## Contoh Penggunaan

### Button

```tsx
import { Button } from "@/components/ui/button";

export default function Page() {
  return (
    <div className="flex gap-2">
      <Button>Default</Button>
      <Button variant="secondary">Secondary</Button>
      <Button variant="destructive">Destructive</Button>
      <Button variant="outline">Outline</Button>
      <Button variant="ghost">Ghost</Button>
      <Button variant="link">Link</Button>
    </div>
  );
}
```

### Dialog

```tsx
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";
import { Button } from "@/components/ui/button";

export default function Page() {
  return (
    <Dialog>
      <DialogTrigger asChild>
        <Button variant="outline">Open Dialog</Button>
      </DialogTrigger>
      <DialogContent>
        <DialogHeader>
          <DialogTitle>Are you sure?</DialogTitle>
          <DialogDescription>This action cannot be undone.</DialogDescription>
        </DialogHeader>
      </DialogContent>
    </Dialog>
  );
}
```

### Form dengan Zod

```tsx
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

const formSchema = z.object({
  username: z.string().min(2).max(50),
});

export default function ProfileForm() {
  const form = useForm<z.infer<typeof formSchema>>({
    resolver: zodResolver(formSchema),
    defaultValues: {
      username: "",
    },
  });

  function onSubmit(values: z.infer<typeof formSchema>) {
    console.log(values);
  }

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
        <FormField
          control={form.control}
          name="username"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Username</FormLabel>
              <FormControl>
                <Input placeholder="shadcn" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />
        <Button type="submit">Submit</Button>
      </form>
    </Form>
  );
}
```

## Dependencies Tambahan

Beberapa komponen memerlukan dependencies tambahan:

```bash
# Untuk form
npm install react-hook-form @hookform/resolvers zod

# Untuk chart
npm install recharts

# Untuk date picker
npm install date-fns

# Untuk sonner (toast)
npm install sonner

# Untuk carousel
npm install embla-carousel-react

# Untuk command palette
npm install cmdk

# Untuk resizable
npm install react-resizable-panels
```

## Theming

### Mengubah Warna

Edit `app/globals.css`:

```css
@layer base {
  :root {
    --background: 0 0% 100%;
    --foreground: 222.2 84% 4.9%;
    --primary: 222.2 47.4% 11.2%;
    --primary-foreground: 210 40% 98%;
    /* ... */
  }

  .dark {
    --background: 222.2 84% 4.9%;
    --foreground: 210 40% 98%;
    /* ... */
  }
}
```

### Dark Mode

Tambahkan di `app/layout.tsx`:

```tsx
<html lang="en" suppressHydrationWarning>
  <body>
    <ThemeProvider attribute="class" defaultTheme="system">
      {children}
    </ThemeProvider>
  </body>
</html>
```

```bash
npx shadcn@latest add theme-toggle
```

## Tips

- Gunakan `npx shadcn@latest add --all` untuk menginstal semua komponen sekaligus
- Komponen di-copy ke proyek, jadi bisa dimodifikasi sesuai kebutuhan
- Selalu gunakan TypeScript untuk pengalaman terbaik
- Install `lucide-react` untuk icons: `npm install lucide-react`
- Untuk className conditioning, gunakan `cn()` dari `lib/utils`
