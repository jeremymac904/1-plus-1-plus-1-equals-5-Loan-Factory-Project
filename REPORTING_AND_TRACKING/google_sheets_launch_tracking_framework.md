# Google Sheets Launch Tracking Framework

**Owner:** Jeremy McDonald (with Tara for cross-pod coordination)
**Status:** Active for Wave 1 launch
**Purpose:** Lightweight, manual launch tracking for the 1+1+1=5 program. Google Sheets first, existing systems first, no custom dashboard.

## Why this exists

Thuan, Andre, and the team agreed... no new software for June 1. Manual tracking in Google Sheets covers everything Wave 1 needs. If the pilot proves we need a custom dashboard, that becomes Phase 2 work coordinated with TERA.

## The single source sheet

**File name:** `1+1+1=5 Launch Tracking Sheet`
**Location:** Google Drive / Jeremy and Andre BD Folder / Training Knowledge / LOAN_FACTORY_TEAM_MARKETING_EXECUTION_SYSTEM / Tracking /
**Access:** Jeremy (owner), Tara (editor), Marketing pod lead (editor), TERA pod lead (editor), Compliance lead (editor), Andre (viewer), Thuan (viewer)
**Update cadence:** Weekly minimum. Daily during launch week (May 25 to June 5).

## Columns

One row per team. Add a row when an intake is submitted.

| # | Column | Type | Notes |
| --- | --- | --- | --- |
| 1 | Team name | Text | As submitted on intake |
| 2 | Division | Dropdown | Chinese, Vietnamese, Russian, Spanish, Korean, Latino, Veteran or Military, Investor or DSCR or Fix and Flip, Regional, Audience-based, None |
| 3 | Team Leader | Text | Full name |
| 4 | Team Leader NMLS | Text | NMLS number |
| 5 | LO roster | Text or link | Names + NMLS or link to a sub-sheet |
| 6 | Markets | Text | Cities and states |
| 7 | Languages | Text | Spoken / published languages |
| 8 | Intake date | Date | Date intake submitted |
| 9 | Wave | Dropdown | Wave 1 / Wave 2 / Wave 3 / Queued |
| 10 | Status | Dropdown | New / Reviewing / Approved / Implementing / Active / On hold / Declined |
| 11 | Marketing kit status | Dropdown | Not started / In progress / Delivered |
| 12 | TERA setup status | Dropdown | Not started / Ally in progress / Portal in progress / Email Drip in progress / GBP in progress / All wired |
| 13 | Compliance status | Dropdown | Not reviewed / Template-approved / Pending review / Flagged / Cleared |
| 14 | GBP status | Dropdown | Not started / Claim requested / Verified / Live |
| 15 | Ally status | Dropdown | Not started / Workflow built / Publishing |
| 16 | Newsletter status | Dropdown | Not started / Template loaded / First send sent |
| 17 | Email Drip status | Dropdown | Not started / Sequence loaded / Active |
| 18 | First post date | Date | First GBP or social post date |
| 19 | First newsletter date | Date | Date of first newsletter send |
| 20 | First Realtor outreach date | Date | Date of first Realtor outreach |
| 21 | Pilot Leader meeting attendance | Text | Date list of attended meetings |
| 22 | Application growth attribution | Text or number | Apps attributed to team brand (post Day 30) |
| 23 | Recruiting activity | Text | LOs added or in conversation |
| 24 | Notes | Long text | Free-form |
| 25 | Blockers | Long text | What is stopping progress |
| 26 | Last updated | Date | Auto-stamped via Apps Script if possible, otherwise manual |
| 27 | Owner of next action | Text | Who needs to do the next thing |

## Supporting tabs in the same workbook

- **Tab 1: Teams (main).** The 27 columns above.
- **Tab 2: Intake log.** Raw export of Google Form submissions, untouched. Source of truth for "what was submitted."
- **Tab 3: Compliance log.** Per-team compliance review history. Date, reviewer, template or piece, outcome.
- **Tab 4: Friction log.** Surfaced at every bi-weekly Pilot Team Leader meeting. Item, surfaced by, status, fix owner, fix date.
- **Tab 5: Cadence heat map.** Conditional-formatted view of who is publishing on cadence. Green / yellow / red per channel per team per week.
- **Tab 6: Wave assignment log.** Decisions about which team moves to which wave, with date and reason.

## What we monitor (the seven non-optional areas)

Pulled directly from the May 14 meeting direction.

1. Posting activity (columns 15, 18 and Cadence heat map)
2. Newsletter activity (columns 16, 19)
3. Campaign activity (columns 17, 20)
4. Team Leader participation (column 21)
5. Application growth (column 22)
6. Recruiting activity (column 23)
7. Compliance review status (columns 13, Tab 3)

## Update rules

- Anyone with edit access can update their pod's columns.
- Jeremy owns columns 1 through 10, 24, 25, 26, 27.
- Marketing owns column 11.
- TERA owns columns 12, 14, 15, 16, 17.
- Compliance owns column 13.
- Team Leaders report columns 18, 19, 20, 23 via the Pilot Leader meeting or async update form.
- Notes and blockers are open to anyone.

## What this is NOT

- Not a dashboard build.
- Not a custom app.
- Not a TERA-managed system. (TERA may absorb this later, but for now it is Jeremy + Tara owned.)
- Not real-time. Weekly update minimum, daily during launch week.
- Not a substitute for the bi-weekly Pilot Team Leader meeting.

## Phase 2 path

After August 30, if the pilot proves we need real-time reporting, this becomes the spec for a TERA-aligned dashboard build. Until then, sheets are enough.

## Cross-references

- `PROJECT_DECISIONS_AND_CONTEXT.md` D24
- `NEXT_ACTIONS_QUEUE.md` A18
- `FORMS_AND_ONBOARDING/team_leader_intake_form_fields.md`
- `TERA_AND_TECH_REQUIREMENTS/tera_stack_alignment_questions.md`
