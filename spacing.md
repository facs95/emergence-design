# Spacing System

> Consistent spacing is the secret to creating visual rhythm and making products feel like they belong to the same family.

## Base Unit: 4px

Everything in the Emergence design system uses a **4px base unit**. This creates:
- Visual consistency across products
- Easy mental math (multiples of 4)
- Alignment to pixel grid (crisp rendering)
- Natural rhythm in layouts

---

## The Spacing Scale

All spacing values are multiples of 4px (0.25rem):

```
Value   Pixels   Rem      Common Uses
─────────────────────────────────────────────────────────
0       0px      0        Reset/none
px      1px      —        Borders, dividers
0.5     2px      0.125rem Tight spacing
1       4px      0.25rem  Minimal spacing
1.5     6px      0.375rem Between icon and text
2       8px      0.5rem   Small gaps
2.5     10px     0.625rem Compact spacing
3       12px     0.75rem  Standard small spacing
3.5     14px     0.875rem Between related items
4       16px     1rem     Standard spacing (base)
5       20px     1.25rem  Comfortable spacing
6       24px     1.5rem   Section spacing
8       32px     2rem     Large spacing
10      40px     2.5rem   Extra large spacing
12      48px     3rem     Major sections
16      64px     4rem     Page sections
20      80px     5rem     Large page sections
24      96px     6rem     Hero/landing spacing
```

**Most commonly used:**
- **2, 3, 4** - Component internals (padding, small gaps)
- **4, 6, 8** - Between components
- **8, 12, 16** - Section spacing
- **16, 20, 24** - Page-level spacing

---

## Spacing Principles

### 1. Use the Scale, Nothing Else

```
✅ Good
padding: 1rem;      /* 16px - from scale */
margin: 1.5rem;     /* 24px - from scale */
gap: 0.75rem;       /* 12px - from scale */

❌ Avoid
padding: 15px;      /* Arbitrary value */
margin: 22px;       /* Not on scale */
gap: 18px;          /* Off-scale */
```

### 2. Increase Spacing as You Zoom Out

**Visual hierarchy through spacing:**

```
Icon to text:      1.5  (6px)   - Very related
Within button:     2, 3 (8-12px) - Compact
Between inputs:    4    (16px)  - Related
Between sections:  6, 8 (24-32px) - Separated
Page sections:     12+  (48px+) - Major divisions
```

### 3. Consistent Internal Spacing

Components of the same type should have the same internal spacing:

```
✅ All buttons use the same padding
Small button:  py-2 px-3  (8px × 12px)
Medium button: py-2.5 px-4 (10px × 16px)
Large button:  py-3 px-6  (12px × 24px)

✅ All cards use the same padding
Card: p-6 (24px)
Compact card: p-4 (16px)
```

### 4. Use Multiples for Harmony

Stack spacing in harmonious multiples:

```
✅ Good progression
Container padding: 6  (24px)
Section gap:       8  (32px)
Page margin:       12 (48px)

❌ Random values
Container padding: 5  (20px)
Section gap:       7  (28px)
Page margin:       11 (44px)
```

---

## Common Patterns

### Component Padding

```
Compact components:  p-2 to p-3   (8-12px)
Standard components: p-4 to p-6   (16-24px)
Large components:    p-6 to p-8   (24-32px)
```

**Examples:**
- **Button:** `px-4 py-2` (16px × 8px)
- **Input:** `px-3 py-2` (12px × 8px)
- **Card:** `p-6` (24px)
- **Modal:** `p-6 to p-8` (24-32px)
- **Page container:** `px-6 py-8` or `px-8 py-12`

### Vertical Spacing (Stacks)

```
Tightly related:     space-y-1 to space-y-2   (4-8px)
Related:             space-y-3 to space-y-4   (12-16px)
Distinct sections:   space-y-6 to space-y-8   (24-32px)
Major sections:      space-y-12 to space-y-16 (48-64px)
```

**Example:**
```html
<div class="space-y-8">
  <!-- Section 1: 32px gap below -->
  <section class="space-y-4">
    <h2>Title</h2>
    <p>Content</p> <!-- 16px gap between -->
  </section>

  <!-- Section 2: 32px gap from section 1 -->
  <section class="space-y-4">
    <h2>Title</h2>
    <p>Content</p>
  </section>
</div>
```

### Horizontal Spacing (Inline)

```
Icon + text:         gap-1.5 to gap-2  (6-8px)
Inline buttons:      gap-2 to gap-3    (8-12px)
Toolbar items:       gap-3 to gap-4    (12-16px)
Navigation items:    gap-4 to gap-6    (16-24px)
```

### Grid Gaps

```
Tight grid:          gap-2 to gap-3   (8-12px)
Standard grid:       gap-4 to gap-6   (16-24px)
Loose grid:          gap-6 to gap-8   (24-32px)
```

**Example:**
```html
<div class="grid grid-cols-3 gap-6">
  <div>Card 1</div>
  <div>Card 2</div>
  <div>Card 3</div>
</div>
```

---

## Layout Spacing

### Page Container

```html
<div class="container mx-auto px-6 py-12">
  <!-- Horizontal padding: 24px -->
  <!-- Vertical padding: 48px -->
</div>
```

### Sections

```html
<main class="space-y-16">
  <!-- 64px between major sections -->

  <section class="space-y-6">
    <!-- 24px between section elements -->
    <h2>Section Title</h2>
    <div>Content</div>
  </section>

  <section class="space-y-6">
    <h2>Section Title</h2>
    <div>Content</div>
  </section>
</main>
```

### Form Spacing

```html
<form class="space-y-6">
  <!-- 24px between form groups -->

  <div class="space-y-2">
    <!-- 8px between label and input -->
    <label>Email</label>
    <input />
    <p class="text-sm text-gray-600">Helper text</p>
  </div>

  <div class="space-y-2">
    <label>Password</label>
    <input />
  </div>

  <button>Submit</button>
</form>
```

---

## Responsive Spacing

Scale down spacing on mobile devices:

```css
/* Desktop */
.section { padding: 3rem; }      /* 48px */
.container { gap: 2rem; }        /* 32px */

/* Tablet */
@media (max-width: 1024px) {
  .section { padding: 2rem; }    /* 32px */
  .container { gap: 1.5rem; }    /* 24px */
}

/* Mobile */
@media (max-width: 768px) {
  .section { padding: 1.5rem; }  /* 24px */
  .container { gap: 1rem; }      /* 16px */
}
```

**Tailwind approach:**
```html
<div class="p-6 md:p-8 lg:p-12">
  <!-- Mobile: 24px, Tablet: 32px, Desktop: 48px -->
</div>
```

---

## Special Cases

### Touch Targets (Mobile)

Minimum **44px × 44px** for interactive elements:

```html
<button class="h-11 px-4">
  <!-- Height: 44px (11 × 4px) -->
  <!-- Horizontal padding: 16px -->
</button>
```

### Optical Adjustments

Sometimes you need to break the rule for visual balance:

```
Icons in buttons might need different spacing than text
Logos might need custom spacing for optical alignment
```

**Rule:** Use the scale first. Only deviate with good reason and document why.

---

## Common Mistakes

### ❌ Arbitrary Values

```css
/* Don't */
margin: 17px;
padding: 23px;
gap: 14px;
```

### ❌ Inconsistent Component Spacing

```html
<!-- Don't mix padding within same component type -->
<button class="px-4 py-2">Button 1</button>
<button class="px-5 py-3">Button 2</button>  <!-- Different! -->
```

### ❌ Not Enough Whitespace

```html
<!-- Don't cram everything together -->
<div class="p-2 space-y-1">
  <!-- Too tight, hard to scan -->
</div>
```

### ❌ Too Much Whitespace

```html
<!-- Don't create unnecessary distance -->
<form class="space-y-16">
  <!-- 64px between form fields is too much -->
</form>
```

---

## Quick Reference

**Component Internals:**
- Button padding: `px-4 py-2` to `px-6 py-3`
- Input padding: `px-3 py-2`
- Card padding: `p-4` to `p-6`
- Modal padding: `p-6` to `p-8`

**Between Elements:**
- Tightly related: `gap-2` (8px)
- Related: `gap-4` (16px)
- Sections: `gap-6` to `gap-8` (24-32px)
- Major sections: `gap-12` (48px)

**Page Level:**
- Container padding: `px-6 py-12` to `px-8 py-16`
- Section spacing: `space-y-12` to `space-y-16`

---

## For AI Assistants

When implementing spacing:

1. **Always use values from the spacing scale** in `tokens.json`
2. **Start with standard patterns** from this guide
3. **Increase spacing as you zoom out** (hierarchy principle)
4. **Keep component spacing consistent** across the same component types
5. **Use Tailwind spacing utilities** that map to these values
6. **Scale down on mobile** using responsive classes

Example:
```html
<div class="p-6 space-y-4 md:p-8 md:space-y-6">
  <!-- Mobile: 24px padding, 16px gap -->
  <!-- Desktop: 32px padding, 24px gap -->

  <h2>Section Title</h2>
  <p>Content here</p>
</div>
```

The spacing system works seamlessly with shadcn/ui components, which already follow similar 4px-based spacing principles.
