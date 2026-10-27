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
