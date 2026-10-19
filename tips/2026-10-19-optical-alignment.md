# Optical Alignment Beats Mathematical Alignment

That button text is centered with `text-align: center` — so why does it look slightly off? Because mathematical centering ignores visual weight: a triangle, a play icon, or rounded letterforms carry more mass on one side than the other, and your eye notices the imbalance instantly.

The fix is optical correction: nudge the element 1–2px toward its lighter side until it *looks* right. In Figma, trust pixel preview over the align panel; in CSS, a tiny `transform` or asymmetric padding often beats perfect symmetry:

```css
/* Play icon looks off-center even when centered — nudge it right */
.play-icon { transform: translateX(2px); }
```

Train your eye with a squint test: blur your vision and the heavier side reveals itself. This one habit separates interfaces that feel "designed" from ones that feel merely "built."

**Why it matters:** Users judge credibility in milliseconds, and a logo or button that looks "slightly off" silently erodes trust in the entire product — optical alignment is invisible when right, conspicuous when wrong.

#GraphicDesign #UIUX #DesignTips #Typography
