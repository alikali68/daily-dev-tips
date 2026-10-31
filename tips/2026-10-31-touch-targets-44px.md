# Design Touch Targets People Can Actually Tap

A button that looks tappable but is only 24 pixels tall will frustrate users on every phone, especially on the move or with one hand. Aim for a minimum touch target of 44×44 pixels for every interactive element — buttons, links, icons, and toggles — and keep at least 8 pixels of clear space between neighboring targets so a tap never lands on the wrong one. When a visual icon has to stay small, enlarge its invisible hit area with padding instead of shrinking the target itself. Test on a real device, not just a desktop preview: thumbs are wider than cursors, and what feels precise with a mouse often feels cramped with a finger.

```css
/* Small icon, comfortable target */
.icon-button {
  min-width: 44px;
  min-height: 44px;
  padding: 10px;
}
```

**Why it matters:** Generous touch targets cut mis-taps, reduce user frustration, and make your interface genuinely usable for everyone, including people with limited dexterity.

#UXDesign #UIDesign #MobileDesign #Accessibility #UserExperience
