# Use a Modular Type Scale for Consistent Typography

Random font sizes make a design feel messy, even when the colors and layout are right. A modular scale fixes that: pick one ratio — 1.25 (the "major third") is a safe starting point — and derive every size from it. Start with a 16px body size, then multiply by the ratio for each step up: 20px, 25px, 31px, 39px. Every heading, subheading, and caption is now mathematically related instead of eyeballed. In CSS, define the scale once as custom properties and reuse them everywhere:

```css
:root {
  --text-base: 1rem;
  --text-lg: 1.25rem;
  --text-xl: 1.563rem;
  --text-2xl: 1.953rem;
}

h1 { font-size: var(--text-2xl); }
h2 { font-size: var(--text-xl); }
```

For extra polish, wrap the steps in `clamp()` so the scale breathes with the viewport instead of jumping at breakpoints. And pick one ratio per project and stick to it — consistency is what makes a type system feel designed rather than improvised.

**Why it matters:** A shared ratio turns arbitrary font sizes into a system, so your typography looks intentional on every screen.

#Typography #GraphicDesign #WebDesign #DesignTips
