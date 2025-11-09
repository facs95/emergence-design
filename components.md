# Component Guidelines

> How to use shadcn/ui as the foundation for Emergence products, while maintaining design system consistency.

## Overview

[shadcn/ui](https://ui.shadcn.com) is the recommended component library for all Emergence web applications. It aligns perfectly with our design philosophy:

- **Accessible by default** (built on Radix UI)
- **Customizable** (you own the code)
- **Modern aesthetic** (similar to Linear, Notion)
- **TypeScript-first**
- **Tailwind-based** (easy to apply our design tokens)

---

## Why shadcn/ui?

### Perfect Alignment

shadcn/ui already follows similar principles to the Emergence design system:

✅ Uses Inter font by default
✅ 4px-based spacing (Tailwind)
✅ Neutral gray palette similar to ours
✅ Medium border radius
✅ Subtle shadows
✅ Clean, minimal aesthetic
✅ Accessibility built-in

### Customization Model

Unlike traditional component libraries, shadcn/ui:

- **Copies components into your project** (not installed as dependency)
- **You own the code** (modify as needed)
- **Easy to theme** (CSS variables + Tailwind)
- **No bloat** (only install components you use)

This makes it perfect for maintaining brand identity while using common patterns.

---

## Setup

### 1. Initialize shadcn/ui

```bash
npx shadcn@latest init
```

When prompted, choose:
- **Style:** Default
- **Base color:** Neutral (matches our gray scale)
- **CSS variables:** Yes (enables easy theming)

### 2. Configure with Emergence Tokens

Update your `tailwind.config.js` to use Emergence spacing and typography:

```js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
      },
      // Tailwind already uses 4px spacing scale - perfect!
      // Just verify it matches our tokens.json
    },
  },
}
```

### 3. Set Your Brand Color

Edit `app/globals.css` (or wherever shadcn puts CSS variables):

```css
@layer base {
  :root {
    /* Your product's primary color */
    --primary: 221 83% 53%;        /* HSL for your brand color */
    --primary-foreground: 0 0% 100%; /* White text on primary */

    /* Neutrals (keep shadcn defaults, they match our system) */
    --background: 0 0% 100%;
    --foreground: 0 0% 9%;
    /* ... rest of shadcn variables ... */
  }
}
```

**Tip:** Use [Shadcn Theme Generator](https://gradient.page/tools/shadcn-theme-generator) to convert your brand hex color to HSL.

---

## Using Components

### Installation

Install only what you need:

```bash
npx shadcn@latest add button
npx shadcn@latest add input
npx shadcn@latest add card
# ... etc
```

### Basic Usage

Components will be added to your project (usually in `components/ui/`):

```tsx
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Card } from '@/components/ui/card'

export function MyComponent() {
  return (
    <Card className="p-6">
      <h2 className="text-xl font-semibold mb-4">Form Title</h2>
      <form className="space-y-4">
        <Input placeholder="Email" />
        <Button>Submit</Button>
      </form>
    </Card>
  )
}
```

### Customization

Since you own the code, you can modify components:

```tsx
// components/ui/button.tsx

// Add custom variants
const buttonVariants = cva(
  "inline-flex items-center justify-center rounded-md text-sm font-medium",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        // ... other variants ...

        // Add your own!
        brand: "bg-gradient-to-r from-primary to-purple-600",
      },
    },
  }
)
```

---

## Component Recommendations

### Essential Components

Start with these core components:

**Forms:**
- `button` - Primary, secondary, ghost variants
- `input` - Text inputs
- `label` - Form labels
- `textarea` - Multi-line text
- `select` - Dropdowns
- `checkbox` - Checkboxes
- `radio-group` - Radio buttons
- `switch` - Toggle switches

**Layout:**
- `card` - Containers for content
- `separator` - Dividers
- `scroll-area` - Custom scrollbars

**Feedback:**
- `alert` - Notifications and messages
- `toast` - Temporary notifications
- `badge` - Status indicators
- `skeleton` - Loading states

**Overlays:**
- `dialog` - Modals
- `sheet` - Slide-out panels
- `popover` - Floating content
- `dropdown-menu` - Menus
- `tooltip` - Contextual help

### Component Patterns

**Standard Button Hierarchy:**
```tsx
// Primary action
<Button>Save Changes</Button>

// Secondary action
<Button variant="outline">Cancel</Button>

// Tertiary action
<Button variant="ghost">Learn More</Button>

// Destructive action
<Button variant="destructive">Delete</Button>
```

**Form Layout:**
```tsx
<div className="space-y-6">
  <div className="space-y-2">
    <Label htmlFor="email">Email</Label>
    <Input id="email" type="email" placeholder="you@example.com" />
    <p className="text-sm text-gray-500">We'll never share your email.</p>
  </div>

  <div className="space-y-2">
    <Label htmlFor="password">Password</Label>
    <Input id="password" type="password" />
  </div>

  <Button className="w-full">Sign In</Button>
</div>
```

**Card with Header:**
```tsx
<Card>
  <CardHeader>
    <CardTitle>Card Title</CardTitle>
    <CardDescription>Supporting description</CardDescription>
  </CardHeader>
  <CardContent>
    <p>Main content here</p>
  </CardContent>
  <CardFooter>
    <Button>Action</Button>
  </CardFooter>
</Card>
```

---

## Theming for Different Products

Each Emergence product can have its own theme while using the same components.

### Option 1: CSS Variables (Recommended)

Create a theme file for each product:

```css
/* themes/product-a.css */
:root {
  --primary: 221 83% 53%;  /* Blue */
  --primary-foreground: 0 0% 100%;
}

/* themes/product-b.css */
:root {
  --primary: 142 76% 36%;  /* Green */
  --primary-foreground: 0 0% 100%;
}
```

Import the appropriate theme in your app.

### Option 2: Tailwind Theme Extend

```js
// tailwind.config.js for Product A
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: {
          500: '#3b82f6',  // Blue
          600: '#2563eb',
          700: '#1d4ed8',
        },
      },
    },
  },
}

// tailwind.config.js for Product B
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: {
          500: '#22c55e',  // Green
          600: '#16a34a',
          700: '#15803d',
        },
      },
    },
  },
}
```

---

## Customization Guidelines

### When to Customize

✅ **Customize when:**
- Adjusting colors to match brand
- Adding product-specific variants
- Modifying spacing for specific use cases
- Enhancing accessibility
- Adding features specific to your product

❌ **Avoid customizing:**
- Core interaction patterns (breaks familiarity)
- Accessibility features (unless improving)
- Basic component structure (maintain consistency)

### Maintaining Consistency

Even when customizing, maintain:

1. **Spacing scale** - Use Tailwind's spacing classes (4px base)
2. **Typography scale** - Use defined text sizes
3. **Border radius** - Use consistent rounding
4. **Transition timing** - Keep animations quick and subtle
5. **Color patterns** - Follow semantic color usage

---

## Best Practices

### 1. Component Composition

Build complex UIs by composing simple components:

```tsx
// Good - Composed from primitives
function UserCard({ user }) {
  return (
    <Card>
      <CardHeader>
        <CardTitle>{user.name}</CardTitle>
        <CardDescription>{user.email}</CardDescription>
      </CardHeader>
      <CardContent>
        <Badge>{user.role}</Badge>
      </CardContent>
    </Card>
  )
}
```

### 2. Consistent Spacing

Use Tailwind's spacing utilities:

```tsx
// Vertical spacing
<div className="space-y-4">  {/* 16px gaps */}

// Horizontal spacing
<div className="flex gap-3">  {/* 12px gaps */}

// Padding
<div className="p-6">  {/* 24px padding */}
```

### 3. Responsive Design

Use Tailwind's responsive prefixes:

```tsx
<Card className="p-4 md:p-6 lg:p-8">
  {/* Mobile: 16px, Tablet: 24px, Desktop: 32px */}
</Card>
```

### 4. Accessibility First

Always include proper labels and ARIA attributes:

```tsx
// Good
<div>
  <Label htmlFor="search">Search</Label>
  <Input
    id="search"
    type="search"
    aria-label="Search products"
    placeholder="Search..."
  />
</div>

// Bad - Missing label
<Input placeholder="Search..." />
```

### 5. Loading States

Always provide feedback:

```tsx
import { Button } from '@/components/ui/button'
import { Loader2 } from 'lucide-react'

<Button disabled={isLoading}>
  {isLoading && <Loader2 className="mr-2 h-4 w-4 animate-spin" />}
  {isLoading ? 'Saving...' : 'Save Changes'}
</Button>
```

---

## Common Patterns

### Empty States

```tsx
<Card className="p-12 text-center">
  <div className="mx-auto w-12 h-12 rounded-full bg-gray-100 flex items-center justify-center mb-4">
    <InboxIcon className="h-6 w-6 text-gray-400" />
  </div>
  <h3 className="text-lg font-semibold text-gray-900 mb-2">No messages</h3>
  <p className="text-gray-600 mb-6">Get started by sending your first message.</p>
  <Button>Send Message</Button>
</Card>
```

### List Items

```tsx
<div className="divide-y divide-gray-200">
  {items.map(item => (
    <div key={item.id} className="py-4 flex items-center justify-between">
      <div>
        <h4 className="font-medium text-gray-900">{item.title}</h4>
        <p className="text-sm text-gray-600">{item.description}</p>
      </div>
      <Button variant="ghost" size="sm">Edit</Button>
    </div>
  ))}
</div>
```

### Settings Layout

```tsx
<div className="space-y-6">
  <div>
    <h2 className="text-2xl font-semibold mb-2">Settings</h2>
    <p className="text-gray-600">Manage your account preferences</p>
  </div>

  <Separator />

  <div className="space-y-4">
    <div className="flex items-center justify-between">
      <div className="space-y-0.5">
        <Label>Email Notifications</Label>
        <p className="text-sm text-gray-600">Receive updates via email</p>
      </div>
      <Switch />
    </div>

    {/* More settings... */}
  </div>
</div>
```

---

## Resources

**Official shadcn/ui:**
- [Documentation](https://ui.shadcn.com)
- [Component Examples](https://ui.shadcn.com/docs/components)
- [Theme Generator](https://ui.shadcn.com/themes)

**Useful Tools:**
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) - VS Code extension
- [Lucide Icons](https://lucide.dev) - Icon library (used by shadcn)
- [Radix UI](https://www.radix-ui.com) - Underlying primitives

---

## For AI Assistants

When building with shadcn/ui:

1. **Use shadcn/ui components** as the foundation for all UI
2. **Install components as needed** with `npx shadcn@latest add [component]`
3. **Apply Emergence design tokens** via Tailwind classes
4. **Follow spacing patterns** from `spacing.md`
5. **Use typography scale** from `typography.md`
6. **Maintain accessibility** - don't remove ARIA attributes
7. **Compose components** - build complex UIs from simple pieces
8. **Test responsive behavior** - use Tailwind breakpoints

Example component:
```tsx
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card'

export function FeatureCard({ title, description, action }) {
  return (
    <Card className="p-6">  {/* Emergence spacing */}
      <CardHeader className="p-0 mb-4">
        <CardTitle className="text-xl font-semibold">  {/* Emergence typography */}
          {title}
        </CardTitle>
      </CardHeader>
      <CardContent className="p-0">
        <p className="text-gray-600 mb-6">{description}</p>  {/* Emergence colors */}
        <Button onClick={action}>Learn More</Button>
      </CardContent>
    </Card>
  )
}
```

shadcn/ui + Emergence design system = Beautiful, consistent, accessible products with minimal effort.
