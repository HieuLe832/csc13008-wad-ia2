# brief.md

## Part A — prompt 1

Context: static page (index.html, style.css, app.js, check.js), no build.
Every element in index.html is a `<div>`.

Task: edit ONLY index.html. Replace each `<div>` with the element that
matches its meaning (header, nav, main, h1, form, label, ul/li, h2,
button, p, footer). That includes the card inside `<template id="card-template">`.

Constraints:
- Keep every id and class exactly as they are (style.css, app.js and
  check.js find elements by them).
- Do NOT edit style.css, check.js or app.js.
- Do not turn every `<div>` into `<section>`; keep `<div>` for layout-only wrappers.
- Exactly one `<h1>` (the page title); product names are `<h2>`.
- Search: `<form>` + `<label for="q">` + `<button type="submit">`.
- Add / Load more: real `<button type="button">`, no onclick attributes.
- Sold-out Add: add the `disabled` attribute and keep class="disabled".
- The page must look identical to before.

How I check "done": Console shows "Session 4 self-check: 8/8 passed";
Tab reaches every Add except sold-out, plus Search; screenshot before/after
has no difference; no red errors; git diff --stat shows only index.html.

## Part B — shared context, every B prompt need this

Context: static page (index.html, style.css, app.js, check.js), no build.
Part A is done: index.html is semantic and the Console shows
"Session 4 self-check: 8/8 passed". The TODO comments in app.js are the
spec — follow them as written.

Constraints for every B prompt:
- Edit ONLY app.js. Do NOT edit style.css, check.js or index.html.
- Keep every id and class exactly as they are.
- Do not change the given "Load more" code at the bottom of app.js.
- No innerHTML, no insertAdjacentHTML anywhere — write text with textContent.
- No onclick attributes; use addEventListener.
- No new libraries, no new files.
- Do only the part I ask for in this prompt, nothing from later parts.

## Part B — prompt B1 (Add to cart)

Task: do TODO B1 in app.js.
- Add exactly ONE 'click' listener, on `catalogue` (the `<ul>`), not one per
  button. It must also work for cards added later by "Load more".
- Act only when the click came from an .add button
  (event.target.closest('.add')); a click anywhere else in the list does
  nothing. The sold-out button (disabled) must not change the cart.
- Find the card with closest('.card'), read card.dataset.id, add 1 to
  cart[id] (it is undefined the first time), then call renderCart().
- renderCart(): sum Object.values(cart) and write it into cartCount with
  textContent. Leave the B4 part for later.

How I check "done" (README Done means):
- row 4: Add on T-shirt twice, then Add on sold-out Tote bag -> Cart (2)
- row 5: Tab to an Add, press Enter -> count +1
- row 6: Load more, then Add on Belt -> count +1
- row 1 and 10: still 8/8 passed, no red errors in the Console