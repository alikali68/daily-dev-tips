# Lazy-Load Images with Intersection Observer

Loading every image on page load wastes bandwidth and slows your Largest Contentful Paint, especially on image-heavy pages. Instead of attaching a scroll listener that fires dozens of times per second, use the browser's Intersection Observer API: it tells you exactly when an element enters (or nears) the viewport, with zero scroll-event overhead. Keep the real URL in `data-src` and swap it into `src` only when the image is about to appear — add a `rootMargin` like `200px` so images start loading just before they scroll into view, and call `unobserve()` after loading so the observer stops watching. This pattern also pairs well with native `loading="lazy"` as a fallback, but the observer gives you full control over timing, placeholders, and fade-in transitions.

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (!entry.isIntersecting) return;
    const img = entry.target;
    img.src = img.dataset.src;
    observer.unobserve(img);
  });
}, { rootMargin: "200px" });

document.querySelectorAll("img[data-src]").forEach((img) => observer.observe(img));
```

**Why it matters:** Faster initial loads, less wasted bandwidth, and smoother scrolling — a small change users on slow connections feel immediately.

#Frontend #WebPerformance #JavaScript #WebDev
