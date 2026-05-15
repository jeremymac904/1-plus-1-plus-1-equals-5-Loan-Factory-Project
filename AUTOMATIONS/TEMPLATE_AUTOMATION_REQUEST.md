# Automation Request — [Short Title]

**Date submitted:** YYYY-MM-DD
**Submitted by:** [Name + Team / Pod]
**Type:** [Light automation (in scope) / Phase 2 build (out of scope for June 1)]
**Priority:** [Standard / Time-bound (specify date) / Blocking launch]
**Target completion:** YYYY-MM-DD

## Manual process today

[Describe the manual process that currently exists. Be specific about steps, owners, and time per step.]

## What you want automated

[Describe what the automation should do. Trigger → handler → output.]

- **Trigger:** [What event starts it]
- **Handler:** [What system processes it]
- **Output:** [What lands where]
- **Notification:** [Who gets notified, on what channel]

## Why this matters

[What breaks at scale if this stays manual. Or what compounds if it's automated.]

## Frequency / volume estimate

- Current volume: [How often does the manual process run]
- Projected volume by Day 90: [If automation succeeds, how often]

## Existing systems involved

Mark which of these the automation touches:

- [ ] Google Form intake
- [ ] Ally
- [ ] Loan Factory portal (Email Campaign / Send Email)
- [ ] Loan Factory portal (Email Drip)
- [ ] Loan Factory portal (IQ)
- [ ] GBP
- [ ] Gemini / NotebookLM
- [ ] Loan Factory CRM
- [ ] Google Chat / Slack
- [ ] Trello / Asana
- [ ] Zapier or similar light automation
- [ ] Other: [specify]

## What this is NOT

- This is not a request to build new software for June 1 (those go to Phase 2 backlog)
- This is not a request to integrate two systems that don't have an existing connection

If the request requires real engineering work, mark Type as "Phase 2 build" above.

## Acceptance criteria

The automation is done when:

- [ ] [Specific outcome — e.g., "Form submission triggers Google Chat alert in #pilot-intake"]
- [ ] [Tested end-to-end with at least 3 sample inputs]
- [ ] [Logged in `NEXT_ACTIONS_QUEUE.md` as completed]
- [ ] [Documentation added to `TERA_AND_TECH_REQUIREMENTS/`]

## TERA pod response

_(Filled in by TERA after triage.)_

- **Triaged by:** [Name]
- **Triaged date:** YYYY-MM-DD
- **In scope for Phase 1?:** [Yes / No — if no, parked to Phase 2 backlog]
- **Approach:** [How TERA plans to implement]
- **Estimated completion:** YYYY-MM-DD
- **Dependencies:** [What else has to be in place first]

## Resolution

_(Filled in when automation is shipped.)_

- **Shipped date:** YYYY-MM-DD
- **Where it lives:** [System, workflow ID, or doc path]
- **Tested by:** [Name]
- **Documentation:** [Path to runbook in `TERA_AND_TECH_REQUIREMENTS/`]

## Cross-references

- Related workflow: [Path]
- Related team (if team-specific): `TEAM_LEADER_PROGRAM/[team_name]_profile.md`

---

**File naming convention:** `YYYY-MM-DD_short_title_automation_request.md`
Example: `2026-06-15_intake_form_chat_alert_automation_request.md`
