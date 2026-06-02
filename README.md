# ✦ Closer

**The agentic work OS that turns ambiguous work into finished work.**

> A vague ticket goes in. A dev-ready execution plan comes out.

## Run it

```bash
open closer/index.html
```

No build, no API keys, no backend. A single self-contained file (React + Tailwind via CDN) — perfect for a flawless live demo. Everything is realistic simulated data; the orchestration is fully scripted so the demo never fails.

---

## 1. Product architecture

```
                 ┌──────────────────────────────────────┐
   Messy ticket ─►            ORCHESTRATOR               │
                 │  (sequences agents, shares context)   │
                 └──┬───────────────────────────────────┘
                    │  events bus (agents read each other's output)
  ┌─────────────────┴───────────────────────────────────────────┐
  ▼        ▼        ▼        ▼        ▼        ▼        ▼         ▼
Intake  Clarify  Stakeh.  Research  Deps   Planning  Execution  Closer
  │        │        │        │        │        │         │         │
  │  gaps  │ q's    │ Slack  │ themes │ blocks │ epic+   │ brief + │ chases
  │        │        │ ClickUp│ funnel │ risk   │ subtasks│ issues  │ owners
  └────────┴────────┴────────┴────────┴────────┴─────────┴─────────┘
                    │
                    ▼
        Final deliverable: execution plan → "Ready for development"
```

**Multi-agent value:** agents pass context forward (Intake's gaps → Clarification's questions → Stakeholder's routing → Research's findings → Planning's subtasks → Execution's brief). The Closer Agent monitors and follows up so coordination happens without humans.

## 2. The 8 agents

| # | Agent | Job | Talks to / produces |
|---|-------|-----|---------------------|
| 1 | Intake | Understand the task | goal, 67% confidence, gaps, stakeholders |
| 2 | Clarification | Find missing info | 3 clarifying questions |
| 3 | Stakeholder | Route to owners | Slack / ClickUp / Email (mock) |
| 4 | Research | Gather context | 16 complaints, dropoff at step 3 |
| 5 | Dependency | Surface blockers | AUTH-204, ANALYTICS-17, risk medium |
| 6 | Planning | Research → work | epic + 5 subtasks |
| 7 | Execution | Dev handoff | brief, Cursor prompt, 5 GitHub issues |
| 8 | **Closer** | Chase until done | auto follow-up after 24h, escalation |

## 3. Screens

1. **Ticket Intake** — paste ticket (left), preview of agents (right), one *Analyze Ticket* button.
2. **Agent Command Center** — grid of agent cards: name, status (Idle/Running/Waiting/Blocked/Completed), streaming logs, live output.
3. **Activity Timeline** — chronological, alive feed of inter-agent activity.
4. **Final Deliverable** — Before vs After, stats, copyable Cursor prompt + GitHub issues.

## 4. Demo script (3 min)

- **0:00** "Every engineer knows this ticket." Show `ENG-482: Improve onboarding`. "It's unworkable — no data, no owners, no scope."
- **0:20** Click **Analyze Ticket**. "I paste and click once. Watch."
- **0:30** Command Center lights up. Narrate: Intake scores it 67% complete and finds 4 gaps → Clarification writes the questions → **Stakeholder Agent fires Slack/ClickUp/Email automatically.** "No human sent those."
- **1:10** Research returns 16 complaints + dropoff at step 3. Dependency flags AUTH-204 (blocked). Planning generates an epic + 5 subtasks.
- **1:50** Execution produces a Cursor prompt + 5 GitHub issues.
- **2:10** Closer Agent: "Analytics went quiet for 24h — so Closer followed up itself."
- **2:30** Jump to **Final Deliverable.** Before vs After. "Two days of coordination, zero meetings, done."
- **2:50** Land the line: *"Most tools manage work. Closer closes work."*

## 5. Pitch

Engineering teams don't lose time writing code — they lose it on the coordination *before* code: chasing context, owners, data, dependencies. Closer is an agentic work OS where eight specialized agents do that coordination autonomously, talking to each other and to your tools, turning an ambiguous ticket into a development-ready plan. Linear shows you work. Cursor helps you write it. **Closer closes the gap in between — and closes the work.**

## 6. Landing copy

> ### Ambiguous work in. Finished work out.
> Closer is the agentic work OS. Eight agents read your messy tickets, chase the right people, gather the context, map the blockers, and hand your team a dev-ready plan — automatically.
>
> **Stop coordinating. Start shipping.**

## 7. Production stack (when wired up)

Next.js + React + Tailwind · Node.js orchestrator · Gemini API per agent · mock ClickUp / Slack / GitHub adapters (swap for real). The prototype mirrors this structure with local demo state.
