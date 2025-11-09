# Color System

> Each Emergence product has its own brand colors, but shares a common approach to color usage and accessibility.

## Philosophy

Unlike typography and spacing (which are consistent across all products), **colors are product-specific**. Each product in the Emergence family will have its own primary brand color, but they all share:

- **Common neutral grays** for UI chrome
- **Semantic colors** for success, warning, error, info
- **Similar color usage patterns**
- **Consistent accessibility standards**

Think: Different personalities (colors) but same values (usage patterns).

---

## The Color System

### 1. Neutrals (Shared Across All Products)

Every product uses the same neutral gray scale:

```
gray-50:  #fafafa  → Subtle backgrounds
gray-100: #f5f5f5  → Light backgrounds
gray-200: #e5e5e5  → Borders, dividers (light mode)
gray-300: #d4d4d4  → Disabled states
gray-400: #a3a3a3  → Placeholder text
gray-500: #737373  → Secondary text
gray-600: #525252  → Primary text (light backgrounds)
gray-700: #404040  → Emphasized text
gray-800: #262626  → Dark backgrounds
gray-900: #171717  → Primary text (dark mode)
gray-950: #0a0a0a  → Very dark backgrounds
```

**Why these grays?**
- Neutral (no color cast)
- Excellent contrast ratios
- Work well with any brand color
- Match the aesthetic of Linear, Notion, etc.

### 2. Primary Color (Product-Specific)

Each product defines its own primary color with a full scale:

```
primary-50   → Very light tint
primary-100  → Light tint
primary-200  → Subtle
primary-300  → Muted
primary-400  → Soft
primary-500  → Base (main brand color)
primary-600  → Emphasis (buttons, links)
primary-700  → Hover states
primary-800  → Active states
primary-900  → Very dark
primary-950  → Darkest
```

**See example themes** in `/examples/themes/` for reference.

### 3. Semantic Colors (Shared)

These communicate meaning and are consistent across all products:

**Success (Green):**
```
success-500: #22c55e  → Base
success-600: #16a34a  → Hover/emphasis
success-700: #15803d  → Active
```

**Warning (Amber):**
```
warning-500: #f59e0b  → Base
warning-600: #d97706  → Hover/emphasis
warning-700: #b45309  → Active
```

**Error (Red):**
```
error-500: #ef4444  → Base
error-600: #dc2626  → Hover/emphasis
error-700: #b91c1c  → Active
```

**Info (Blue):**
```
info-500: #3b82f6  → Base
info-600: #2563eb  → Hover/emphasis
info-700: #1d4ed8  → Active
```

---

## Color Usage Patterns

### Text Colors

```
Primary text:     gray-900 (light mode) / gray-100 (dark mode)
Secondary text:   gray-600 (light mode) / gray-400 (dark mode)
Tertiary text:    gray-500 (light mode) / gray-500 (dark mode)
Disabled text:    gray-400 (light mode) / gray-600 (dark mode)
Placeholder:      gray-400 (light mode) / gray-500 (dark mode)
```

**Example:**
```html
<h2 class="text-gray-900">Main Heading</h2>
<p class="text-gray-600">Supporting description</p>
<span class="text-gray-500">Metadata or timestamp</span>
```

### Background Colors

```
Page background:        white / gray-950
Subtle background:      gray-50 / gray-900
Raised surface (card):  white / gray-800
Hover state:            gray-100 / gray-800
Active state:           gray-200 / gray-700
```

### Border Colors

```
Default border:    gray-200 (light) / gray-800 (dark)
Subtle border:     gray-100 (light) / gray-900 (dark)
Emphasis border:   gray-300 (light) / gray-700 (dark)
Focus ring:        primary-500 with opacity
```

### Interactive Elements

**Buttons (Primary):**
```
Background:  primary-600
Hover:       primary-700
Active:      primary-800
Text:        white
```

**Buttons (Secondary):**
```
Background:  white / gray-800
Border:      gray-300 / gray-700
Hover bg:    gray-50 / gray-700
Text:        gray-900 / gray-100
```

**Buttons (Ghost):**
```
Background:  transparent
Hover bg:    gray-100 / gray-800
Text:        gray-700 / gray-300
```

**Links:**
```
Default:     primary-600
Hover:       primary-700
Visited:     primary-800 (optional)
```

---

## Choosing a Primary Color

When creating a new product, choose a primary color that:

1. **Reflects the product personality**
   - Professional tool → Blue, purple, gray
   - Creative tool → Orange, pink, teal
   - Financial → Blue, green
   - Communication → Blue, purple

2. **Has good contrast**
   - Works on white backgrounds
   - Text remains readable
   - Accessible at all required sizes

3. **Feels sophisticated**
   - Avoid overly saturated colors
   - Test with the neutral grays
   - Should feel modern and professional

4. **Generate a full scale**
   - Use tools like [Tailwind Color Generator](https://uicolors.app/create)
   - Or [Shadcn Theme Generator](https://gradient.page/tools/shadcn-theme-generator)
   - Create 50-950 shades

**Good examples:**
- **Linear:** Purple (`#5E6AD2`)
- **Notion:** Gray/neutral with subtle tints
- **Todoist:** Red (`#DB4C3F`)
- **LogSnag:** Teal/cyan

---

## Accessibility Requirements

### Contrast Ratios (WCAG)

**Minimum (AA):**
- Normal text: 4.5:1
- Large text (≥24px): 3:1
- UI components: 3:1

**Enhanced (AAA):**
- Normal text: 7:1
- Large text: 4.5:1

### Testing

Always test your color combinations:

**Tools:**
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Coolors Contrast Checker](https://coolors.co/contrast-checker)
- Browser DevTools (Chrome, Firefox)

**Common combinations to verify:**
```
✅ gray-900 on white       → 18.2:1 (Excellent)
✅ gray-600 on white       → 7.2:1  (AAA)
✅ primary-600 on white    → Test this!
✅ white on primary-600    → Test this!
✅ success-700 on white    → 4.8:1  (AA)
```

### Color Blindness

- **Never use color alone** to communicate information
- Combine with icons, labels, or patterns
- Test with tools like [Color Oracle](https://colororacle.org/)

**Examples:**
```
✅ Good
<button class="bg-red-500">
  <XIcon /> Delete
</button>

❌ Avoid
<div class="text-red-500">Error</div>  <!-- Color only -->
```

---

## Dark Mode

### Approach

**Option 1: Full dark mode support**
- Define dark variants for all colors
- Use Tailwind's `dark:` modifier
- Provide mode toggle

**Option 2: Light mode only**
- Simpler to maintain initially
- Can add dark mode later
- Many B2B SaaS products are light-only

### If Supporting Dark Mode

```css
/* Light mode */
background: white;
text: gray-900;
border: gray-200;

/* Dark mode */
background: gray-950;
text: gray-100;
border: gray-800;
```

**Primary color adjustments:**
- Use lighter shades in dark mode (400-500)
- Use darker shades in light mode (600-700)
- Ensures sufficient contrast

```html
<button class="bg-primary-600 dark:bg-primary-500">
  Click me
</button>
```

---

## Best Practices

### 1. Limit Your Palette

Within a single product, use:
- **1 primary color** (your brand)
- **4 semantic colors** (success, warning, error, info)
- **Neutral grays** for everything else

Don't introduce extra colors without purpose.

### 2. Use Color Meaningfully

```
✅ Good
- Primary → Main actions, brand elements
- Success → Confirmations, completed states
- Warning → Cautions, important notices
- Error → Errors, destructive actions
- Gray → Everything else

❌ Avoid
- Random colors for decoration
- Too many accent colors
- Color without meaning
```

### 3. Consistent State Colors

```
Interactive element states:

Default:  primary-600
Hover:    primary-700    (darker)
Active:   primary-800    (even darker)
Disabled: gray-300       (desaturated)
```

### 4. Subtle Backgrounds

For backgrounds, use very light tints:

```
✅ Subtle
bg-gray-50    (very light gray)
bg-blue-50    (barely blue)

❌ Too strong
bg-gray-300   (too gray)
bg-blue-200   (too blue)
```

### 5. Test in Context

Always preview colors:
- With actual content
- Next to other UI elements
- On different screen types
- In different lighting conditions

---

## Common Patterns

### Status Indicators

```html
<!-- Success -->
<div class="flex items-center gap-2 text-green-700">
  <CheckIcon class="text-green-600" />
  <span>Completed successfully</span>
</div>

<!-- Warning -->
<div class="flex items-center gap-2 text-amber-700">
  <AlertIcon class="text-amber-600" />
  <span>Action required</span>
</div>

<!-- Error -->
<div class="flex items-center gap-2 text-red-700">
  <XIcon class="text-red-600" />
  <span>Failed to save</span>
</div>
```

### Badges

```html
<span class="bg-primary-100 text-primary-700 px-2 py-1 rounded-md text-sm">
  New
</span>

<span class="bg-green-100 text-green-700 px-2 py-1 rounded-md text-sm">
  Active
</span>

<span class="bg-gray-100 text-gray-700 px-2 py-1 rounded-md text-sm">
  Draft
</span>
```

### Cards

```html
<div class="bg-white border border-gray-200 rounded-lg p-6">
  <h3 class="text-gray-900 font-semibold">Card Title</h3>
  <p class="text-gray-600 mt-2">Card content</p>
</div>
```

---

## For AI Assistants

When implementing colors:

1. **Use neutrals from `tokens.json`** for UI chrome (text, borders, backgrounds)
2. **Ask for the primary brand color** if not provided, or suggest options
3. **Use semantic colors** for success/warning/error/info states
4. **Always check contrast ratios** - aim for WCAG AA minimum
5. **Follow the usage patterns** above for consistency
6. **Reference shadcn/ui themes** for examples of good color usage
7. **Document the color choices** if creating a new product theme

Example theme configuration:
```json
{
  "name": "Product Name",
  "primary": {
    "500": "#3b82f6",
    "600": "#2563eb",
    "700": "#1d4ed8"
  }
}
```

shadcn/ui makes it easy to define custom color themes while maintaining all the semantic and neutral colors from the base system.
