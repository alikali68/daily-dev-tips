---
# The 12-Column Grid: The Layout System Behind Most Professional Designs

Most polished layouts you admire — websites, posters, editorial spreads — sit on a 12-column grid, and 12 is no accident: it divides evenly by 2, 3, 4, and 6, so one system covers halves, thirds, quarters, and sixths without custom math. Start by defining your columns and gutters first, then place every element on the grid instead of nudging things by eye; if an element spans 4 columns on desktop, it should span a clean fraction (like 6 or 12) on mobile, not an arbitrary width. Keep one consistent gutter width across the whole design — inconsistent gutters are the fastest way to make a clean layout feel sloppy. And remember the grid is a tool, not a cage: breaking it deliberately for one hero element creates emphasis precisely because everything else obeys it.

```css
.layout {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 24px; /* one consistent gutter */
}
.hero { grid-column: span 8; }
.sidebar { grid-column: span 4; }
```

**Why it matters:** A shared grid makes every page feel intentional and consistent, speeds up layout decisions, and keeps designs responsive without redesigns at every breakpoint.

#Design #GridSystem #GraphicDesign #WebDesign
---
