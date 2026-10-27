# Self-assessment — IA#2

Submitted by: 24120048 — Le Hoang Hieu

Total I claim: 96 / 100

| Criterion | Max | I claim | Evidence |
|---|---|---|---|
| 1. Behaviour (B1–B4) | 45 | 45 | Ran every row of *Done means* in the browser. Row 1: 8/8 passed. Row 4: T-shirt ×2 then sold-out Tote bag → `Cart (2)`. Row 5: Tab + Enter on an Add → +1. Row 6: Load more, Add on Belt → +1 (one delegated listener on `#catalogue`, app.js:33). Row 7: `scarf` / `SCARF` → one card, `Showing 1 of 12 products`; empty box → all cards, status empty. Row 8: `<img src=x onerror=alert(1)>` shown literally via `textContent`, no alert (app.js:78). Row 9: Enter on `cap` → no `?q=cap`, cart kept (app.js:96). Row 10: no red errors. B4: T-shirt ×2 + Cap → `Cart (3) · 455.000 đ`; Load more + Belt → +140.000 đ (`renderCart()`, app.js:44-50). |
| 2. Scope | 10 | 10 | `git diff --stat 783e251 HEAD`: only `index.html` and `app.js` changed among starter files; `style.css`, `check.js`, `README.md` untouched. The other files in the diff (`brief.md`, `AI-LOG.md`) are the required hand-in files, new, not starter files. |
| 3. The brief | 15 | 15 | `brief.md`: the prompts as given, in order (A, shared B context, B1–B4). States every constraint the rubric lists: keep every `id`/`class`, do not edit `style.css`/`check.js`, ONE click listener on the list (B1), `textContent` never `innerHTML` (shared B constraints + B2), `preventDefault` / no reload (B3). Each prompt ends with "How I check done" naming the *Done means* rows. |
| 4. AI-LOG.md | 20 | 16 | One entry per part (A, B1, B2, B3, B4), each with Tool, Asked for, Kept, Changed, Rejected and the rows run. B4 entry records what the assistant got wrong (`querySelector('[data-id="' + id + '"]')` throws on `"`/`\` ids and on a cart key with no card), what I replaced it with (`{ qty, price }` stored in `cart`), and the Console check after the fix — matches commit `32ffe1e`. Not 20: the mistake was caught by reading the code, so no entry names a *Done means* row that caught it, which the top band asks for. |
| 5. Commit history | 10 | 10 | `783e251 starter` first, then `1002555` Part A (plus `cdb9aa9`, a formatting fix to the Part A brief), `c33f07e` B1, `c52987d` B2, `99e19b0` B3, `32ffe1e` B4, each preceded by its brief commit. Every message says what changed, and each part commit touches only `app.js`/`index.html` + its log entry, so the log can be checked against the diff. |

## What I did not manage

- The B4 mistake was caught by reading the code, not by a row of *Done means*
  failing — the table never went red for me, so the AI-LOG cannot name a row
  that caught it.
- The B4 fix went beyond the `renderCart()` part the TODO asks for: `cart` now
  holds `{ qty, price }` instead of a plain count, which also changed the B1
  listener. The comment at app.js:16 still shows the old shape
  `{ tshirt: 2, cap: 1 }`; I left it because it is part of the given starter
  comments.

## What I would do differently

Read each diff before running the table, not after. For B1–B3 I ran the rows
first and only skimmed the code; reading it first is what found the B4 issue,
and I would have liked to apply the same check to every part.
