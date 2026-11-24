# Scroll-Driven Animations: Let the Scrollbar Drive Your CSS

CSS scroll-driven animations let you tie an animation's progress directly to scrolling — no JavaScript, no scroll listeners, no IntersectionObserver boilerplate. With `animation-timeline: scroll()` (or `view()` for element visibility), a progress bar, a fading hero, or a parallax effect becomes a few lines of declarative CSS.

```css
.progress-bar {
  animation: grow linear;
  animation-timeline: scroll();
  transform-origin: left;
}
@keyframes grow {
  from { transform: scaleX(0); }
  to   { transform: scaleX(1); }
}
```

Because the browser drives the animation on the compositor thread, it stays smooth even on long pages — and it respects `prefers-reduced-motion` if you gate it behind that media query. Browser support is now solid in Chrome, Edge and Safari, with Firefox catching up; a `@supports (animation-timeline: scroll())` guard keeps older browsers on a static fallback.

**Why it matters:** scroll-linked motion used to mean JavaScript listeners and jank; now it's native CSS — cheaper to write, smoother to run, and easier to maintain.

#CSS #WebDev #Frontend #Animation #UX
