# Theme Examples

> Example theme configurations for Emergence products showing how to define brand colors while maintaining the design system.

## Overview

Each Emergence product can have its own primary brand color. These examples show how to configure different color themes while maintaining consistency with the design system.

All themes share:
- Same neutral grays
- Same semantic colors (success, warning, error, info)
- Same spacing and typography
- Same component patterns

Only the **primary brand color** changes.

---

## Available Examples

### [Product A - Blue](./product-a-blue.json)
**Industry:** Productivity
**Personality:** Professional, trustworthy, efficient
**Inspiration:** Linear, Notion

Blue is the most common choice for professional productivity tools. It's trustworthy, familiar, and works well in business contexts.

**Primary color:** `#2563eb`

### [Product B - Purple](./product-b-purple.json)
**Industry:** Creative / Collaboration
**Personality:** Creative, innovative, modern
**Inspiration:** Linear (their purple brand)

Purple conveys creativity and innovation. Great for design tools, creative collaboration, or products that want to feel modern and forward-thinking.

**Primary color:** `#9333ea`

### [Product C - Teal](./product-c-teal.json)
**Industry:** Data / Analytics
**Personality:** Modern, reliable, insightful
**Inspiration:** LogSnag, modern SaaS products

Teal is sophisticated and modern. Excellent for data tools, analytics platforms, or developer products. Feels fresh without being too bold.

**Primary color:** `#0d9488`

---

## How to Use

### 1. Choose a Theme

Pick an example that matches your product's personality, or use it as inspiration to create your own color.

### 2. Apply to Your Project

Each theme file includes two integration methods:

**Option A: CSS Variables (for shadcn/ui)**

Copy the `shadcn.cssVariables` values to your `globals.css`:

```css
@layer base {
  :root {
    /* From the theme file */
    --primary: 221 83% 53%;
    --primary-foreground: 0 0% 100%;

    /* shadcn provides the rest */
  }
}
```

**Option B: Tailwind Config**

Copy the `tailwind.extend.colors` to your `tailwind.config.js`:

```js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#eff6ff',
          100: '#dbeafe',
          // ... rest of scale
          DEFAULT: '#2563eb',
        },
      },
    },
  },
}
```

### 3. Use in Components

```tsx
// Primary button
<Button className="bg-primary-600 hover:bg-primary-700">
  Save Changes
</Button>

// Link
<a href="..." className="text-primary-600 hover:text-primary-700">
  Learn more
</a>

// Badge
<span className="bg-primary-100 text-primary-700 border border-primary-200">
  New
</span>

// Subtle background
<div className="bg-primary-50 p-4">
  Highlighted section
</div>
```

---

## Creating Your Own Theme

### Step 1: Choose Your Color

Pick a primary color that represents your product's personality:

**Color Psychology:**
- **Blue** - Trust, professionalism, stability
- **Purple** - Creativity, innovation, luxury
- **Teal/Cyan** - Modern, fresh, tech-forward
- **Green** - Growth, finance, health
- **Orange** - Energy, enthusiasm, warmth
- **Red** - Urgency, importance, passion
- **Pink** - Friendly, approachable, creative
- **Indigo** - Deep, sophisticated, intelligent

### Step 2: Generate Color Scale

Use one of these tools to generate a full 50-950 scale:

- **[UIColors](https://uicolors.app/create)** - Create Tailwind color scales
- **[Shadcn Theme Generator](https://gradient.page/tools/shadcn-theme-generator)** - Generate shadcn themes
- **[Coolors](https://coolors.co)** - Color palette generator

**Tips:**
- Start with your preferred shade (usually 500 or 600)
- Generate lighter and darker variants
- Ensure good contrast with white and gray backgrounds

### Step 3: Verify Accessibility

Test your primary color for contrast:

**Required ratios:**
- White text on primary-600: **4.5:1** minimum (WCAG AA)
- Primary-600 text on white: **4.5:1** minimum (WCAG AA)

**Tools:**
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Coolors Contrast Checker](https://coolors.co/contrast-checker)

If your color doesn't meet contrast requirements, adjust the shade until it does.

### Step 4: Create Theme File

Copy one of the example JSON files and update:

```json
{
  "name": "Your Product - Color Name",
  "description": "Your product description",

  "metadata": {
    "productName": "Your Product",
    "industry": "Your industry",
    "personality": "Your brand personality",
    "inspiration": "Products that inspired you"
  },

  "colors": {
    "primary": {
      "50": "#...",
      "100": "#...",
      // ... your generated scale
    }
  },

  // ... rest of configuration
}
```

### Step 5: Test in Context

Build a few example components and verify:
- ✅ Buttons look good and are readable
- ✅ Links are visible and accessible
- ✅ Badges and highlights work well
- ✅ Color doesn't clash with the neutral grays
- ✅ Feels appropriate for your product's personality

---

## Guidelines

### Do's

✅ Choose colors that match your product personality
✅ Generate a full 50-950 scale
✅ Verify contrast ratios
✅ Test with actual UI components
✅ Use the same neutral grays as other Emergence products
✅ Keep semantic colors consistent (success, warning, error, info)

### Don'ts

❌ Use multiple primary colors in one product
❌ Create colors that fail accessibility standards
❌ Modify the neutral gray scale
❌ Use overly saturated or neon colors
❌ Change semantic color meanings

---

## Advanced Customization

### Accent Colors

If your product needs a secondary accent color (rare), follow the same process:

```json
{
  "colors": {
    "primary": { /* ... */ },
    "accent": {
      "50": "#...",
      // ... full scale
    }
  }
}
```

Use sparingly and purposefully.

### Dark Mode Adjustments

For dark mode, you may need slightly lighter shades:

```css
@layer base {
  :root {
    --primary: 221 83% 53%;  /* Darker for light mode */
  }

  .dark {
    --primary: 217 91% 60%;  /* Lighter for dark mode */
  }
}
```

This ensures sufficient contrast on dark backgrounds.

---

## Color Combinations

### Testing Your Theme

Create these components to verify your theme works well:

```tsx
// Primary button
<Button>Primary Action</Button>

// Link in text
<p>
  Read more about our <a href="...">product features</a>.
</p>

// Status badge
<span className="badge">Active</span>

// Highlighted card
<Card className="border-l-4 border-primary-600 bg-primary-50">
  <CardContent>Important information</CardContent>
</Card>

// Icon with accent
<CheckCircle className="text-primary-600" />
```

If all of these look good and feel cohesive, your theme is ready!

---

## Resources

**Color Tools:**
- [UIColors](https://uicolors.app/create)
- [Shadcn Theme Generator](https://gradient.page/tools/shadcn-theme-generator)
- [Coolors](https://coolors.co)
- [Adobe Color](https://color.adobe.com)

**Contrast Checkers:**
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Coolors Contrast Checker](https://coolors.co/contrast-checker)
- [Accessible Colors](https://accessible-colors.com)

**Inspiration:**
- [Linear](https://linear.app) - Purple theme
- [Notion](https://notion.com) - Neutral with subtle tints
- [Todoist](https://todoist.com) - Red theme
- [LogSnag](https://logsnag.com) - Teal theme

---

## Support

Need help choosing a color or creating a theme?

1. Start with the examples in this directory
2. Use the color generation tools linked above
3. Test with actual components
4. Iterate until it feels right

Remember: The right color should feel appropriate for your product's personality while maintaining the professional, modern aesthetic of the Emergence family.
