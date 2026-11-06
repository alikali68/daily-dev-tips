# Skeleton Screens: Show Structure While You Wait

A spinner tells users "something is happening." A skeleton screen tells them "this is what's coming." Instead of a blank page or a generic loader, render a simplified outline of the layout — grey blocks where text, images, and cards will appear — while the real data loads.

Skeletons reduce perceived wait time because users start processing the page structure before the content arrives. Keep the skeleton's shape close to the final layout so nothing jumps when real content swaps in, and add a subtle shimmer animation to signal activity.

```css
.skeleton {
  background: linear-gradient(90deg, #e5e7eb 25%, #f3f4f6 50%, #e5e7eb 75%);
  background-size: 200% 100%;
  animation: shimmer 1.2s infinite;
  border-radius: 6px;
}
@keyframes shimmer {
  to { background-position: -200% 0; }
}
```

Reserve skeletons for waits over roughly 300ms; for instant loads, render the content directly to avoid a flash of grey. And always pair them with a timeout fallback — if data fails, replace the skeleton with a clear error state, not an endless shimmer.

**Why it matters:** Users judge speed by what they see, not by the clock — a skeleton makes the same wait feel shorter and keeps people on the page.

#UXDesign #WebDesign #Frontend #UI #UserExperience
