## 2026-10-27 — Part A: semantic HTML
Tool: Claude Sonnet 5.5 
Asked for: replace the `<div>`s in index.html with semantic elements (brief.md, prompt 1).  
Kept: the whole result — header/nav/main/h1/form/label/ul/li/h2/p/button/footer, including the card inside `<template>`; 4 `<div>`s left as layout-only wrappers, as the brief asked.  
Changed: nothing.  
Rejected: nothing. Ran rows 1, 2, 3, 10 and 11 of Done means, all passed: 8/8 in the Console; before/after screenshots identical; Tab reaches both header links, the search box, Search, the 7 in-stock Add buttons and Load more, skips the sold-out Tote bag's Add, and the orange ring is visible each time; no red errors; `git diff --stat` shows only index.html.  

## 2026-10-27 — Part B1: add to cart
Tool: Claude Sonnet 5.5  
Asked for: TODO B1 in app.js (brief.md, prompt B1) — one `click` listener on `catalogue`, act only on `.add`, count per product id in `cart`, `renderCart()` writes the total into `cartCount`.  
Kept: the whole result — a single delegated listener using `event.target.closest('.add')` then `closest('.card')` and `card.dataset.id`; `cart[id] = (cart[id] || 0) + 1`; `renderCart()` sums `Object.values(cart)` and writes it with `textContent`. The B4 total is left for later.  
Changed: nothing.  
Rejected: nothing. Ran rows 1, 4, 5, 6 and 10 of Done means, all passed: Add on T-shirt twice then on sold-out Tote bag gives Cart (2); Tab to an Add and Enter adds 1; Load more then Add on Belt adds 1; 8/8 in the Console, no red errors. Also checked in the Console that `Object.keys(cart).length` counts distinct products (many T-shirts = 1, then another product = 2), while the header shows the sum. Also ran `console.table(cart)` to see the exact quantity per product id, and the table matched the header count.  

## 2026-10-27 — Part B2: filter as you type
Tool: Claude Sonnet 5.5  
Asked for: TODO B2 in app.js (brief.md, prompt B2) — `applyFilter()` plus an `input` listener on `searchInput`: trim and lower-case the query, hide every `.card` whose `.name` does not contain it, write one status line with `textContent`.  
Kept: the whole result — the cards are queried on every call, so the ones added by "Load more" count; `card.hidden = !name.includes(query)`; status is `''` for an empty query, `Showing N of <all cards> products` when something matches, `No products match "<raw value>"` when nothing does (the raw `searchInput.value`, not the lower-cased one); `searchInput.addEventListener('input', applyFilter)`. The B3 form-submit part and the given "Load more" code are untouched.  
Changed: nothing.  
Rejected: nothing. Ran rows 7, 8 and 10 of Done means, all passed: after Load more, `scarf` and `SCARF` each show one card and "Showing 1 of 12 products", clearing the box brings all cards back and empties the status; typing `<img src=x onerror=alert(1)>` gives no alert and no broken image, and the status shows it literally as text; no red errors in the Console.  

## 2026-10-27 — Part B3: no reload on Enter
Tool: Claude Sonnet 5.5  
Asked for: TODO B3 in app.js (brief.md, prompt B3) — listen for `submit` on the search form (`searchInput.form`), call `event.preventDefault()`, then `applyFilter()`. Do not change the form in index.html and keep the submit button.  
Kept: the whole result — one `submit` listener on `searchInput.form` that calls `event.preventDefault()` and then `applyFilter()`. index.html, the Search button and the given "Load more" code are untouched.  
Changed: nothing.  
Rejected: nothing. Ran rows 9 and 3 of Done means, all passed: typing `cap` and pressing Enter does not change the address bar (no `?q=cap`), the cart count is still there, and the list is filtered; Tab still reaches every Add except the sold-out one, and Search. Console still shows 8/8 passed with no red errors. The assistant itself only ran a syntax check (`node --check app.js`); the browser checks were done by me.  
