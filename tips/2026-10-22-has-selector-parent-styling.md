# Style Parent Elements With the CSS :has() Selector

For years, CSS had no parent selector — you reached for JavaScript to style a wrapper based on what it contains. The `:has()` pseudo-class changes that: `form:has(input:invalid) { border-color: red; }` highlights the whole form as soon as any field is invalid. It also powers elegant conditional layouts, like `figure:has(figcaption) img { border-radius: 0 0 8px 8px; }`, without extra utility classes.

Use it for state-driven UI: a card that changes when its image fails to load, or a nav that reflows when it contains a long menu. Keep selectors simple — `:has()` is evaluated at layout time, so overly deep or chained checks on large pages can cost rendering performance. And remember it works in every direction: `:has(+ .sibling)` styles an element based on the element after it, which was impossible in pure CSS before.

**Why it matters:** `:has()` removes a whole class of JavaScript state-syncing hacks — cleaner markup, less code, and styling that stays true to the DOM as it actually is.

#CSS #Frontend #WebDev #CSSTips
