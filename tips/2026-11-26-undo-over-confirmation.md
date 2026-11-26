# Undo Beats Confirmation: Stop Interrupting Your Users

Every "Are you sure?" dialog is a small tax on your user's attention. Most of the time they already know what they want — the dialog only slows them down and teaches them to click "Yes" on autopilot, which defeats its own purpose. A far better pattern is to let the action happen instantly and offer an undo instead: delete the item, show a quiet toast with an Undo button, and keep the item recoverable for a few seconds. This is how Gmail's "Undo send" and most modern editors work — the destructive action feels fast and reversible at the same time.

```js
// Delete now, offer undo — no confirmation dialog needed
function deleteItem(id) {
  const item = items.get(id);
  items.delete(id);
  render();

  showToast("Item deleted", {
    action: "Undo",
    onAction: () => { items.set(id, item); render(); },
    duration: 5000,
  });
}
```

Reserve confirmation dialogs for actions that are truly irreversible and costly — deleting an account, wiping a workspace, sending money. For everything else, undo is faster, kinder, and safer than asking first.

**Why it matters:** Users forgive a mistake they can undo in one tap; they never forgive a product that nags them before every click.

#UXDesign #UIUX #ProductDesign #UserExperience
