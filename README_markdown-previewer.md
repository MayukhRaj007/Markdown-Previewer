# Markdown Previewer

![Language](https://img.shields.io/badge/language-JavaScript-F7DF1E?logo=javascript)  ![License](https://img.shields.io/badge/license-MIT-green)  ![Status](https://img.shields.io/badge/status-active-brightgreen)  ![Dependencies](https://img.shields.io/badge/dependencies-none-blue)

A live, browser-based Markdown previewer built with **vanilla HTML, CSS, and JavaScript** — zero dependencies, zero build step. Type Markdown on the left, see it rendered on the right, in real time.

**[Live demo →](https://YOUR_USERNAME.github.io/markdown-previewer/)**

## Features

- Live preview as you type (debounced for performance)
- Hand-written Markdown parser — no external library, fully readable source
- Supports headings (`#`, `##`, `###`), bold, italic, inline code, fenced code blocks, links, lists, blockquotes, and horizontal rules
- XSS-safe: user input is HTML-escaped before any Markdown rules are applied
- Auto-saves your draft to `localStorage` — refresh the page without losing work
- "Copy HTML" button to grab the rendered output
- Responsive layout — stacks vertically on mobile

## Usage

Just open `index.html` in any browser. No installation, no server, no build step.

Or visit the [live GitHub Pages demo](https://YOUR_USERNAME.github.io/markdown-previewer/).

## Running the tests

Open `tests/test_parser.html` directly in your browser. It runs 18 test cases against the parser and prints pass/fail results on the page — no Node, no npm, no test framework required.

## Project structure

```
markdown-previewer/
├── index.html              # The entire app — HTML, CSS, and JS in one file
├── tests/
│   └── test_parser.html    # Browser-runnable test suite (18 tests)
└── README.md
```

## How the parser works

The Markdown → HTML conversion happens in three stages:

1. **Escape** — all user input is HTML-escaped first (`<` → `&lt;`, etc.) so nothing can inject raw HTML or scripts
2. **Block-level parsing** — the text is split into lines and scanned for headings, lists, blockquotes, code fences, and horizontal rules
3. **Inline parsing** — within each block, regex rules handle bold, italic, inline code, and links

Fenced code blocks are extracted *before* block parsing and restored at the end, so content inside a code block (like a `#` in a code comment) is never mistaken for Markdown syntax.

## Why no library?

Tools like `marked.js` or `markdown-it` are what you'd use in production. This project intentionally reimplements a subset of their logic by hand so the mechanics are fully visible and understood — not hidden behind an import.

## What I learned

- DOM manipulation with vanilla JS (`addEventListener`, `innerHTML`, `localStorage`)
- Writing a real (if minimal) parser: block-level vs inline-level passes
- Debouncing input events for performance
- XSS prevention: escape before transform, never trust `innerHTML` from raw user text
- CSS Grid for a resizable two-pane layout
- Deploying a static site live with **GitHub Pages**

## Tech stack

- HTML5
- CSS3 (Grid, custom properties)
- Vanilla JavaScript (ES6+) — no frameworks, no build tools

---

Part of my [50 GitHub Projects](https://github.com/YOUR_USERNAME) portfolio challenge.
