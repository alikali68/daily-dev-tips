# Use CSS Logical Properties for RTL-Ready Layouts

Hard-coding `margin-left`, `padding-right`, or `left`/`right` bakes a left-to-right assumption into your CSS. The moment your site needs Arabic, Persian, or Hebrew support, every one of those declarations has to be overridden or duplicated. CSS logical properties solve this at the source: they map to the writing direction instead of the physical screen.

Instead of `margin-left`, use `margin-inline-start`; instead of `padding-right`, use `padding-inline-end`; instead of `left`, use `inset-inline-start`. The browser flips them automatically when `dir="rtl"` is set — no overrides, no second stylesheet, no `[dir="rtl"]` hacks.

```css
.card {
  margin-inline-start: 1rem;   /* left in LTR, right in RTL */
  padding-inline-end: 1.5rem;  /* right in LTR, left in RTL */
  text-align: start;           /* follows the document direction */
  border-inline-start: 2px solid currentColor;
}
```

Logical properties also cover block flow (`margin-block-start` instead of `margin-top`) and sizing (`inline-size` instead of `width`), so the same code adapts to vertical writing modes too. Browser support is universal in modern browsers, and the physical properties remain available for the rare cases where direction truly shouldn't flip, like a logo lockup.

**Why it matters:** One stylesheet that works in every language means fewer bugs, less CSS, and a product that respects its users' reading direction from day one.

#CSS #Frontend #WebDev #RTL #Accessibility
