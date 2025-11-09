# Typography Guidelines

> Typography creates rhythm, hierarchy, and personality. It's one of the strongest signals of the Emergence family identity.

## Font Family

### Primary: Inter

**Why Inter?**
- Designed specifically for digital interfaces
- Excellent readability at all sizes
- Wide range of weights (we use 400, 500, 600, 700)
- Open source and free
- Widely cached (performance benefit)
- Used by many modern SaaS products

**Alternatives:** If a product needs a different feel, consider:
- SF Pro (Apple-like)
- Geist (Vercel's font, similar to Inter)
- System fonts (best performance)

### Monospace: JetBrains Mono

For code blocks, technical content, or when you need monospace:
- JetBrains Mono (primary)
- Fira Code (alternative)
- Fallback to system monospace

---

## Type Scale

Based on a modular scale with a 16px base:

```
xs:   12px / 0.75rem   → Small labels, captions
sm:   14px / 0.875rem  → Secondary text, metadata
base: 16px / 1rem      → Body text, primary content
lg:   18px / 1.125rem  → Emphasized body text
xl:   20px / 1.25rem   → Small headings, subheadings
2xl:  24px / 1.5rem    → Section headings
3xl:  30px / 1.875rem  → Page headings
4xl:  36px / 2.25rem   → Large headings
5xl:  48px / 3rem      → Hero headings
6xl:  60px / 3.75rem   → Marketing/landing pages
7xl:  72px / 4.5rem    → Large marketing content
```

**Usage:**
- Stick to this scale - don't create arbitrary sizes
- Most UI will use sm, base, and lg
- Headings use xl through 5xl
- Reserve 6xl and 7xl for marketing/landing pages

---

## Font Weights

**Use only these weights:**

- **400 (Regular)** - Body text, most content
- **500 (Medium)** - Subtle emphasis, labels
- **600 (Semibold)** - Headings, buttons, strong emphasis
- **700 (Bold)** - Rare, only for very strong emphasis

**Guidelines:**
- Default to 400 for readability
- Use 500 for UI elements (buttons, tabs, labels)
- Use 600 for headings
- Avoid 700 unless absolutely necessary (it can feel heavy)

---

## Line Height

**Ratios based on content type:**

```
tight:   1.25  → Large headings (4xl+)
snug:    1.375 → Headings (xl-3xl)
normal:  1.5   → Body text (default)
relaxed: 1.625 → Long-form content
loose:   2     → Special cases only
```

**Rules:**
- Larger text = tighter line-height
- Body text should be 1.5 (excellent for readability)
- Dense UIs can use 1.375-1.5
- Long-form content (blog posts, docs) use 1.625

**Example:**
```css
h1 { line-height: 1.25; }  /* Large heading */
h2 { line-height: 1.375; } /* Medium heading */
p  { line-height: 1.5; }   /* Body text */
```

---

## Letter Spacing

**Use sparingly:**

```
tight:   -0.025em → Large headings (optional)
normal:  0        → Default, most text
wide:    0.025em  → Small caps, labels
```

**Guidelines:**
- Most text should use normal (0)
- Slight negative tracking (-0.025em) can help large headings
- Slight positive tracking (0.025em) helps small ALL CAPS text
- Avoid extreme values

---

## Hierarchy Patterns

### Standard Page Hierarchy

```
Page Title:    3xl / semibold (30px, 600 weight)
Section Title: 2xl / semibold (24px, 600 weight)
Subsection:    xl / semibold  (20px, 600 weight)
Body Text:     base / normal  (16px, 400 weight)
Secondary:     sm / normal    (14px, 400 weight)
Caption:       xs / normal    (12px, 400 weight)
```

### UI Component Hierarchy

```
Modal Title:     lg / semibold  (18px, 600 weight)
Card Title:      base / semibold (16px, 600 weight)
Button Text:     sm / medium    (14px, 500 weight)
Input Label:     sm / medium    (14px, 500 weight)
Input Text:      base / normal  (16px, 400 weight)
Helper Text:     xs / normal    (12px, 400 weight)
Badge/Tag Text:  xs / medium    (12px, 500 weight)
```

---

## Best Practices

### 1. Contrast Through Size and Weight

Create hierarchy by varying both size AND weight:

```
✅ Good
<h2 class="text-2xl font-semibold">Section Title</h2>
<p class="text-base font-normal">Body content here</p>

❌ Avoid
<h2 class="text-2xl font-bold">Section Title</h2>  <!-- Too heavy -->
<p class="text-base font-medium">Body content here</p> <!-- Body shouldn't be medium -->
```

### 2. Comfortable Reading Width

**65-75 characters per line** is optimal for readability.

```css
.prose {
  max-width: 65ch; /* About 650-680px */
}
```

Wider than 75 characters makes text harder to read. Use the `maxWidth.prose` token.

### 3. Pair Sizes Thoughtfully

Create clear distinction between levels:

```
✅ Good pairs
h1: 3xl (30px) + body: base (16px)  → 14px difference
h2: 2xl (24px) + body: base (16px)  → 8px difference

❌ Too close
h2: xl (20px) + body: lg (18px)     → Only 2px difference
```

### 4. Responsive Typography

Scale down on mobile:

```css
/* Desktop */
h1 { font-size: 3rem; }     /* 48px */

/* Mobile */
@media (max-width: 768px) {
  h1 { font-size: 2.25rem; } /* 36px */
}
```

Use the breakpoints from `tokens.json`.

### 5. Avoid Faux Emphasis

```
✅ Use semantic HTML and proper weights
<strong class="font-semibold">Important text</strong>
<em class="italic">Emphasized text</em>

❌ Don't use color alone
<span class="text-blue-500">Important text</span>  /* Accessibility issue */
```

---

## Common Patterns

### Text Block with Label

```html
<div>
  <label class="text-sm font-medium text-gray-700">
    Email Address
  </label>
  <p class="text-base text-gray-900">
    user@example.com
  </p>
</div>
```

### Card with Hierarchy

```html
<div class="card">
  <h3 class="text-lg font-semibold text-gray-900">
    Card Title
  </h3>
  <p class="text-sm text-gray-600 mt-1">
    Supporting description or metadata
  </p>
  <p class="text-base text-gray-700 mt-4">
    Main card content goes here
  </p>
</div>
```

### List with Secondary Text

```html
<div>
  <h4 class="text-base font-medium text-gray-900">
    Primary Item Text
  </h4>
  <p class="text-sm text-gray-600">
    Secondary information or timestamp
  </p>
</div>
```

---

## Accessibility

### Minimum Text Sizes

- **Never go below 12px (0.75rem)** for UI text
- **16px minimum** for body content
- **14px minimum** for form inputs (prevents iOS zoom)

### Color Contrast

- **Normal text (< 24px):** 4.5:1 contrast ratio minimum
- **Large text (≥ 24px):** 3:1 contrast ratio minimum
- **Aim for WCAG AAA:** 7:1 for normal text, 4.5:1 for large

Use tools like WebAIM Contrast Checker to verify.

### Readability

- **Line length:** 65-75 characters
- **Line height:** 1.5 minimum for body text
- **Paragraph spacing:** At least 1.5x line height
- **Letter spacing:** Avoid extreme values

---

## For AI Assistants

When implementing typography:

1. **Always use the type scale** from `tokens.json`
2. **Use semantic HTML** (`h1`-`h6`, `p`, `strong`, `em`)
3. **Follow the hierarchy patterns** above for consistency
4. **Check color contrast** for accessibility
5. **Use CSS custom properties** or Tailwind classes that reference the tokens
6. **Apply responsive scaling** on mobile devices

Example Tailwind usage:
```html
<h1 class="text-3xl font-semibold leading-tight">
  Page Title
</h1>
<p class="text-base leading-normal text-gray-700">
  Body content with good readability
</p>
```

The typography system is designed to work seamlessly with shadcn/ui components, which already follow similar principles.
