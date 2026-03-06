# Five UI Edits Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Apply 5 targeted UI edits to index.html — reposition the audience toggle, add a "The Journey" box around the phase stepper, rename "Before" to "ReadMe", centre the export buttons, and embed vibe_approach.png in the Phase 7 DIY tab.

**Architecture:** Single static HTML file, no build step. All edits are direct modifications to `index.html` template literals and inline HTML. One new binary asset (`vibe_approach.png`) is copied from Downloads and committed. All 5 changes ship in one commit to `main`.

**Tech Stack:** Plain HTML, Tailwind CDN, Lucide CDN, vanilla JS

**Design doc:** `docs/plans/2026-03-06-five-ui-edits-design.md`

---

### Task 1: Copy vibe_approach.png from Downloads to assets/

**Files:**
- Copy FROM: `C:/Users/jayak/Downloads/vibe_approach.png`
- Copy TO: `J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/assets/vibe_approach.png`

**Step 1: Copy the file**

```powershell
Copy-Item "C:/Users/jayak/Downloads/vibe_approach.png" "J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/assets/vibe_approach.png"
```

**Step 2: Verify file was copied and is non-zero**

```powershell
Get-Item "J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/assets/vibe_approach.png" | Select-Object Name, Length
```

Expected: Name = `vibe_approach.png`, Length > 0

**Step 3: Verify git sees it as untracked**

```bash
cd "J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS" && git status assets/
```

Expected: `assets/vibe_approach.png` listed as untracked

> No commit yet — the asset and HTML changes will be committed together in Task 4.

---

### Task 2: Apply items 1–4 to index.html (layout + stepper box + rename + centre)

**Files:**
- Modify: `J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/index.html` (hero section, lines ~372–431)

**Context — current hero section structure (lines 372–431):**

```html
<!-- Audience Toggle -->
<div id="audience-toggle" class="no-print inline-flex items-center gap-1 bg-gray-100 rounded-full p-1 mb-8 text-sm font-medium">
  <button onclick="setAudience('nontechnical')" ...>Non-Tech</button>
  <button onclick="setAudience('both')" ...>Both</button>
  <button onclick="setAudience('semitechnical')" ...>Semi-Tech</button>
</div>
<p class="text-xs text-gray-400 mb-8 no-print">
  Toggle to adjust the depth of "Do It Yourself" content throughout the playbook.
</p>

<!-- Title Block -->
<div class="inline-block bg-teal-50 ...">A Vibe Coding Playbook</div>
<h1 ...>From Vibe 2 VPS</h1>
<p ...>How to vibe-code right...</p>
<div class="w-16 h-1 ..."></div>

<!-- Hook -->
<p ...>Enough <strong>"Chatting"</strong>...</p>
<p ...>Most AI influencers...</p>

<!-- Phase Stepper (built by JS) -->
<div id="phase-stepper" class="flex items-center justify-center gap-1 flex-wrap mb-10 no-print"></div>

<!-- Export / Share toolbar -->
<div class="no-print flex flex-wrap items-center gap-2 mb-2">
  ... 4 buttons ...
</div>
```

**Step 1: Replace the entire hero section inner content**

Find this exact block (from `<!-- Audience Toggle -->` through end of export toolbar `</div>`):

OLD — remove this block entirely:
```html
      <!-- Audience Toggle -->
      <div id="audience-toggle" class="no-print inline-flex items-center gap-1 bg-gray-100 rounded-full p-1 mb-8 text-sm font-medium">
        <button onclick="setAudience('nontechnical')" data-aud="nontechnical"
          class="aud-btn px-4 py-1.5 rounded-full transition-all">Non-Tech</button>
        <button onclick="setAudience('both')" data-aud="both"
          class="aud-btn px-4 py-1.5 rounded-full transition-all bg-white shadow text-teal-600">Both</button>
        <button onclick="setAudience('semitechnical')" data-aud="semitechnical"
          class="aud-btn px-4 py-1.5 rounded-full transition-all">Semi-Tech</button>
      </div>
      <p class="text-xs text-gray-400 mb-8 no-print">
        Toggle to adjust the depth of "Do It Yourself" content throughout the playbook.
      </p>

      <!-- Title Block -->
```

NEW — replace with (audience toggle removed from top; title block first):
```html
      <!-- Title Block -->
```

**Step 2: Replace the phase stepper div and export toolbar block**

Find this block:
```html
      <!-- Phase Stepper (built by JS) -->
      <div id="phase-stepper" class="flex items-center justify-center gap-1 flex-wrap mb-10 no-print"></div>

      <!-- Export / Share toolbar -->
      <div class="no-print flex flex-wrap items-center gap-2 mb-2">
        <button onclick="window.print()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <i data-lucide="download" class="w-4 h-4"></i>
          Export PDF
        </button>
        <button onclick="downloadMarkdown()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <i data-lucide="file-text" class="w-4 h-4"></i>
          Download MD
        </button>
        <button onclick="shareOnX()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.73-8.835L1.254 2.25H8.08l4.259 5.629 5.905-5.629zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
          Share on X
        </button>
        <button onclick="shareOnLinkedIn()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          Share on LinkedIn
        </button>
      </div>
```

Replace with:
```html
      <!-- Phase Stepper wrapped in "The Journey" box (built by JS) -->
      <div class="no-print text-center mb-10">
        <div class="inline-block border border-gray-200 rounded-2xl px-6 py-4">
          <p class="text-xs font-semibold text-gray-400 uppercase tracking-widest mb-3">The Journey</p>
          <div id="phase-stepper" class="flex items-center justify-center gap-1 flex-wrap"></div>
        </div>
      </div>

      <!-- Export / Share toolbar (centred) -->
      <div class="no-print flex flex-wrap items-center justify-center gap-2 mb-4">
        <button onclick="window.print()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <i data-lucide="download" class="w-4 h-4"></i>
          Export PDF
        </button>
        <button onclick="downloadMarkdown()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <i data-lucide="file-text" class="w-4 h-4"></i>
          Download MD
        </button>
        <button onclick="shareOnX()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.73-8.835L1.254 2.25H8.08l4.259 5.629 5.905-5.629zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
          Share on X
        </button>
        <button onclick="shareOnLinkedIn()"
          class="inline-flex items-center gap-2 text-sm text-gray-500 hover:text-teal-600 border border-gray-200 hover:border-teal-400 rounded-full px-4 py-2 transition-all hover:shadow-sm">
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          Share on LinkedIn
        </button>
      </div>

      <!-- Audience Toggle (moved below export toolbar) -->
      <div id="audience-toggle" class="no-print inline-flex items-center gap-1 bg-gray-100 rounded-full p-1 mb-3 text-sm font-medium">
        <button onclick="setAudience('nontechnical')" data-aud="nontechnical"
          class="aud-btn px-4 py-1.5 rounded-full transition-all">Non-Tech</button>
        <button onclick="setAudience('both')" data-aud="both"
          class="aud-btn px-4 py-1.5 rounded-full transition-all bg-white shadow text-teal-600">Both</button>
        <button onclick="setAudience('semitechnical')" data-aud="semitechnical"
          class="aud-btn px-4 py-1.5 rounded-full transition-all">Semi-Tech</button>
      </div>
      <p class="text-xs text-gray-400 mb-6 no-print">
        Toggle to adjust the depth of "Do It Yourself" content throughout the playbook.
      </p>
```

**Step 3: Rename "Before" to "ReadMe" in the PHASE_LABELS array**

Find:
```js
      { num: 0, short: 'Before' },
```

Replace with:
```js
      { num: 0, short: 'ReadMe' },
```

**Step 4: Verify changes look correct**

Grep to confirm audience toggle has moved to after export toolbar and "ReadMe" is present:
```bash
grep -n "ReadMe\|audience-toggle\|justify-center\|The Journey" "J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/index.html"
```

Expected output includes:
- A line with `The Journey` (inside the stepper wrapper)
- A line with `justify-center` (export toolbar)
- A line with `ReadMe` (PHASE_LABELS)
- The `audience-toggle` div appearing AFTER the export toolbar `</div>`

---

### Task 3: Insert vibe_approach.png figure in Phase 7 diyHTML

**Files:**
- Modify: `J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/index.html` (Phase 7 buildPhaseCard call, around line 1100)

**Context — current Phase 7 diyHTML (line 1100 onwards):**

```js
      diyHTML: `
        <h3>The Maturity Ladder</h3>
        <ul>
          <li><strong>Non-Technical Founder</strong>...
```

**Step 1: Find and replace the opening of diyHTML**

Find:
```js
      diyHTML: `
        <h3>The Maturity Ladder</h3>
```

Replace with:
```js
      diyHTML: `
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
        <h3>The Maturity Ladder</h3>
```

**Step 2: Verify figure is in place**

```bash
grep -n "vibe_approach\|The Maturity Ladder" "J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/index.html"
```

Expected: `vibe_approach.png` appears on the line just before `The Maturity Ladder`.

---

### Task 4: Commit and push to main

**Step 1: Stage both changed files**

```bash
cd "J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS" && git add "assets/vibe_approach.png" index.html
```

**Step 2: Verify staged files**

```bash
git diff --staged --stat
```

Expected:
```
assets/vibe_approach.png | Bin 0 -> XXXX bytes
index.html               | XX insertions(+), XX deletions(-)
2 files changed
```

**Step 3: Commit**

```bash
git commit -m "feat: journey box, ReadMe label, centred buttons, toggle repositioned, vibe approach image"
```

**Step 4: Push to main**

```bash
git push origin main
```

Expected: `main -> main` with commit hash.

**Step 5: Verify HEAD**

```bash
git log --oneline -3
```

Expected: Newest commit message matches step 3.
