# Respect `prefers-reduced-motion`: Animations That Don't Hurt

Not everyone experiences motion the same way. For people with vestibular disorders, migraines, or motion sensitivity, parallax effects, auto-playing carousels, and sweeping transitions can trigger dizziness or nausea — and roughly one in three people report some motion sensitivity. The fix is a single media query: wrap your animations in `@media (prefers-reduced-motion: reduce)` and provide a calm alternative, or turn the motion off entirely. Better still, design motion-first with a reduced-motion baseline and layer animation on top only when the user hasn't asked for less.

```css
/* Default: calm, instant state changes */
.card { transition: none; }

/* Only animate when the user is comfortable with motion */
@media (prefers-reduced-motion: no-preference) {
  .card { transition: transform 0.3s ease; }
  .card:hover { transform: translateY(-4px); }
}
```

This "opt-in to motion" pattern is more robust than the common approach of disabling animations inside a `reduce` block, because it also covers browsers and users who never set a preference. Apply the same thinking to JavaScript-driven motion: check `window.matchMedia('(prefers-reduced-motion: reduce)').matches` before starting carousels, counters, or scroll-linked effects.

**Why it matters:** Motion is decoration; comfort is the product. A site that respects the user's motion preference is usable by more people, with almost no extra code.

#CSS #WebDev #Accessibility #UX #Frontend
