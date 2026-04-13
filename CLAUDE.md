# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file Korean shopping list web app (`shopping-list.html`). No build tools, no dependencies — open the HTML file directly in a browser.

## Architecture

Everything lives in one file:

- **CSS** (inline `<style>`): Card-centered layout, custom checkbox styling, transition effects
- **HTML**: Input row, stats bar, `<ul id="list">` for items, empty state message
- **JavaScript** (inline `<script>`): State stored in `localStorage` as `shoppingList` (JSON array of `{ text, checked }` objects)

Key functions:
- `render()` — rebuilds the entire list DOM from the `items` array
- `save()` — persists `items` to `localStorage`
- `addItem()`, `toggle(i)`, `remove(i)`, `clearChecked()` — mutate `items`, then call `save()` + `render()`

## Running

Open `shopping-list.html` directly in a browser. No server required.
