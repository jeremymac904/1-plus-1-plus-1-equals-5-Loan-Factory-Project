# TERA_AND_TECH_REQUIREMENTS

Platform configs, technical setup docs, and TERA pod working space.

## What goes here

- Ally workflow setup per team
- Portal newsletter audience + template configurations
- Email Drip sequence definitions
- GBP setup checklists per team
- Tracking dashboard structure (Ally + portal + GBP)
- TERA pod runbooks
- Light automation runbooks (post-ship)
- Platform escalation procedures

## What doesn't

- New software builds (those are Phase 2 backlog in `AUTOMATIONS/`)
- Marketing creative decisions (those live in `MARKETING_SYSTEMS/`)
- Strategy documents

## Existing systems in scope

| System | Owner | Purpose |
| --- | --- | --- |
| Ally | TERA | Social scheduling per team |
| Loan Factory portal — Email Campaign / Send Email | TERA | Newsletters + Realtor outreach |
| Loan Factory portal — Email Drip | TERA | New-contact nurture |
| Loan Factory portal — IQ | TERA | Monthly homeowner equity / market reports |
| Google Business Profile | Marketing + Team Leader | Team-level GBP per market |
| Loan Factory CRM | TERA | Application attribution to teams |

## Naming

- Platform setup doc: `[platform]_setup_runbook.md`
- Per-team config: `[team_name]_[platform]_config.md`
- Light automation runbook: `[automation_name]_runbook.md`

## SLAs

| Action | SLA |
| --- | --- |
| Channel setup per new team | 7 business days |
| Platform troubleshooting | 48 hours |
| Compliance review on platform changes | 3 business days (Compliance owns) |

## Cross-references

- `AUTOMATIONS/` — automation requests and Phase 2 backlog
- `WORKFLOWS/` — operational workflows that use these systems
- `REPORTING_AND_TRACKING/` — what gets pulled from these platforms

## Future engineering collaboration

When TERA is ready to deepen technical collaboration in this repo:

- GitHub issues for tracked work
- PRs for config changes that need review
- A `scripts/` folder if automation scripts need version control

Phase 1 doesn't need that — markdown is enough.
