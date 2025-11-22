# Rensei Integrated Canon Tracker

Single-file HTML + JS reading tracker for the Rensei Canon (Jung, Frankl, Dostoevsky, Buddhist texts, etc.) with:

- **Rensei Canon view** – your prebuilt reading order
- **Custom Canon view** – anyone can build their own order
- **Synced progress** – if two entries share the same `data-book-id`, checking one checks them all
- **Local-only storage** – everything is kept in `localStorage` in the user's browser

Perfect for GitHub Pages: just drop `index.html` into a repo and enable Pages.

## Features

- Core/secondary/Buddhist/thinkers-on-thinking lists preloaded
- "Custom Canon" tab:
  - add books with a title
  - optional **ID** field to sync with an existing Rensei item
  - reorder (up/down) and delete items
- Global progress indicator: shows how many unique books are completed
- "Reset all progress" button
- No frameworks, no build step, no external dependencies

## Sync logic

Each checkbox has a `data-book-id`. Progress is stored by that ID.

- If you add a custom book with an ID that matches a Rensei Canon book
  (e.g. `jung-man-and-his-symbols`), ticking it in one place will mark it as
  complete everywhere else that shares the same ID.
- If you leave the ID blank, a new custom ID is generated and used only for
  that item.

This means:

- People can follow your canonical order **and** build their own order.
- If they "pull" some of your books into their custom list and reuse the same ID,
  their progress stays in sync.

## Local-only data

- All state lives in `localStorage` under two keys:

  - `renseiCanonProgressV1` – `{ [bookId: string]: boolean }`
  - `renseiCustomCanonV1` – `Array<{ id: string, title: string }>`

- No backend, no tracking, no analytics.
- Each browser has its own independent data.

## Usage

1. Create a new GitHub repo.
2. Copy `index.html`, `LICENSE`, `.gitignore`, and `README.md` into it.
3. Enable GitHub Pages (e.g. from `main` branch, `/root`).
4. Open your Pages URL – you now have a reading tracker.

## License

MIT – see `LICENSE`.
