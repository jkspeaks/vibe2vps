# Design: Five UI Edits
**Date:** 2026-03-06
**Status:** Approved

## Overview

Five targeted UI edits to `index.html`:

1. Move audience toggle + description below export buttons
2. Box around phase stepper labelled "The Journey"
3. Rename phase stepper label "Before" → "ReadMe"
4. Centre-align export buttons
5. Add `vibe_approach.png` to Phase 7 DIY tab above bullets

---

## Item 1 — Move Audience Toggle + Description

**Current order** in `#hero` section:
1. Audience toggle (`#audience-toggle`)
2. Description `<p>Toggle to adjust…</p>`
3. Title block + hook text
4. Phase stepper
5. Export toolbar

**New order:**
1. Title block + hook text
2. Phase stepper (wrapped with "The Journey" label — see item 2)
3. Export toolbar (centred — see item 4)
4. Audience toggle (`#audience-toggle`)
5. Description `<p>Toggle to adjust…</p>`

Both the `<div id="audience-toggle">` and the `<p class="text-xs text-gray-400 ...">` blocks move together, maintaining their relative order, to immediately after the closing `</div>` of the export toolbar.

---

## Item 2 — "The Journey" Box

Wrap `#phase-stepper` in a new container that provides the border, rounded corners, and label. Remove the existing `mb-10` from the stepper div (the outer wrapper carries the margin instead):

```html
<div class="no-print text-center mb-10">
  <div class="inline-block border border-gray-200 rounded-2xl px-6 py-4">
    <p class="text-xs font-semibold text-gray-400 uppercase tracking-widest mb-3">The Journey</p>
    <div id="phase-stepper" class="flex items-center justify-center gap-1 flex-wrap"></div>
  </div>
</div>
```

---

## Item 3 — Rename "Before" → "ReadMe"

In the `PHASE_LABELS` JS array, change:
```js
{ num: 0, short: 'Before' }
```
to:
```js
{ num: 0, short: 'ReadMe' }
```

---

## Item 4 — Centre-Align Export Buttons

Add `justify-center` to the export toolbar's flex wrapper, and bump bottom margin to `mb-4` to add breathing room before the audience toggle:

```html
<div class="no-print flex flex-wrap items-center justify-center gap-2 mb-4">
```

---

## Item 5 — `vibe_approach.png` in Phase 7 DIY Tab

**Asset:** `C:/Users/jayak/Downloads/vibe_approach.png` → copy to `J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/assets/vibe_approach.png`

**Placement:** Top of `diyHTML` in the Phase 7 `buildPhaseCard()` call, before the first `<h3>The Maturity Ladder</h3>`.

```html
<figure class="my-4">
  <img
    src="assets/vibe_approach.png"
    alt="How to approach vibe coding projects — Research, Plan, Design Spec, Prompt, Refine"
    class="w-full max-h-96 rounded-xl border border-gray-200 shadow-sm"
    style="object-fit:contain;"
  />
  <figcaption class="text-center text-xs text-gray-400 mt-2">
    The Vibe Coding Approach
  </figcaption>
</figure>
```

---

## Commit Plan

Single commit to `main`:
- `assets/vibe_approach.png` (copied from Downloads)
- `index.html` (all 5 edits)

Message: `feat: UI edits — journey box, ReadMe label, centred buttons, toggle repositioned, vibe approach image`
