# Design Doc: "From Vibe 2 VPS" — Interactive Playbook
**Date:** 2026-03-04
**Status:** Approved
**Format:** Self-contained HTML/CSS/JS (static, no backend)
**Output file:** `index.html` (single file, exportable to PDF)

---

## 1. Project Overview

A professional, interactive LinkedIn playbook based on the author's real-world experience building the **Agentic Commerce Readiness (ACR) assessment app** — from a blank Lovable canvas to a production-grade, HTTPS-hosted, VPS-deployed web application.

**Primary Goal:** Teach LinkedIn professionals how to vibe-code *correctly* — with intent, creativity, and a methodology that results in production-grade output.

**Two Titles (both approved, primary used in header):**
- Primary: *"From Vibe 2 VPS"*
- Subtitle/alternate: *"How to vibe-code right, and get it production grade."*

---

## 2. Design Decisions (Confirmed)

| Decision | Choice | Rationale |
|---|---|---|
| Format | Interactive HTML/CSS/JS | Option B — interactivity possible; Option A (PDF) as free byproduct via print |
| Audience | Both non-tech & semi-tech | Option C — dual audience served via toggle |
| Tools handling | Named in story, sidebars evergreen | Option B — authenticity in narrative, longevity in framework |
| Content gaps | All three expanded (A) | Git sync, VPS decision, Perplexity Computer moment — all detailed |
| Structure | The Accordion Playbook | Option 3 — progressive disclosure, dual-tab per phase |

---

## 3. Architecture

### 3.1 Format
- **Single `index.html` file** — no build step, no Node.js, no dependencies
- All CSS and JS inline or via CDN (Tailwind CDN, Lucide icons CDN)
- Works offline, exportable as PDF via browser print
- Hosted on any static server or opened as a local file

### 3.2 Global Interactive Features

| Feature | Behavior |
|---|---|
| **Audience Toggle** | Pinned at top: `[Non-Tech]` `[Both]` `[Semi-Tech]` — adjusts language depth in all "Do It Yourself" tabs |
| **Accordion Cards** | Each phase collapsed by default (headline + 1-line outcome visible); click to expand |
| **Dual Tabs per Phase** | "My Story" tab (personal narrative) + "Do It Yourself" tab (evergreen framework) |
| **Progress Tracker** | Checkbox per phase — reader marks off completed phases |
| **Sticky TOC** | Left sidebar (desktop) / hamburger (mobile) for jump-navigation |
| **Copy-to-Clipboard** | On key prompt snippets and commands |
| **Export to PDF** | Button triggers `window.print()` with a print stylesheet that flattens the accordion |

### 3.3 Audience Toggle Logic

The toggle controls a CSS class on `<body>`:
- `audience-nontechnical` → shows simplified language in "Do It Yourself" tabs; hides advanced technical callouts
- `audience-both` → default; shows all content
- `audience-semitechnical` → shows full technical depth in "Do It Yourself" tabs; shows advanced callouts

---

## 4. Content Structure — Phase by Phase

### Cover / Hero Section
- Title: **"From Vibe 2 VPS"** (large, bold)
- Subtitle: *"How to vibe-code right, and get it production grade."*
- Hook paragraph: *"Enough 'Chatting' with AI. It's time to Engage."*
- Journey overview: 7 phases shown as a horizontal numbered stepper graphic
- Audience toggle selector (prominent, explained)
- "Start Reading" CTA scrolls to Phase 0

---

### Phase 0 — Before You Start
**Collapsed headline:** *"What vibe coding actually is — and what it isn't"*
**1-line outcome:** *"Set the right expectations before touching a single tool."*

**My Story tab:** The misconception in the market. Why AI influencers planning fake vacations miss the point. The author's call to use a real industry use case.

**Do It Yourself tab:** Definition of vibe coding. The spectrum from 1-line prompt to production-grade methodology. What this playbook covers and what it doesn't.

---

### Phase 1 — Pick Your Use Case
**Collapsed headline:** *"Why your use case is the only decision that truly matters"*
**1-line outcome:** *"You chose the right problem. Now build the right solution."*

**My Story tab:** Why agentic commerce readiness assessment. 15+ years of maturity assessment experience. The value for Retail/CPG executives. How deep domain knowledge is the unfair advantage.

**Do It Yourself tab:** Framework for picking a use case — 3 criteria: (1) domain you know cold, (2) audience you can reach, (3) problem that benefits from automation. Anti-patterns to avoid.

---

### Phase 2 — Build It in Lovable
**Collapsed headline:** *"From blank canvas to working app — without writing a line of code"*
**1-line outcome:** *"A functional, styled, multi-page web app — entirely AI-generated."*

**My Story tab:**
- Step 2a: Building the feature list and design spec before opening Lovable
- Step 2b: Prompt engineering — researching tools, landing on Lovable, using ChatGPT to refine the prompt
- Token discipline: 5 free tokens/day → must be organized
- Three-part prompt strategy (68K chars split across 3 sequential prompts with continuity headers)
- **Prompt Snippets (with copy-to-clipboard):**
  1. Opening brief snippet
  2. Design system spec snippet (exact hex codes, no-deviate instruction)
  3. Question filtering logic snippet (CRITICAL label)
  4. Scoring logic snippet
  5. Multi-part continuity header snippet

**Do It Yourself tab:**
- Generic prompt engineering framework: Research → Plan → Design spec → Prompt → Refine
- Why one-line prompts fail
- How to structure a long prompt (tech stack, design, data, pages, logic, content)
- Token management tips
- Recommended prompt resources (e.g., lovableprompts.app)
- Tool-agnostic tips for any vibe coding platform

---

### Phase 3 — Code Liberation: GitHub Sync
**Collapsed headline:** *"Own your code. Escape the platform."*
**1-line outcome:** *"Your codebase is now yours — portable, inspectable, version-controlled."*

**My Story tab:** The "Edit with Lovable" badge problem. Realizing that paid subscription = locked in. Discovering GitHub sync (one click in Lovable). Opening in Cursor to verify no Lovable server references remain.

**Do It Yourself tab (from expanded Q4 content):**
> "By moving the project to GitHub, you own the generated codebase, stored safely outside of Lovable's platform. This protects your work from potential platform issues, service changes, or account problems. GitHub integration allows you to clone the repository and work locally in your preferred IDE (such as Cursor), which provides granular control and customization options that may be limited within Lovable's visual editor. Once the code is on GitHub, you are free to self-host or deploy the application to any platform (e.g., Vercel, AWS)."

Generic tips: What GitHub gives you (5 bullets). How to check for platform dependencies using Cursor's AI feature. When to use Vercel vs VPS.

---

### Phase 4 — Choose Your Hosting
**Collapsed headline:** *"Free hosting is real. Picking the right one isn't obvious."*
**1-line outcome:** *"A VPS selected, configured, and ready — without paying a cent."*

**My Story tab (from expanded Q4 content):**
- Why shared hosting ($5/month) didn't work (Node.js requirement, upgrade cost = 6x)
- OCI vs AWS comparison: OCI = better "Always Free" tier; AWS = better documentation, Claude-assisted setup
- The pivot: Started with OCI, switched to AWS because of documentation richness and Claude compatibility
- Quote: *"Later realized that the help files and documentation available for AWS was plenty and taking help from Claude would be easy. Hence, decided to shift course from OCI to AWS."*

**Do It Yourself tab:** Decision framework for hosting — 4 questions to ask. Free tier comparison table (OCI vs AWS vs Vercel vs Railway). When a VPS is overkill vs necessary (Node.js / backend requirement test).

---

### Phase 5 — Deploy to VPS *(The Big One — Special Treatment)*
**Collapsed headline:** *"From local to live — and an AI agent takes the wheel"*
**1-line outcome:** *"Your app is running live at a public URL. You barely clicked a button."*

**Sub-steps (nested accordion within Phase 5):**

#### 5a — Set Up EC2
My Story: Creating AWS account, reading EC2 documentation, first error hit.
Do It Yourself: EC2 setup checklist (generic, tool-agnostic equivalent steps).

#### 5b — ★ The Perplexity Computer Moment *(Starred, featured)*
**My Story tab:**
> *"I had this instinct that Perplexity assistant, even without the Max plan, would leverage some capabilities of Perplexity Computer as it was launched just a few days ago. So, tapped into Comet browser, created the AWS account and started to configure the EC2 instance. Hit the first error and I asked Perplexity Assistant to take over. Gave it a couple of permissions which it wanted — like accessing the browser. No different from what I had done with Claude Code, Craft agent and OpenClaw. Using this permission, it started to take screenshots, read what was on the screen, scroll, click buttons, fill text boxes, and submitting them on my behalf."*

**Proof Panel (inline film-strip, two screenshots side by side):**
- **Left screenshot:** Perplexity building its to-do list, cloning the repo, preparing SSH connection
- **Right screenshot:** Perplexity navigating AWS Console — "DNS added. I see the status in AWS as Issued."
- Caption: *"I didn't click a single button in this step."*

**Do It Yourself tab:** What Perplexity Computer is. How to access via Comet browser. What permissions to grant. What to expect. Safety note on permissions.

#### 5c — App Goes Live
My Story: `http://acr-tool.jkspeaks.com` — Phase 3 complete. The moment.
Do It Yourself: Verification checklist after deployment.

---

### Phase 6 — Go Secure: HTTP → HTTPS
**Collapsed headline:** *"Your domain. Your SSL. Your credibility."*
**1-line outcome:** *"`http://acr-tool.jkspeaks.com` → `https://acr-tool.jkspeaks.com` — in under 5 minutes."*

**My Story tab:** One-line prompt to Perplexity Assistant. It set up certificates, load balancer, and everything else. *"Why am I reading pages and pages of documentation when I can ask AI to help?"* Total time: under 5 minutes.

**Do It Yourself tab:** What HTTPS requires (SSL cert, load balancer or reverse proxy). Free options (Let's Encrypt, AWS ACM). The AI-assisted approach vs the documentation approach.

---

### Phase 7 — What's Next
**Collapsed headline:** *"This isn't the end. This is Version 1."*
**1-line outcome:** *"A framework you can apply to any use case, any time."*

**My Story tab:** The author's own next steps for the ACR app — observability, token-based login, multi-org support, chatbot on the report, voice-activated survey, reassessment at 12 months.

**Do It Yourself tab:** How to think about iteration. The maturity ladder: Non-Technical Founder → Vibe Architect → Agentic Engineer. What "production grade" means and when you've reached it.

---

### Closing Section — The Call to Action
Full-width, bold:
> *"Stop writing one-line prompts to vibe code an app and call it a day. Pick a real-world problem, apply your thinking and creativity, scale it till it satisfies your hunger."*

> *"The era of the 'Non-Technical Founder' is over. 'Vibe Architects' are commodity now. Scale up to become 'Agentic Engineers' and create the impact."*

---

### End Matter — Non-Accordion Sections

#### Tools Landscape *(As of Early 2026 — verify before use)*
A clean, dated table:

| Tool | Category | What it does | Free tier? |
|---|---|---|---|
| Lovable | App builder | Full-stack AI code generator | Yes (5 tokens/day) |
| Bolt | App builder | Alternative to Lovable | Yes |
| Cursor | IDE | Local AI-assisted code editor | Yes |
| GitHub | Version control | Code hosting, portability | Yes |
| Supabase | Backend/DB | Postgres + auth + storage | Yes |
| AWS EC2 | VPS | Cloud server (industry standard) | Yes (6 months) |
| Oracle Cloud (OCI) | VPS | Always-free VPS | Yes (permanent) |
| Perplexity (Comet) | AI agent | Browser-use computer agent | Limited (no Max plan needed) |
| Vercel | Hosting | Static + serverless deploy | Yes |
| Namecheap / IONOS | Domain | Domain registration | No |

#### The Methodology *(Printable, Standalone)*
A visual one-pager summarizing the 7 phases as a reusable framework — generic, no tool names, no personal story. Just the skeleton.

---

## 5. Visual Design Spec

| Element | Value |
|---|---|
| Background | `#FFFFFF` |
| Primary text | `#1a1a1a` |
| Secondary text | `#666666` |
| Accent | `#0f172a` (dark navy) with `#6366f1` (indigo) highlights |
| Phase cards | White bg, `1px solid #e5e7eb` border, `border-radius: 16px` |
| Active tab | Indigo underline, bold label |
| Audience toggle | Pill-style selector, active = indigo fill |
| Progress checkboxes | Custom styled, indigo on check |
| Proof panel | Dark `#0f172a` background with white text captions — makes screenshots pop |
| Copy button | Ghost style, small, icon only |
| Export PDF button | Primary, top-right corner |
| Fonts | `Inter` via Google Fonts |
| Icons | Lucide React (CDN) |
| Mobile breakpoint | `768px` — single column, hamburger TOC |

---

## 6. File Output

```
J:/Office_CBC/Whitepaper/LinkedIN/Vibe2VPS/
├── index.html          ← The complete playbook (single file)
├── assets/
│   ├── perplexity-screen-1.png   ← Screenshot 1 (Perplexity to-do + SSH)
│   └── perplexity-screen-2.png   ← Screenshot 2 (AWS Console navigation)
└── docs/
    └── plans/
        └── 2026-03-04-from-vibe-2-vps-playbook-design.md  ← This file
```

The two screenshots provided by the user will be saved to `assets/` and referenced in the proof panel.

---

## 7. Implementation Notes

- **No build step** — pure HTML/CSS/JS, works as a file:// URL
- **Tailwind via CDN** — `<script src="https://cdn.tailwindcss.com"></script>`
- **Lucide icons via CDN** — `<script src="https://unpkg.com/lucide@latest"></script>`
- **Accordion JS** — vanilla JS, no framework
- **Audience toggle JS** — sets `data-audience` attribute on `<body>`, CSS selectors handle visibility
- **Print CSS** — `@media print` expands all accordions, hides toggle/TOC/buttons
- **Screenshots** — embedded as `<img>` tags referencing `assets/` folder

---

## 8. Next Step

Invoke `superpowers:writing-plans` to create a detailed implementation plan.
