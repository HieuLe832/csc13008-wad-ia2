## 2026-10-27 — Part A: semantic HTML
Tool: Claude Sonnet 5.5 
Asked for: replace the `<div>`s in index.html with semantic elements (brief.md, prompt 1).  
Kept: the whole result — header/nav/main/h1/form/label/ul/li/h2/p/button/footer, including the card inside `<template>`; 4 `<div>`s left as layout-only wrappers, as the brief asked.  
Changed: nothing.  
Rejected: nothing. Ran rows 1, 2, 3, 10 and 11 of Done means, all passed: 8/8 in the Console; before/after screenshots identical; Tab reaches both header links, the search box, Search, the 7 in-stock Add buttons and Load more, skips the sold-out Tote bag's Add, and the orange ring is visible each time; no red errors; `git diff --stat` shows only index.html.  
