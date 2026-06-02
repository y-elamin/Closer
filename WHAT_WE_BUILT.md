# Closer — What We've Built So Far

> Handoff doc for the planner agent. This describes the **current working prototype** (not aspiration). Use it to pick a demo story.

---

## One-line

**Closer is an agentic work OS that turns one vague ticket into an accurate, assigned, prioritized backlog — created live in ClickUp — with a human approval gate in the middle.**

Tagline in the product: *"Most tools manage work. Closer closes work."*

---

## The core transformation (the "before → after")

- **Before:** a messy ticket — `ENG-482: Improve onboarding experience / "Customers are complaining onboarding is confusing. Can someone improve it?"` Priority: Unspecified. No owners, no data, no scope, no plan.
- **After:** an epic + 5 sub-tickets, each assigned, prioritized, estimated, with dependencies and blockers flagged — pushed into a ClickUp-style board, ready to start.

The single human action is: **paste a ticket, click Analyze.** Then later, **review/approve, click Create.** Everything between is agents.

---

## What actually exists (current build)

A single self-contained `index.html` (React + Tailwind via CDN, no backend, no API keys). All orchestration is **scripted/simulated on a timeline** so the demo is deterministic and never fails. Light mode, Linear/Vercel/Cursor aesthetic.

### Screen 1 — Ticket Intake
- Left: the messy ticket (editable title + description), author "Maria (PM)", priority "Unspecified".
- Right: preview of the 8 agents that will run.
- One button: **Analyze Ticket**.

### Screen 2 — Agent Command Center
- A live grid of **8 agent cards**. Each card has: name, one-line purpose, a **status** (Idle → Running → Waiting / Blocked → Completed), a **streaming reasoning log** (token-by-token feel), and a **structured output** that fills in when the agent finishes.
- Cards light up sequentially as agents run.

### Screen 3 — Activity Timeline
- A chronological feed (09:01 → 09:08) of agents acting and **handing off to each other** — the visible "agents talking to agents" beat.

### Screen 4 — Create Tickets (two stages)
1. **Review & Approve** (the human-in-the-loop gate):
   - All 6 drafted tickets in a table.
   - Per ticket: **confidence score** (color-coded bar + %), **approve checkbox** (uncheck to exclude), **editable title** (inline), **editable owner** (dropdown), **editable priority** (dropdown).
   - **"+ Add task"** to append your own ticket.
   - Sticky bottom CTA: **"Create N tickets in ClickUp →"** with running count + avg confidence.
2. **ClickUp board** (the deliverable):
   - A ClickUp-styled screen (ClickUp logo/topbar, List/Board/Calendar tabs, "Pushed by Closer" badge).
   - The epic + approved sub-tickets get **created live, one at a time**, each with a green "+ created" pop, indented under the epic, with assignee avatar, status pill, priority flag, estimate.
   - Ends on stats + the "Closer closes work" line.

---

## The 8 agents (and what each one outputs in the demo)

| # | Agent | Job | Concrete output shown |
|---|-------|-----|------------------------|
| 1 | **Intake** | Understand the task | Goal, **67% confidence**, 4 missing-info gaps, stakeholder list |
| 2 | **Clarification** | Find the gaps | 3 clarifying questions |
| 3 | **Stakeholder** | Route to owners | Mock **Slack / ClickUp / Email** messages sent (with statuses: Awaiting / Read / Sent) |
| 4 | **Research** | Gather context | "16 complaints", dropoff at **step 3 (41%)**; **hoverable sources** — 16 tickets, 1 Amplitude funnel, 4 reviews, each with a detail popover |
| 5 | **Dependency** | Surface blockers | `AUTH-204` (Ahmed), `ANALYTICS-17` (Sarah), risk Medium |
| 6 | **Planning** | Research → work | Epic + 5 subtasks with estimates |
| 7 | **Execution** | Dev handoff | Implementation brief (FE/BE/Analytics/Testing), Cursor prompt, GitHub issues |
| 8 | **Closer** | Chase until done | Detects Analytics silent 24h → **auto follow-up sent**, escalation scheduled |

The generated backlog:
- **ONB-100 (EPIC)** Improve onboarding completion — Maria — High — 92% conf
- **ONB-101** Add onboarding progress indicator — Lena — Frontend — High — 95%
- **ONB-102** Simplify registration form — Omar — Frontend — High — 74% — ⛒ blocked by AUTH-204
- **ONB-103** Rewrite onboarding copy — Priya — Content — Medium — 88%
- **ONB-104** Emit funnel analytics events — Sarah — Backend — Medium — 83% — ⛓ ANALYTICS-17
- **ONB-105** A/B experiment new vs control — Tom — Testing — Medium — 79%

---

## What makes it a *multi-agent* story (judge-relevant)

- **Multiple specialized agents**, each with its own card, status, logs.
- **Agents hand off** — Intake's gaps feed Clarification; Research/Dependency feed Planning; Planning feeds Execution. Visible in the timeline.
- **Agents take real-looking actions** — send Slack/ClickUp/Email, open issues, follow up.
- **Reduces human coordination** — the "before" is ~2 days of chasing people; the "after" is one review click.
- **Human-in-the-loop** — confidence scores + approval gate = trust, not a black box.

---

## Honest scope / caveats (so the story doesn't overclaim)

- Everything is **simulated** — no real Gemini calls, no real ClickUp/Slack/GitHub. It's a scripted demo, intentionally, for reliability.
- The narrative is built around **one example ticket** (onboarding). Pasting a different ticket still runs the same scripted output.
- The ClickUp screen is a **styled mock**, not the real ClickUp.
- No persistence, no auth, no team accounts.

---

## Assets that exist in the repo

- `index.html` — the full working prototype (open in any browser).
- `README.md` — architecture, agent table, demo script, pitch, landing copy.
- Repo: https://github.com/y-elamin/Closer

---

## Hooks the planner could build a story around

Pick one spine; these are the strongest beats available **with what's already built**:

1. **"The 2-day ticket, closed in 90 seconds."** Lead with the pain (engineer's wasted coordination time), end on the ClickUp board filling up.
2. **"Agents that talk to each other."** Lean on the timeline + Stakeholder agent sending Slack/Email — emphasize coordination, not chat.
3. **"Trust, not magic."** Lead with the confidence scores + approval gate — the differentiator vs. "another autonomous black box."
4. **"From one sentence to a sprint backlog."** Visual payoff = the live ticket creation in ClickUp.
5. **"Closer closes."** Use the Closer agent (auto follow-up) as the memorable closing line — the thing that chases humans so humans don't chase each other.

**Strongest single moment for a 3-min live demo:** the transition from the *Review & Approve* screen → tickets **materializing one-by-one in ClickUp**. That's the "wow."
