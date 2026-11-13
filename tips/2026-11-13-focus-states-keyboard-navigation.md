# Design Focus States for Keyboard Users, Not Just Mouse Users

A large share of users navigate the web with a keyboard alone — power users, people with motor impairments, and anyone using assistive technology. Yet many sites strip the browser's default focus outline with `outline: none` in the name of cleaner visuals, leaving keyboard users with no idea where they are on the page.

The fix is `:focus-visible`: it shows a clear focus ring only when the user is navigating by keyboard, while mouse clicks stay clean. Style it to match your brand — a bold color and enough contrast — and keep the tab order matching the visual order of the page. Then test it yourself: put the mouse aside and Tab through your whole flow, from the header to the checkout button.

```css
:focus-visible {
  outline: 3px solid #0066cc;
  outline-offset: 2px;
  border-radius: 4px;
}
```

**Why it matters:** if a user can't see where they are, they can't use your product — no matter how beautiful it looks.

#UXDesign #Accessibility #WebDesign #UIUX
