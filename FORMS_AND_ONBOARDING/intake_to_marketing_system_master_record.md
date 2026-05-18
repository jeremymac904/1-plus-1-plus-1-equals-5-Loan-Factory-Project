# Intake to Marketing System Master Record

**Owner:** Jeremy McDonald (operational), Marketing pod lead (review), TERA pod lead (technical home)
**Status:** Direction documented, Wave 1 implementation in Google Sheets
**Last updated:** 2026-05-18
**Purpose:** Define the master team marketing record that is produced from the Google Form intake and that every downstream system reads from. Single source of truth so the team's brand, channels, languages, niche, and commitments stay aligned across website, newsletter, drip, ALLY, GBP, realtor outreach, compliance, and reporting.

## Why this exists

The intake form captures everything a team needs to launch. Today that data lives in a Google Sheet row. Tomorrow it needs to live in a system that every downstream surface can read from. Either way, the **same field-set drives every system**. This doc names those fields, defines who reads them, and locks the master record schema so we stop re-entering the same data five times.

## Master record schema

Each row in the master record represents one team. Field names are stable. Field values are sourced from the intake form (see `FORMS_AND_ONBOARDING/team_leader_intake_form_fields.md`).

### Identity

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Team ID | Auto, assigned at promotion to Tab 1 | All systems |
| Team name | Q7 | Website, newsletter, drip, ALLY, GBP, realtor outreach, compliance, reporting |
| Team type | Q8 (Existing vs New) | Reporting, onboarding workflow |
| Wave number | Assigned at review | Reporting, onboarding workflow |
| Division umbrella | Q9 | Branding, marketing production, reporting |
| Custom division detail | Q10 | Branding, marketing production |
| Date promoted to master | Auto | Reporting |

### Roster

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Team Leader name | Q1 | All systems |
| Team Leader NMLS | Q2 | All systems (compliance disclosures) |
| Team Leader email | Q3 | Notifications, kickoff scheduling |
| Team Leader phone | Q4 | Notifications |
| Primary city and state | Q5 | Website, GBP, realtor outreach |
| Role at intake | Q6 | Onboarding workflow |
| LO count committed | Q11 | Capacity planning, reporting |
| Multi-city or state coverage | Q12 | Eligibility check |
| LO roster (names + NMLS) | Q13 | Website LO pages, ALLY user provisioning, compliance, reporting |

### Markets and languages

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Operating languages | Q14 | Branding, newsletter, drip, ALLY content variants, GBP, realtor outreach, compliance |
| Markets covered | Q15 | Website, GBP, realtor outreach, reporting |

### Niche and partner relationships

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Niche or audience anchor | Derived from Q9 + Q10 + Q23 | Branding, drip sequencing, content production |
| Partner relationships | Q16 | Realtor outreach, marketing production |
| Existing marketing activities | Q17 | Marketing production, gap analysis |

### Channels and cadence

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Channels committed | Q18 | ALLY config, content production, reporting |
| Cadence commitment | Q19 | ALLY scheduling, drip scheduling, GBP scheduling, reporting |

### Brand preferences

Brand preferences are partially captured at intake and completed during the Marketing kit kickoff. The master record stores both stages so the team kit, website, newsletter, drip, ALLY, GBP, and realtor outreach all read the same values.

| Field | Source | Reads it |
| --- | --- | --- |
| Brand origin | Q8 (existing brand vs new) + kit kickoff | Branding |
| Logo lockup link | Marketing kit | Website, newsletter, drip, ALLY, GBP, realtor outreach |
| Color palette | Marketing kit | All surfaces |
| Typography | Marketing kit | All surfaces |
| Tagline | Marketing kit | All surfaces |
| Division brand variant | Marketing kit (if applicable) | All surfaces |
| Photography or imagery direction | Marketing kit | All surfaces |

### Compliance posture

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Required disclosures (NMLS, EHL, state-specific, trigger term, $2,000 Best Price Guarantee) | Derived from Q14, Q15, Q23, Q25 | Compliance review, every published surface |
| Acknowledgment of human review | Q24 | Compliance |
| Acknowledgment of Loan Factory marketing policy | Q25 | Compliance |
| Acknowledgment of capacity-based waves | Q26 | Onboarding |
| Acknowledgment of bi-weekly Pilot Leader meeting | Q27 | Onboarding, reporting |

### Why and need

| Field | Source (intake) | Reads it |
| --- | --- | --- |
| Reason for joining | Q20 | Marketing production, Pilot Leader prep |
| Top marketing bottleneck | Q21 | First-30-day support plan |
| Requested support from Marketing and TERA | Q22 | First-30-day support plan |
| Anything else | Q23 | Marketing production, Pilot Leader prep |

### Operational

| Field | Source | Reads it |
| --- | --- | --- |
| Kickoff call window | Q28 | Onboarding |
| Signature | Q29 | Audit |
| Submitted date | Q30 | Reporting |
| Status (Intake → Reviewed → Approved → In Setup → Live → On Hold → Closed) | Manual | Reporting, escalation |
| Wave assignment | Manual | Reporting, onboarding |
| Marketing rep assigned | Manual | First-30-day support plan |
| TERA rep assigned | Manual | First-30-day support plan |
| Compliance reviewer assigned | Manual | Compliance |

## Who reads from the master record

| System | Reads | Notes |
| --- | --- | --- |
| ALLY social setup | Team name, LO roster, channels, cadence, languages, brand kit | Per `ally_stack_and_integration_requirements.md` |
| Loan Factory website team pages | Team name, market, languages, LO roster, brand kit | Driven by TERA |
| Loan Factory portal newsletters | Languages, markets, niche, brand kit, audience scoping | Driven by TERA |
| Loan Factory portal Email Drip | Niche, division, languages, brand kit | Driven by TERA |
| Google Business Profile workflows | Markets, brand kit, languages | Driven by TERA + Marketing |
| Realtor outreach | Markets, partner relationships, languages, brand kit | Driven by Marketing |
| Compliance review templates | Languages, niche, required disclosures | Driven by Compliance |
| Marketing production workflow | Everything | Marketing reads it all |
| TERA technical setup | All technical fields | TERA reads it all |
| Reporting and tracking | Status, wave, activity per surface | Marketing + TERA joint |

If a system needs a field that is not on the master record, it gets added here first. No shadow data stores.

## Implementation by phase

### Wave 1 (June 1)

- Google Form posts to `1+1+1=5 Intake Submissions` Google Sheet
- Tab 1 (Teams) is the master record
- Tab 2 (Intake log) is the raw inbound feed
- Jeremy promotes approved rows from Tab 2 to Tab 1
- Each downstream surface reads from Tab 1 by reference (paste links, copy fields, manual sync)
- Marketing kit fields get filled in during kit kickoff

### Phase 2 (post-August 30)

- Master record migrates to TERA-backed storage (DB to be confirmed in `tera_stack_alignment_questions.md`)
- Intake form posts directly into the master record
- Downstream surfaces read via API or scheduled sync
- ALLY pull pattern defined once `ally_stack_and_integration_requirements.md` is closed out
- Reporting dashboard reads the master record + activity logs

## Update rules

1. **Intake fields are immutable.** Original intake values stay as submitted. Corrections get a separate "correction" field with date and note.
2. **Operational fields are editable.** Status, wave, assigned reps, kickoff window, etc.
3. **Brand kit fields are versioned.** Each new kit version gets a version number and date.
4. **Any change to the master record triggers a propagation check.** Jeremy runs the propagation checklist in `WORKFLOWS/team_marketing_system_sync_workflow.md`.

## Open questions

| # | Question | Owner | Target |
| --- | --- | --- | --- |
| MR1 | Confirm Tab 1 column ordering with Marketing before June 1 | Jeremy + Marketing | May 27 |
| MR2 | Confirm whether TERA has a preferred DB for the Phase 2 master record | TERA via Tara | May 27 |
| MR3 | Confirm whether intake should route directly into a TERA system in Phase 2 or stay form-driven | TERA + Marketing | June 30 |
| MR4 | Confirm whether ALLY can pull team setup from the master record via API | TERA + ALLY | July 15 |
| MR5 | Confirm whether the portal can pull newsletter audience and drip configuration from the master record | TERA | July 15 |

## Cross-references

- `FORMS_AND_ONBOARDING/team_leader_intake_form_fields.md` — source fields
- `WORKFLOWS/team_marketing_system_sync_workflow.md` — how the master record drives the sync
- `MARKETING_SYSTEMS/brand_sync_requirements.md` — branding consistency
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md` — ALLY integration questions
- `TERA_AND_TECH_REQUIREMENTS/tera_stack_alignment_questions.md` — TERA stack questions
- `REPORTING_AND_TRACKING/google_sheets_launch_tracking_framework.md` — Wave 1 workbook
- `PROJECT_DECISIONS_AND_CONTEXT.md` D15, D24, D25
