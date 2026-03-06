# Design: Phase 7 Prioritization Matrix Image Embed

**Date:** 2026-03-05
**Scope:** Single image insertion into Phase 7 "My Story" section

## Context

Phase 7 ("This isn't the end. This is Version 1.") My Story section currently contains:
1. Opening paragraph about next iterations
2. Seven-item bullet list of future features
3. Closing paragraph

The user wants to embed `Prioritization matrix.png` (already placed in the worktree assets folder) between the opening paragraph and the bullet list.

## Approach

**Option A selected:** Full-width inline `<figure>` with `<figcaption>`.

## Implementation

### Step 1 — Copy asset to main repo
Copy `Prioritization matrix.png` from worktree assets to main repo assets:
- Source: `J:\Office_CBC\Whitepaper\LinkedIN\Vibe2VPS\.worktrees\build-index-html\assets\Prioritization matrix.png`
- Dest:   `J:\Office_CBC\Whitepaper\LinkedIN\Vibe2VPS\assets\Prioritization matrix.png`

### Step 2 — Insert HTML in Phase 7 storyHTML
Insert between the opening `<p>` and the `<ul>` in `buildPhaseCard({ id: 'phase7' ... })`:

```html
<figure class="my-4">
  <img
    src="assets/Prioritization matrix.png"
    alt="Prioritization matrix showing next iterations for the project"
    class="w-full rounded-xl border border-gray-200 shadow-sm"
    style="object-fit:contain;"
  />
  <figcaption class="text-center text-xs text-gray-400 mt-2">
    Prioritization matrix — What's next
  </figcaption>
</figure>
```

### Step 3 — Commit and push to main
Single commit covering both the new asset and the index.html change.

## Design Decisions

- **No new CSS needed** — `border-gray-200`, `text-gray-400` already have dark mode overrides
- **No `no-print` class** — image should render in PDF export
- **`object-fit:contain`** — ensures the matrix isn't cropped if aspect ratio differs
- **`w-full`** — fills the card content width for easy reading
