# From Vibe 2 VPS

> **A Grounded Playbook** · Based on real experience · Built with vibe

A single-page interactive playbook documenting a real-world journey from a blank canvas to a production-grade, HTTPS-hosted, VPS-deployed web app — built entirely with AI coding tools.

**🔗 Live site:** [jkspeaks.github.io/vibe2vps](https://jkspeaks.github.io/vibe2vps/)

---

## What This Is

Most AI content online treats vibe coding as "write one prompt, accept what you get." This playbook argues otherwise.

Vibe coding done right is **you** — with your domain expertise and design instinct — using AI as the engine while staying the architect. This site walks through 8 phases of a real industry project (an Agentic Commerce Readiness Assessment tool), from first prompt to live production URL, with every decision, mistake, and AI-agent moment documented.

The methodology is tool-agnostic and can be applied to any use case in any domain.

---

## Two Audiences, One Playbook

Each phase of the playbook has two tabs:

| Tab | Who it's for |
|-----|-------------|
| **My Story** | Readers who want the real narrative — what was built, what broke, what surprised, and why decisions were made |
| **Do It Yourself** | Practitioners who want the reusable framework — checklists, anti-patterns, and generic steps to apply to their own use case |

Use the **depth toggle** at the top of the page to filter content by your technical level (Non-Tech / Both / Semi-Tech).

---

## The Journey (8 Phases)

| Phase | Title | Outcome |
|-------|-------|---------|
| **ReadMe** | What vibe coding actually is — and what it isn't | Set the right expectations before touching a single tool |
| **1** | Why your use case is the only decision that truly matters | A problem worth solving, with a real audience |
| **2** | From blank canvas to working app — without writing a line of code | A functional, styled, multi-page web app — entirely AI-generated |
| **3** | Own your code. Escape the platform. | Codebase on GitHub, portable and version-controlled |
| **4** | Free hosting is real. Picking the right one isn't obvious. | A VPS selected, configured, and ready — without paying a cent |
| **5** ★ | From local to live — and an AI agent takes the wheel | App running live at a public URL — barely clicked a button |
| **6** | Your domain. Your SSL. Your credibility. | `http://` → `https://` in under 5 minutes |
| **7** | This isn't the end. This is Version 1. | A framework you can apply to any use case, any time |

---

## Features

- **Dual-audience tabs** — "My Story" (narrative) and "Do It Yourself" (framework) on every phase
- **Depth toggle** — filters DIY content between Non-Tech, Both, and Semi-Tech levels
- **Dark mode** — persisted via `localStorage`, flash-prevention on load
- **Sticky navbar** — JK logo linking to [jkspeaks.com](https://www.jkspeaks.com), dark mode toggle
- **Phase stepper** — visual "The Journey" navigation strip
- **Accordion phases** — expand/collapse individual phases or all at once
- **Progress checkboxes** — mark phases complete as you work through them
- **Scroll-spy TOC** — fixed sidebar dot navigation (desktop only)
- **Export toolbar** — Export as PDF, Download as Markdown, Share on X, Share on LinkedIn
- **Embedded images** — Prioritization matrix (Phase 7 My Story), Vibe Coding Approach diagram (Phase 7 DIY)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Structure | Single static `index.html` — no build step, no framework |
| Styling | [Tailwind CSS](https://tailwindcss.com/) via CDN |
| Icons | [Lucide](https://lucide.dev/) via CDN |
| JavaScript | Vanilla JS — accordion, tabs, dark mode, audience toggle, scroll-spy, Markdown export |
| Hosting | GitHub Pages |

No npm. No bundler. No dependencies to install.

---

## Project Structure

```
vibe2vps/
├── index.html              # Entire site — all HTML, CSS, and JS
├── assets/
│   ├── jk_logo2.png        # Navbar logo
│   ├── vibe_approach.png   # Vibe coding approach diagram (Phase 7 DIY)
│   ├── Prioritization matrix.png  # Phase 7 roadmap image
│   ├── perplexity-screen-1.png    # Phase 5 Perplexity Computer evidence
│   └── perplexity-screen-2.png    # Phase 5 Perplexity Computer evidence
└── docs/
    └── plans/              # Design docs and implementation plans (dev reference)
```

---

## Running Locally

No setup required. Open the file directly in any browser:

```bash
git clone https://github.com/jkspeaks/vibe2vps.git
cd vibe2vps
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Or serve it with any static file server:

```bash
npx serve .
# → http://localhost:3000
```

---

## The Vibe Coding Stack Used to Build the ACR Tool

| Tool | Role |
|------|------|
| [Lovable](https://lovable.dev) | AI code generation (React/TypeScript app) |
| [Supabase](https://supabase.com) | Backend database and auth |
| [GitHub](https://github.com) | Version control and escape from platform lock-in |
| [Cursor](https://cursor.sh) | AI-enabled IDE for local editing |
| [AWS EC2](https://aws.amazon.com/ec2/) | VPS hosting (free tier) |
| [AWS ACM + ALB](https://aws.amazon.com/certificate-manager/) | SSL certificate and HTTPS |
| [Perplexity Computer](https://www.perplexity.ai) | AI agent that navigated the AWS Console |
| [Claude Code](https://claude.ai) | This playbook site was built and iterated with Claude Code |

---

## Author

**JK** — [jkspeaks.com](https://www.jkspeaks.com)

Built to demonstrate that vibe coding is an art — and if done right, it scales to production grade.

---

*Grounded Playbook · Built with vibe*
