# Rensei Integrated Canon Tracker (v4)

Small tweaks over v3:

- Fix: clicking **Add** on one Rensei item no longer disables all Add buttons.
- Add: **hover descriptions work in the auto-built Expanded Path** list as well.
- Keep: global + per-view stats, Expanded Path overlay, Custom Canon multi-lists, synced progress.

## What changed from v3

1. **Add button logic**

   - We now precompute a `Set` of all IDs that exist in your custom lists.
   - For each Rensei item we:
     - **Enable / disable** its own “Add” button based on whether *its* ID is in that set.
   - This prevents the bug where clicking “Add” once made every button look disabled.

2. **Expanded Path hover tooltips**

   - The Expanded Path section now reuses the same hover behavior:
     - Title
     - Description
     - Canon ID at the bottom
   - Add buttons are **removed from Expanded Path items** so it stays a clean overview lane.

3. **Sync & persistence**

   - Synced progress still works the same:
     - Any checkboxes sharing the same `data-book-id` toggle together.
   - Expanded toggle state still persists via `renseiCanonUiV1`.

Everything else (data model, localStorage keys, etc.) is compatible with v3.
