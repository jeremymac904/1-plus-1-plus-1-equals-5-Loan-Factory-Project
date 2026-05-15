# 1+1+1=5 — Loan Factory Team Marketing Enhancement Program

Operational source of truth for the Loan Factory Team Marketing Enhancement Program. Strategy lives in ChatGPT. Execution lives in Claude CoWork. Decisions, documentation, and workflows live here.

## What this project is

A 90-day pilot that gives Loan Factory loan officers a way to grow as **collaborative marketing teams** — language-based, niche-based, regional, or audience-based — using infrastructure Loan Factory already runs (Ally, TERA, the Loan Factory portal, GBP, newsletters, Email Drip, IQ).

We are not building new software. We are connecting existing systems into one repeatable team marketing kit and giving Team Leaders the support to run it.

## Status

- **Status:** Approved directionally. Execution mode.
- **Target launch:** June 1, 2026
- **Operational lead:** Jeremy McDonald
- **Cross-functional:** Tara Bartoli (Marketing + TERA)
- **Strategic:** Andre King, Edward Arvizo
- **Executive sponsor:** Thuan Nguyen

## June 1 pilot launch

The pilot opens June 1, 2026 with 4–10 active teams (final number gated by Marketing + TERA capacity). See `EXECUTION_ROADMAP.md` for the week-by-week plan and `NEXT_ACTIONS_QUEUE.md` for the live work queue.

## Operational philosophy

**ACTION > THEORY. EXECUTION > PRESENTATION. SPEED > PERFECTION.**

- Use existing systems before building new ones
- Templates over per-piece review wherever possible
- AI drafts, humans approve, no autopublish
- Friction surfaced fast at the bi-weekly Pilot Team Leader meeting
- Capacity gates team count — not the other way around
- Fewer teams done well beats more teams done sloppy

This is a pilot. It is a learning loop. It is collaborative, not punitive.

## Three-tool ecosystem

### ChatGPT Project — strategy layer

- Strategic thinking and planning
- Leadership communication drafts
- Meeting prep and executive summaries
- Brainstorming and roadmap refinement
- Operational guidance for Jeremy

See `CHATGPT_PROJECT_INSTRUCTIONS.md` — upload this file into the ChatGPT Project so it operates with full context.

### Claude CoWork Project — execution layer

- Markdown-first workflow generation
- Repository organization and documentation
- Workflow mapping and operational systems
- Automation planning (no premature builds)
- Implementation support for Marketing + TERA

See `CLAUDE_COWORK_PROJECT_INSTRUCTIONS.md` — upload into Claude CoWork.

### GitHub repository — source of truth

- Centralized operational documentation
- Shared collaboration with TERA + Marketing
- Workflow versioning
- Execution tracking
- Future technical collaboration

This repo: `1-plus-1-plus-1-equals-5-Loan-Factory-Project` — https://github.com/jeremymac904/1-plus-1-plus-1-equals-5-Loan-Factory-Project

## Role of Marketing

Marketing builds the reusable team kit, reviews intake submissions, owns compliance review at the template level, and supports each new team actively during its first 30 days. See `TERA_AND_TECH_REQUIREMENTS/` and `MARKETING_SYSTEMS/`.

## Role of TERA

TERA stands up team workflows in Ally, configures newsletter templates and Email Drip sequences in the portal, wires Google Business Profiles, and surfaces basic tracking. See `TERA_AND_TECH_REQUIREMENTS/`.

## Role of Team Leaders

Team Leaders recruit and approve LOs onto their team, submit intake, run the team meeting, hit publishing cadence, coordinate content production, submit marketing requests, bring feedback to the bi-weekly Pilot Team Leader meeting, and serve as the single point of contact between the team and HQ. See `TEAM_LEADER_PROGRAM/`.

## Repository structure

```
1-plus-1-plus-1-equals-5-Loan-Factory-Project/
├── README.md                                — this file
├── PROJECT_OVERVIEW.md                      — what the program is and why
├── VISION_AND_MISSION.md                    — long-arc direction
├── EXECUTION_ROADMAP.md                     — week-by-week and 90-day plan
├── CHATGPT_PROJECT_INSTRUCTIONS.md          — uploaded into ChatGPT Project
├── CLAUDE_COWORK_PROJECT_INSTRUCTIONS.md    — uploaded into Claude CoWork
├── PROJECT_DECISIONS_AND_CONTEXT.md         — every locked decision
├── CURRENT_TEAM_AND_STAKEHOLDERS.md         — who's who
├── NEXT_ACTIONS_QUEUE.md                    — live operational queue
├── REPOSITORY_COLLABORATION_GUIDE.md        — how TERA + Marketing use this
├── PROJECT_SOURCE_INDEX.md                  — full document index
├── MEETING_NOTES/                           — Pilot Leader recaps, leadership meetings
├── EXECUTIVE_DECKS/                         — 10-slide deck, briefing PDFs
├── WORKFLOWS/                               — onboarding, publishing, escalation flows
├── AUTOMATIONS/                             — light-automation requests + queue
├── MARKETING_SYSTEMS/                       — kit, templates, Marketing requests
├── TEAM_LEADER_PROGRAM/                     — team profiles, scorecards, candidates
├── FORMS_AND_ONBOARDING/                    — Google Form intake, onboarding checklists
├── LANGUAGE_DIVISIONS/                      — Spanish, Vietnamese, Russian, Korean, Veteran, Investor
├── REPORTING_AND_TRACKING/                  — cadence dashboards, KPI rollups
├── TERA_AND_TECH_REQUIREMENTS/              — Ally, portal, GBP, Email Drip configs
├── PROMPTS/                                 — Gemini / NotebookLM prompts for content drafting
└── ARCHIVE/                                 — superseded docs, kept for reference
```

## Execution-first philosophy

This is not an enterprise PMO. It is not a consultant artifact. It is a living command center for a program that is launching in two and a half weeks.

Three rules govern this repo:

1. **If it isn't useful within 30 days, it doesn't get added.**
2. **If a decision can be made in a meeting, it doesn't go in a 12-page document.**
3. **Every document has an owner. Every section has a deadline.**

## How to use this repo

- **New here?** Read `PROJECT_OVERVIEW.md`, then `EXECUTION_ROADMAP.md`, then `NEXT_ACTIONS_QUEUE.md`.
- **Want the full document map?** `PROJECT_SOURCE_INDEX.md`.
- **Trying to collaborate?** `REPOSITORY_COLLABORATION_GUIDE.md`.
- **Need decisions context?** `PROJECT_DECISIONS_AND_CONTEXT.md`.
- **Looking for who owns what?** `CURRENT_TEAM_AND_STAKEHOLDERS.md`.

## Related folder in Google Drive

Full execution system markdowns (the 11-doc operational command center) live in:

```
Google Drive / Jeremy and Andre BD Folder / Training Knwoledge /
  LOAN_FACTORY_TEAM_MARKETING_EXECUTION_SYSTEM/
```

This GitHub repo wraps that work, adds living queues, and opens it up to TERA + Marketing collaboration over time.
