# REPORTING_AND_TRACKING

Cadence rollups, KPI dashboards, monthly scorecards, and reporting cadence definitions.

## What goes here

- Weekly cadence compliance rollup (green / yellow / red across all teams)
- Monthly per-team scorecards (rolled up here; individual scorecards live in `TEAM_LEADER_PROGRAM/`)
- Monthly leadership update one-pagers
- 90-day pilot retro
- Dashboard structure definitions (what we pull from Ally, portal, GBP, CRM)

## What doesn't

- Raw exports from platforms (those stay in source platforms; this folder holds rollups and analyses)
- Real-time live data — this is a documentation repo, not a live BI tool

## Reporting cadence

| Cadence | Output | Audience |
| --- | --- | --- |
| Weekly | Cadence compliance check | Jeremy + Tara |
| Bi-weekly | Pilot Leader meeting recap (lives in `MEETING_NOTES/`) | All Team Leaders + pods |
| Monthly | Per-team scorecard (lives in `TEAM_LEADER_PROGRAM/`; rollup here) | Team Leader + Jeremy |
| Monthly | Pilot health summary | Thuan + Andre + Edward |
| 90-day | Pilot retrospective | Full leadership |

## Naming

- Weekly rollup: `weekly_cadence_YYYY-MM-DD.md`
- Monthly rollup: `monthly_pilot_health_YYYY-MM.md`
- Leadership update: `leadership_update_YYYY-MM.md`
- 90-day retro: `pilot_retro_YYYY-MM-DD.md`

## Metrics tracked

See the Drive execution folder `KPI_AND_MONITORING_FRAMEWORK.md` for full definitions:

- Posting consistency (Ally)
- Newsletter activity (portal Send Email)
- Realtor outreach (portal contact list + sends)
- GBP performance (GBP insights)
- Recruiting growth (Team Leader self-report)
- Meeting attendance (roll call)
- Application growth (Loan Factory CRM, attributed by team)

## Tooling

Phase 1: Google Sheets + per-team scorecards stitched manually.
Phase 2 (post-August 30): unified dashboard if the pilot proves it's needed.

## Cross-references

- `TEAM_LEADER_PROGRAM/` — individual team scorecards
- `MEETING_NOTES/` — meeting recaps where reports get discussed
- Drive: `KPI_AND_MONITORING_FRAMEWORK.md` — full metric framework
