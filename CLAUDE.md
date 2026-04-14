# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file Korean shopping list web app (`index.html`). No build tools, no dependencies — open directly in a browser or deploy to Vercel as-is.

## Architecture

Everything lives in `index.html`:

- **CSS** (inline `<style>`): Two-panel grid layout — blue sidebar (280px) + white main panel. Responsive with `@media` not yet added; layout uses `grid-template-columns: 280px 1fr`.
- **HTML**: Sidebar contains input group + stat box + clear button. Main panel contains filter tabs + `<ul id="list">` + empty state div.
- **JavaScript** (inline `<script>`): State is `items` (array of `{ text, checked }`) persisted to `localStorage` key `shoppingList`. A `filter` variable (`'all'` | `'todo'` | `'done'`) controls what `render()` displays.

Key functions:
- `render()` — filters `items` by current `filter`, rebuilds `<ul>` DOM, updates stats (totalCount, doneCount, progressFill)
- `save()` — serializes `items` to `localStorage`
- `addItem()`, `toggle(i)`, `remove(i)`, `clearChecked()` — mutate `items`, then call `save()` + `render()`
- `setFilter(f, btn)` — updates `filter`, toggles `.active` on filter tab buttons, calls `render()`

Index mapping: `render()` uses `items.indexOf(item)` to get the real index when passing to `toggle`/`remove`, because the displayed list may be a filtered subset.

## Running

Open `index.html` directly in a browser. No server required.
