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

## Part B — prompt B2 (filter as you type)

Task: do TODO B2 in app.js (applyFilter and its 'input' listener).
- Read searchInput.value, trim(), toLowerCase().
- For every .card (query it each time, so cards from "Load more" count):
  card.hidden = true unless its .name text, lower-cased, contains the query.
- Write ONE line into statusBox with textContent, never innerHTML:
    empty query      -> '' and every card shown again
    some match       -> 'Showing 1 of 12 products' (total = all cards now in the list)
    nothing matches  -> 'No products match `"<exactly what the user typed>"`'
  "Exactly what the user typed" = the raw value, not the lower-cased one.
- Call applyFilter on every 'input' event of searchInput.

How I check "done":
- row 7: after Load more, type scarf, then SCARF -> one card and
  "Showing 1 of 12 products" both times; clear the box -> all cards back,
  status empty
- row 8: type `<img src=x onerror=alert(1)>` -> no alert, no broken image,
  status shows No products match "`<img src=x onerror=alert(1)>`" literally
- row 10: no red errors

## Part B — prompt B3 (no reload on Enter)

Task: do TODO B3 in app.js.
- Listen for 'submit' on the search form (searchInput.form), call
  event.preventDefault(), then applyFilter().
- Do not change the form in index.html and do not remove the submit button.

How I check "done":
- row 9: type cap, press Enter -> the address bar does NOT change to ?q=cap
  and the cart count is still there
- row 3: Tab still reaches every Add except sold-out, and Search