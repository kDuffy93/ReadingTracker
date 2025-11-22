# Rensei Canon Reading Tracker

Single-page reading tracker for:

- **Rensei integrated canon** (Jung, Dostoevsky, Machiavelli, Sun Tzu, Japanese strategy & Zen, Buddhist depth texts, thinkers-on-thinking, Tesla/Einstein worldview, etc.)
- **Custom canons** that you define yourself.

This is **version 5** of the HTML-only app, designed to be dropped into GitHub Pages or opened directly in a browser. All state is stored locally in `localStorage`.

## Features

- Two tabs:
  - **Rensei Canon** – the curated base path.
  - **Custom Canons** – arbitrary lists and experiments.
- Two Rensei layouts:
  - **Condensed** columns by type (core / secondary / Buddhist & Tao / thinking-about-thinking).
  - **Grouped by core** – each core work with its wired secondary and tertiary suggestions beneath.
- **Expanded path overlay** – one long, ordered list built from core → secondary → tertiary mappings. Checkmarks sync with every other view.
- **Hover tooltips** for all canon items – description plus the internal ID (so you can wire them into your own custom lists).
- **Add-to-custom buttons** on the Rensei side:
  - Adds the item into your first custom list.
  - Button automatically disables when the item already exists in any custom list.
- Custom canon builder:
  - Multiple named lists.
  - Reorder lists (left/right) and items (up/down).
  - Duplicate items into other lists.
  - Add completely custom entries that are not part of the Rensei base.
- **Progress pills** at the top:
  - Global count, Rensei-only, and custom-only completion.
  - All completion state is shared across views via the item IDs.
- **Local-only**:
  - No network access, APIs, or cookies.
  - Everything is stored in `localStorage` under three keys:
    - `renseiCanonProgressV1`
    - `renseiCustomCanonV2`
    - `renseiCanonUiV1`

## Usage

1. Open `index.html` directly in a browser, or host the file with GitHub Pages.
2. Use the **Rensei Canon** tab as a scaffold:
   - Hover titles to see what they are and copy IDs.
   - Use **+ Add** to move a book into your first custom list.
3. Use the **Custom Canons** tab to:
   - Rename lists (e.g., “Winter 2025 Stack”, “Deep Jung Run”).
   - Reorder items with ↑/↓ to create precise reading orders.
   - Add your own entries (e.g., Rensei Papers volumes or new authors).
4. Progress is automatically persisted. “Reset all progress” only clears completion state, not your custom lists.

## License

MIT – see `LICENSE`.
