# Rensei Integrated Canon Tracker

Single-file HTML + JS reading tracker for the Rensei Canon (Jung, Frankl, Dostoevsky, Buddhist texts, etc.) with:

- **Rensei Canon view** – your prebuilt reading order with hover descriptions and IDs
- **Custom Canon view** – layered lists (Core / Secondary / Tertiary / Other) that you can build yourself
- **Synced progress** – if two entries share the same `data-book-id`, checking one checks them all
- **Local-only storage** – everything is kept in `localStorage` in the user's browser

Perfect for GitHub Pages: just drop `index.html` into a repo and enable Pages.

## Features

### Rensei Canon view

- Core, Secondary, Buddhist, and Thinkers-on-Thinking sections
- **Condensed vs Expanded toggle**:
  - Condensed: only Core Canon visible
  - Expanded: show Secondary, Buddhist, and Thinkers sections too
- **Hover tooltips**:
  - Move your mouse over any canonical item to see a short description
  - Tooltip shows the internal **ID** so people can copy it into their custom lists
- **Add to Custom**:
  - Each canonical row has an **Add** button
  - Clicking it adds that book (with a syncing ID) into the first Custom list

### Custom Canon view

- Create multiple lists (e.g., *My Core*, *My Secondary*, *Winter Deep Dive*), each with a type:
  - Core / Secondary / Tertiary / Other (type is just a label for now)
- In each list:
  - Add books with a title
  - Optional **ID**:
    - If the ID matches a Rensei Canon ID, progress is synced
    - If you leave it blank, a unique custom ID is generated
  - Reorder items (up / down)
  - Delete items
- Rename or delete entire lists
- All lists and items are stored in:

  - `renseiCustomCanonV2` – `Array<{ id, title, type, items: { id, title }[] }>` in `localStorage`

### Progress logic

Each checkbox has a `data-book-id`. Progress is stored by that ID:

- `renseiCanonProgressV1` – `{ [bookId: string]: boolean }` in `localStorage`
- If two or more checkboxes share the same ID, checking one checks all.
- Global counter shows **unique** books completed vs total unique IDs.

This means:

- People can follow your canonical order **and** build their own orders.
- If they “pull” some of your books into their custom lists and reuse the same ID,
  their progress stays in sync across both views.

### Local-only data

- No backend, no tracking, no analytics.
- Each browser has its own independent canon state.

## Usage

1. Create a new GitHub repo.
2. Copy `index.html`, `LICENSE`, `.gitignore`, and `README.md` into it.
3. Enable GitHub Pages (e.g. from `main` branch, `/root`).
4. Open your Pages URL – you now have an interactive Rensei Canon tracker.

## License

MIT – see `LICENSE`.
