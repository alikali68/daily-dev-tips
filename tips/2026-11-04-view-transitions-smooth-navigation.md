# Smooth Page Transitions with the View Transitions API

Single-page apps made animated navigation feel normal, but multi-page sites were left behind — every click meant a hard cut to a new document. The View Transitions API changes that: wrap your DOM update in `document.startViewTransition(() => updateDOM())` and the browser captures a snapshot of the old view, swaps in the new one, and cross-fades between them automatically. For multi-page navigation, add `@view-transition { navigation: auto; }` to your CSS and the browser handles transitions between documents with no JavaScript at all. You can name elements with `view-transition-name` to animate a shared element — like a product image — morphing from one page to the next. Keep transitions short (200–400ms) and respect `prefers-reduced-motion` so motion-sensitive users get an instant switch instead.

```js
document.querySelectorAll("a").forEach(link => {
  link.addEventListener("click", (e) => {
    e.preventDefault();
    document.startViewTransition(() => {
      // update the DOM, e.g. render the new view
      renderPage(link.href);
    });
  });
});
```

**Why it matters:** Native page transitions used to require a framework or an animation library — now a few lines of code give any site a polished, app-like feel.

#WebDev #Frontend #CSS #JavaScript #UX
