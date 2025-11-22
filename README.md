# Rensei Integrated Canon Tracker (v3)

Single-file HTML + JS reading tracker for the Rensei Canon with:

- **Rensei Canon view** – prebuilt core + secondary + Buddhist + thinking paths
- **Expanded Path overlay** – auto-built combined path (Core + all layers)
- **Custom Canon view** – multi-list custom paths (Core / Secondary / Tertiary / Other)
- **Synced progress** – if entries share the same `data-book-id`, checking one checks them all
- **Local-only storage** – everything is kept in `localStorage` in the user's browser only

Perfect for GitHub Pages: just drop `index.html` into a repo and enable Pages.

## New in v3

- **Global + per-view stats**  
  - `All books: X / Y` — unique completed across the whole app  
  - `This view: a / b` — unique completed in the currently active tab (Rensei vs Custom)

- **Expanded Path (overlay)**  
  - Toggle with the **Expanded path** chip on the top-right.
  - When ON, an **“Expanded Path (Auto-built)”** section appears above the core canon.
  - It combines:
    - Core Canon
    - Secondary Canon
    - Buddhist Canon
    - Thinkers on Thinking  
  - Each unique book appears once, and is linked to the same IDs as the rest of the UI.

- **Expanded state persists**  
  - Your Expanded Path ON/OFF state is remembered via `renseiCanonUiV1` in `localStorage`.

- **Rensei → Custom Add button improvements**  
  - “Add” buttons on each Rensei item are now **disabled** if that ID is already present in any Custom list.
  - Click “Add”:
    - If you don’t have any custom lists yet, it auto-creates **“My List”**.
    - The book is added with the canonical ID (no suffixes), so progress syncs cleanly.
  - Hover tooltip still shows:
    - Title
    - Short description
    - Canon ID

- **Custom Canon duplication**  
  - Each item in a Custom list has a **“Copy”** button.
  - This lets you **duplicate that book** (same ID, same title) into another list without retyping.
  - The duplication uses a simple `prompt()` that lists your other lists and asks for a number.

## Data model

### Progress

Stored under:

```js
renseiCanonProgressV1 = {
  [bookId: string]: boolean
}
```

Any checkbox with `data-book-id="..."` reads/writes this state.  
If two or more checkboxes share the same ID, checking one checks all.

### Custom Canon

Stored under:

```js
renseiCustomCanonV2 = [
  {
    id: string,       // group ID
    title: string,    // group title
    type: string,     // "core" | "secondary" | "tertiary" | "other"
    items: [
      { id: string, title: string }  // id == data-book-id for syncing
    ]
  },
  ...
]
```

### UI state

Stored under:

```js
renseiCanonUiV1 = {
  expanded: boolean   // Expanded Path toggle
}
```

## Usage

1. Create or reuse a GitHub repo.
2. Copy `index.html`, `LICENSE`, `.gitignore`, and `README.md` into it.
3. Enable GitHub Pages (e.g. from `main` branch, `/root`).
4. Open your Pages URL – you now have the v3 Rensei Canon tracker.

## License

MIT – see `LICENSE`.
