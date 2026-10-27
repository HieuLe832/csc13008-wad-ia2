# brief.md

## Part A — prompt 1

Context: static page (index.html, style.css, app.js, check.js), no build.
Every element in index.html is a <div>.

Task: edit ONLY index.html. Replace each <div> with the element that
matches its meaning (header, nav, main, h1, form, label, ul/li, h2,
button, p, footer). That includes the card inside <template id="card-template">.

Constraints:
- Keep every id and class exactly as they are (style.css, app.js and
  check.js find elements by them).
- Do NOT edit style.css, check.js or app.js.
- Do not turn every <div> into <section>; keep <div> for layout-only wrappers.
- Exactly one <h1> (the page title); product names are <h2>.
- Search: <form> + <label for="q"> + <button type="submit">.
- Add / Load more: real <button type="button">, no onclick attributes.
- Sold-out Add: add the `disabled` attribute and keep class="disabled".
- The page must look identical to before.

How I check "done": Console shows "Session 4 self-check: 8/8 passed";
Tab reaches every Add except sold-out, plus Search; screenshot before/after
has no difference; no red errors; git diff --stat shows only index.html.
