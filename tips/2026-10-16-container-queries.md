# Container Queries: Components That Respond to Their Container

Media queries respond to the viewport — container queries let a component respond to the width of its own container. Define a container with `container-type: inline-size`, then style against it with `@container`. The same card component can now adapt whether it sits in a sidebar, a three-column grid, or full-width, without a single viewport breakpoint.

```css
.card-wrapper {
  container-type: inline-size;
}

@container (min-width: 480px) {
  .card {
    display: grid;
    grid-template-columns: 160px 1fr;
  }
}
```

One detail people miss: once an element becomes a query container, percentage heights of its children resolve against it differently — so test the layout inside the container, not the page. Support is solid in all modern browsers since 2023, and it's safe progressive enhancement: older browsers just get your base styles.

**Why it matters:** truly reusable components shouldn't care where they're placed — container queries make "build once, drop anywhere" layouts real.

#Frontend #CSS #WebDev #ResponsiveDesign
