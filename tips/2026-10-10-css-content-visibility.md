# Lazy-render off-screen content with `content-visibility`

Long pages waste render time on sections the user hasn't scrolled to yet. CSS `content-visibility: auto` tells the browser to skip rendering off-screen elements entirely until they're needed.

```css
.below-the-fold {
  content-visibility: auto;
  contain-intrinsic-size: auto 500px; /* reserve space to avoid layout shift */
}
```

**Why it matters:** less initial rendering work means faster Largest Contentful Paint and better Interaction to Next Paint — two of the three Core Web Vitals Google ranks you on. On content-heavy pages this alone can shave hundreds of milliseconds.

**Watch out:** always pair it with `contain-intrinsic-size`, otherwise the scrollbar jumps as sections render. Don't apply it to above-the-fold content.

#CSS #WebPerformance #Frontend #CoreWebVitals
