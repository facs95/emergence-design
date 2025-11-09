# Emergence Design System

> A minimal, flexible design foundation for building beautiful software products that feel like family.

## Overview

The Emergence Design System provides a foundation for building software products that maintain a family resemblance while expressing individual brand identities. Think of it like siblings: different personalities and styles, but similar bone structure.

This system is designed to be:
- **Minimal** - Only essential foundations, not prescriptive rules
- **Flexible** - Each product can have its own brand colors and personality
- **AI-friendly** - Structured so AI assistants can read and apply the guidelines
- **Modern** - Inspired by Linear, Notion, Todoist, and LogSnag
- **Practical** - Built on shadcn/ui and Tailwind CSS

---

## Quick Start

### For Humans

1. **Start here:** Read [Design Principles](./principles.md) to understand the philosophy
2. **Core foundations:**
   - [Typography](./typography.md) - Font choices, type scale, hierarchy
   - [Spacing](./spacing.md) - The 4px base unit system
   - [Colors](./colors.md) - How to use color meaningfully
   - [Components](./components.md) - Using shadcn/ui effectively
3. **Reference:** [Design Tokens](./tokens.json) - All values in JSON format
4. **Examples:** See `/examples/themes/` for product theme configurations

### For AI Assistants

When building an Emergence product:

1. **Read `tokens.json`** for all design token values (spacing, typography, colors, etc.)
2. **Follow `principles.md`** for design philosophy and decision-making framework
3. **Use shadcn/ui components** as the UI foundation (see `components.md`)
4. **Apply patterns** from the guide files for consistency
5. **Ask for brand color** if building a new product (or suggest options)

**Key principle:** Maintain consistency in typography, spacing, and patterns. Allow flexibility in brand colors and personality.

---

## What's Included

### Design Tokens (`tokens.json`)

Machine-readable values for:
- Typography (font families, sizes, weights, line heights)
- Spacing (4px-based scale)
- Colors (neutrals and semantic colors)
- Border radius, shadows, animations
- Layout (breakpoints, max widths, grid)
- Z-index scale

### Guidelines

**Core System:**
- **[Principles](./principles.md)** - Design philosophy and decision framework
- **[Typography](./typography.md)** - Type system and usage patterns
- **[Spacing](./spacing.md)** - Spacing scale and layout patterns
- **[Colors](./colors.md)** - Color usage and accessibility guidelines

**Implementation:**
- **[Components](./components.md)** - How to use shadcn/ui with this system

### Examples

- **Theme configurations** - Example brand color configurations for new products
- **Component patterns** - Common UI patterns and compositions

---

## Philosophy

### What's Consistent Across All Products?

✅ **Typography system** - Inter font, type scale, hierarchy patterns
✅ **Spacing scale** - 4px base unit, consistent rhythm
✅ **Design principles** - Clarity, accessibility, subtlety
✅ **Component patterns** - Similar UI patterns and behaviors
✅ **Neutral colors** - Shared gray scale for UI chrome

### What's Unique Per Product?

🎨 **Primary brand color** - Each product has its own identity
🎨 **Imagery and illustrations** - Product-specific visuals
🎨 **Tone and personality** - Expressed through copy and interactions
🎨 **Product-specific components** - Custom features as needed

This balance creates a family resemblance while allowing distinct personalities.

---

## Technology Stack

### Recommended Foundation

- **Framework:** React with Next.js or TanStack Start
- **Styling:** Tailwind CSS
- **Components:** shadcn/ui
- **Icons:** Lucide Icons
- **Fonts:** Inter (primary), JetBrains Mono (monospace)

### Why This Stack?

- **shadcn/ui** - Perfectly aligned with our aesthetic, accessible, customizable
- **Tailwind CSS** - Built-in 4px spacing, easy to apply tokens, utility-first
- **Inter font** - Modern, readable, widely used in SaaS products
- **Copy, not install** - You own the code, easy to customize
- **TanStack Start** - Modern full-stack framework with type-safe routing and server functions

---

## Design Principles (Summary)

1. **Clarity First** - Every element has a clear purpose
2. **Consistent Spacing** - Use the spacing scale religiously
3. **Subtle by Default** - Animations and effects should feel natural
4. **Accessible Always** - WCAG AA minimum, strive for AAA
5. **Fast and Light** - Performance matters
6. **Mobile-First Thinking** - Design for mobile, enhance for desktop

See [principles.md](./principles.md) for details.

---

## Getting Started with a New Product

### Step 1: Choose Your Brand Color

Pick a primary color that reflects your product's personality:

- **Professional tools** → Blue, purple, gray
- **Creative tools** → Orange, pink, teal
- **Financial tools** → Blue, green
- **Communication tools** → Blue, purple

**Tools to generate a color scale:**
- [UIColors](https://uicolors.app/create)
- [Shadcn Theme Generator](https://gradient.page/tools/shadcn-theme-generator)

### Step 2: Set Up Your Project

Choose your preferred framework:

#### Option A: Next.js

```bash
# Create Next.js project
npx create-next-app@latest my-emergence-app

# Initialize Tailwind (if not already done)
npx tailwindcss init -p

# Initialize shadcn/ui
npx shadcn@latest init

# Choose:
# - Style: Default
# - Base color: Neutral
# - CSS variables: Yes
```

#### Option B: TanStack Start

```bash
# Create TanStack Start project
pnpm create @tanstack/start@latest my-emergence-app

# During setup, choose:
# - Enable Tailwind CSS: Yes
# - Enable ESLint: Yes (recommended)

cd my-emergence-app
pnpm install

# Initialize shadcn/ui
npx shadcn@latest init

# Choose:
# - Style: Default
# - Base color: Neutral
# - CSS variables: Yes
```

### Step 3: Configure Design Tokens

#### For Next.js

**Install Inter font:**
```tsx
// app/layout.tsx
import { Inter } from 'next/font/google'

const inter = Inter({ subsets: ['latin'] })

export default function RootLayout({ children }) {
  return (
    <html lang="en" className={inter.className}>
      <body>{children}</body>
    </html>
  )
}
```

**Set your brand color:**
```css
/* app/globals.css */
@layer base {
  :root {
    --primary: YOUR_COLOR_HSL;  /* e.g., 221 83% 53% for blue */
    --primary-foreground: 0 0% 100%;
    /* shadcn provides the rest */
  }
}
```

#### For TanStack Start

**Install Inter font:**
```bash
pnpm add @fontsource-variable/inter
```

**Import Inter in your root route:**
```tsx
// src/routes/__root.tsx
/// <reference types="vite/client" />
import { createRootRoute, Outlet, Scripts, HeadContent } from '@tanstack/react-router'
import { TanStackRouterDevtools } from '@tanstack/react-router-devtools'
import '@fontsource-variable/inter'
import appCss from '../styles/app.css?url'

export const Route = createRootRoute({
  head: () => ({
    meta: [
      { charSet: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { title: 'My Emergence App' },
    ],
    links: [
      { rel: 'stylesheet', href: appCss }
    ],
  }),
  component: RootComponent,
})

function RootComponent() {
  return (
    <RootDocument>
      <Outlet />
    </RootDocument>
  )
}

function RootDocument({ children }: { children: React.ReactNode }) {
  return (
    <html>
      <head>
        <HeadContent />
      </head>
      <body className="font-sans">
        {children}
        <TanStackRouterDevtools position="bottom-right" />
        <Scripts />
      </body>
    </html>
  )
}
```

**Configure Tailwind to use Inter:**
```js
// tailwind.config.js
export default {
  content: ['./src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter Variable', 'system-ui', 'sans-serif'],
      },
    },
  },
}
```

**Set your brand color:**
```css
/* src/styles/app.css */
@import 'tailwindcss';

@layer base {
  :root {
    --primary: YOUR_COLOR_HSL;  /* e.g., 221 83% 53% for blue */
    --primary-foreground: 0 0% 100%;
    /* shadcn provides the rest */
  }
}
```

### Step 4: Install Core Components

```bash
npx shadcn@latest add button
npx shadcn@latest add input
npx shadcn@latest add card
npx shadcn@latest add label
# ... add as needed
```

### Step 5: Build with the System

- Use components from shadcn/ui
- Apply spacing from the scale (Tailwind classes)
- Follow typography patterns
- Reference the guidelines when making decisions

**Example:**
```tsx
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card'

export default function Home() {
  return (
    <div className="container mx-auto px-6 py-12">
      <div className="space-y-8">
        <div>
          <h1 className="text-4xl font-semibold mb-2">Welcome</h1>
          <p className="text-lg text-gray-600">
            Built with the Emergence Design System
          </p>
        </div>

        <Card className="p-6">
          <CardHeader className="p-0 mb-4">
            <CardTitle>Getting Started</CardTitle>
          </CardHeader>
          <CardContent className="p-0">
            <p className="text-gray-600 mb-4">
              Your product is ready to build.
            </p>
            <Button>Get Started</Button>
          </CardContent>
        </Card>
      </div>
    </div>
  )
}
```

---

## Design Reviews

When reviewing designs for Emergence products, ask:

1. **Does it follow the spacing scale?** Check padding, margins, gaps
2. **Is the typography correct?** Sizes, weights, line heights
3. **Are colors accessible?** Check contrast ratios
4. **Does it feel "Emergence"?** Clean, minimal, purposeful
5. **Is it consistent?** Similar patterns to other products

---

## Contributing

This design system will evolve based on learnings from building products.

**To propose changes:**
1. Document the rationale
2. Show examples from actual usage
3. Consider impact on existing products
4. Update relevant markdown files
5. Update `tokens.json` if values change

**Maintain:**
- Backward compatibility when possible
- Clear documentation
- Practical, tested patterns

---

## File Structure

```
/emergence/design/
├── README.md           ← You are here (start here)
├── tokens.json         ← All design tokens (machine-readable)
├── principles.md       ← Design philosophy and principles
├── typography.md       ← Type system and patterns
├── spacing.md          ← Spacing scale and layout
├── colors.md           ← Color usage guidelines
├── components.md       ← shadcn/ui integration guide
└── examples/
    └── themes/         ← Example theme configurations
        ├── product-a.json
        ├── product-b.json
        └── README.md
```

---

## Examples & Inspiration

**Emergence family aesthetic is inspired by:**

- **[Linear](https://linear.app)** - Clean, fast, purposeful interfaces
- **[Notion](https://notion.com)** - Flexible, calm, well-spaced layouts
- **[Todoist](https://todoist.com)** - Clear hierarchy, excellent color usage
- **[LogSnag](https://logsnag.com)** - Modern, sophisticated aesthetic
- **[shadcn/ui](https://ui.shadcn.com)** - Beautiful, accessible components

Study these to understand the aesthetic we're aiming for.

---

## Resources

**Design Tools:**
- [Figma](https://figma.com) - Design and prototype
- [UIColors](https://uicolors.app/create) - Generate color scales
- [Coolors](https://coolors.co) - Color palettes and contrast checking
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)

**Development:**
- [shadcn/ui](https://ui.shadcn.com)
- [Tailwind CSS](https://tailwindcss.com)
- [Radix UI](https://radix-ui.com)
- [Lucide Icons](https://lucide.dev)
- [TanStack Start](https://tanstack.com/start)
- [Next.js](https://nextjs.org)

**Typography:**
- [Inter Font](https://rsms.me/inter/)
- [JetBrains Mono](https://www.jetbrains.com/lp/mono/)
- [Modern Font Stacks](https://modernfontstacks.com/)

---

## Support

This is a living design system. It will grow and improve as we build more products.

**Questions or suggestions?**
- Open an issue in the repository
- Propose changes via pull request
- Document learnings from real usage

---

## Version

**Current version:** 1.0.0

**Last updated:** 2025

**Maintained by:** Emergence

---

## License

This design system is part of the Emergence family of products.

The guidelines and documentation are open for Emergence products to use and adapt as needed.

---

## Quick Links

- **[Design Principles](./principles.md)** - Start here for philosophy
- **[Design Tokens](./tokens.json)** - All values in JSON
- **[Typography Guide](./typography.md)** - Type system
- **[Spacing Guide](./spacing.md)** - Layout and spacing
- **[Color Guide](./colors.md)** - Color usage
- **[Component Guide](./components.md)** - Using shadcn/ui
- **[Examples](./examples/themes/)** - Theme configurations

---

**Build beautiful products. Maintain family resemblance. Express unique personality.**

That's the Emergence way.
