# Affordances: Make Clickable Things Look Clickable

Users decide what they can tap in about 50 milliseconds — before they read a single word. If a button looks like plain text, or plain text looks like a button, you have already lost them. Every interactive element should carry a clear visual signal: a filled or outlined button shape, an underline on links, a hover state that changes colour or lifts the element, and a pointer cursor on desktop. Test your interface with the "squint test": blur your eyes and ask whether the tappable elements still stand out from static content. When in doubt, make the affordance stronger, not subtler — clarity always beats minimalism.

```css
/* A link that reads as a link, and a button that reads as a button */
a { color: #0066cc; text-decoration: underline; }
a:hover { text-decoration-thickness: 2px; }

button {
  cursor: pointer;
  padding: 0.6rem 1.2rem;
  border-radius: 0.5rem;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}
button:hover { transform: translateY(-1px); box-shadow: 0 4px 12px rgba(0,0,0,0.15); }
button:active { transform: translateY(0); }
```

**Why it matters:** Every missed tap is a user who thinks your product is broken — clear affordances cut confusion, support tickets, and drop-off in one move.

#UXDesign #UIUX #WebDesign #UserExperience #DesignTips
