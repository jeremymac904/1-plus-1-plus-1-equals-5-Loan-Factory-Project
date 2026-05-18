# Team Marketing System Sync Workflow

**Purpose:** Define how a single Team Leader intake submission flows into one master team marketing record that drives every downstream system (ALLY, website, newsletters, drips, GBP, realtor outreach, compliance, marketing production, TERA setup, reporting).
**Owner:** Jeremy McDonald (operational), Marketing pod (production), TERA pod (technical), Compliance (template review)
**Last updated:** 2026-05-18
**Status:** Direction documented, implementation phased (manual June 1, semi-automated post-pilot)

## Why this workflow exists

For June 1, every team gets stood up by hand. That works for Wave 1 but does not scale. This doc describes the **target sync direction** so each manual step we run today is already pointing at the automated state we want later. ALLY is the social and campaign execution layer inside this flow, not the whole flow.

## Trigger

Team Leader (or LO acting on behalf of a forming team) submits the Google Form intake at `FORMS_AND_ONBOARDING/team_leader_intake_form_fields.md`.

## End state

A team is operating with:

1. A master team marketing record (single source of truth)
2. Website team page and LO landing pages live and on-brand
3. Newsletter audience configured in the Loan Factory portal
4. Email Drip sequence configured in the portal
5. ALLY configured with team channels, content templates, and scheduling cadence
6. Google Business Profile claimed and templated
7. Realtor outreach templates loaded
8. Compliance template review complete and disclosures locked in
9. Reporting visible in the launch tracking sheet (and later, the Marketing + TERA dashboard)

## The master team marketing record

The intake form becomes the master record. The master record is the single source of truth that every downstream system reads from. See `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md` for field-by-field mapping.

For Wave 1: master record lives in the `1+1+1=5 Intake Submissions` Google Sheet, Tab 1 (Teams).
For Phase 2: master record gets a defined home with TERA (DB-backed) once the ALLY and portal integration questions are answered.

## End-to-end flow

```
Team Leader → Google Form intake
            ↓
Jeremy + Marketing review (24–48h SLA)
            ↓
Master team marketing record created
            ↓
   ┌────────────────────┬───────────────────┬─────────────────────┐
   ↓                    ↓                   ↓                     ↓
Branding kit       TERA technical      Marketing            Compliance
assembled          setup queue         production           template review
(Marketing pod)    (TERA pod)          workflow              (Compliance)
   ↓                    ↓                   ↓                     ↓
   │              Website team page    Newsletter audience   Disclosure
   │              + LO pages           + Email Drip          locks confirmed
   │              ALLY team setup      sequence
   │              GBP claim or wire    
   │              Realtor outreach
   │              templates loaded
   ↓                    ↓                   ↓                     ↓
            Team Leader kickoff + first 30-day support plan
                                ↓
                Reporting and tracking dashboards updated
                                ↓
                Bi-weekly Pilot Team Leader meeting feedback loop
```

## Steps

### Step 1 — Intake submitted

- **Owner:** Team Leader
- **Input:** Completed Google Form
- **Output:** Row added to `1+1+1=5 Intake Submissions` Google Sheet
- **Time:** Minutes
- **Tools:** Google Forms, Google Sheets

### Step 2 — Intake review

- **Owner:** Jeremy + Marketing pod lead
- **Input:** Intake row
- **Output:** Approved master record, wave assignment, or rejection with reason
- **Time:** 24 to 48 hours
- **Tools:** Google Sheets, email

Reviewers check minimum LO count, multi-city or state coverage, division alignment, and acknowledgments. Approved rows get promoted into Tab 1 (Teams) of the launch tracking workbook with a wave number.

### Step 3 — Master team marketing record created

- **Owner:** Jeremy
- **Input:** Approved intake row
- **Output:** Master record row with team identifier, division, languages, markets, niche, LO roster, channel commitments, cadence, brand preferences, compliance acknowledgments
- **Time:** Same day
- **Tools:** Google Sheets (Wave 1), TERA-backed system (Phase 2)

See `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md` for the master record schema.

### Step 4 — Branding kit assembled

- **Owner:** Marketing pod
- **Input:** Master record (team name, division, languages, niche, brand preferences)
- **Output:** Team kit v1 — logo lockups, color palette, typography, tagline, division variant if applicable
- **Time:** 3 to 5 business days
- **Tools:** Canva Pro, Drive, `MARKETING_SYSTEMS/`

The same kit drives website, newsletter, drip, ALLY, GBP, realtor outreach. See `MARKETING_SYSTEMS/brand_sync_requirements.md`.

### Step 5 — TERA technical setup queue

- **Owner:** TERA pod
- **Input:** Master record + team kit
- **Output:**
  - Website team page live with branding
  - LO landing pages live where applicable
  - Newsletter audience configured in the Loan Factory portal
  - Email Drip sequence configured in the portal
  - ALLY team account configured with channels, templates, cadence
  - GBP claim verified or wired
  - Realtor outreach template list loaded into the team's tool stack
- **Time:** 5 to 10 business days, parallelized
- **Tools:** Loan Factory portal, ALLY, GBP, website CMS, internal TERA scripts

ALLY work in this step is the social and campaign execution slice. The rest of the stack is just as important and runs in parallel.

### Step 6 — Compliance template review

- **Owner:** Compliance lead (with Marketing)
- **Input:** All team-facing templates produced in Steps 4 and 5
- **Output:** Approved template set with required disclosures baked in (NMLS, EHL, state-specific, trigger term, $2,000 Best Price Guarantee where applicable)
- **Time:** 3 to 5 business days, runs alongside Step 5
- **Tools:** Marketing kit folder, Compliance review checklist

Per D9, compliance reviews templates, not individual pieces. Once templates are locked, individual pieces produced from them do not need re-review unless the template is materially edited.

### Step 7 — Marketing production workflow loaded

- **Owner:** Marketing pod
- **Input:** Approved templates + team kit + master record
- **Output:** Initial content batch drafted (week 1 social, first newsletter, drip emails, first GBP posts, first realtor outreach), AI-drafted using Gemini and NotebookLM, queued for Team Leader review
- **Time:** 3 to 5 business days
- **Tools:** Gemini, NotebookLM, ALLY drafts, Loan Factory portal drafts, Drive

### Step 8 — Team Leader kickoff

- **Owner:** Jeremy
- **Input:** Configured team across all surfaces, drafted content queue
- **Output:** Team Leader trained on the workflow, knows where to review and approve, has a named Marketing rep and TERA rep, understands the bi-weekly Pilot Team Leader meeting cadence
- **Time:** 1 hour kickoff call + async follow-up
- **Tools:** Zoom, Drive, email

### Step 9 — First-30-day support plan activates

- **Owner:** Marketing pod (active support), Team Leader (execution)
- **Input:** Drafted content queue, approval workflow
- **Output:** Team is publishing on schedule across each committed channel. Friction surfaced inside the bi-weekly Pilot Team Leader meeting.
- **Time:** 30 days
- **Tools:** ALLY, Loan Factory portal, GBP, website, realtor outreach

### Step 10 — Reporting and tracking activates

- **Owner:** Marketing + TERA (joint)
- **Input:** Activity from each surface
- **Output:** Launch tracking sheet shows team status, kit status, TERA status, compliance status, channel activity, cadence adherence, Pilot Leader meeting attendance
- **Time:** Ongoing
- **Tools:** Google Sheets (Wave 1), Marketing + TERA dashboard (Phase 2)

## End-to-end timeline

| Day | Step |
| --- | --- |
| Day 0 | Intake submitted |
| Day 1–2 | Intake review, master record created |
| Day 2–7 | Branding kit assembled |
| Day 3–12 | TERA technical setup runs in parallel across website, newsletter, drip, ALLY, GBP, realtor outreach |
| Day 5–10 | Compliance template review |
| Day 8–12 | Marketing production workflow loaded with first content batch |
| Day 10–14 | Team Leader kickoff |
| Day 14+ | First 30-day support plan active, publishing live |

Wave 1 target: form to live in 14 days. Tightening to 7 to 10 days is a Phase 2 goal.

## Sync responsibilities by surface

| Downstream surface | Owner | Reads from master record | ALLY involvement |
| --- | --- | --- | --- |
| Website team page | TERA + Marketing | Team name, brand kit, market, languages, LO roster | None |
| LO landing pages | TERA + Marketing | LO roster, individual bio inputs, brand kit | None |
| Newsletter audience | TERA + Marketing | Languages, markets, niche, brand kit | None |
| Email Drip sequence | TERA + Marketing | Niche, division, languages, brand kit | None |
| ALLY team setup | TERA + Marketing | Channels committed, cadence, brand kit, languages | This is ALLY's home turf |
| GBP workflow | TERA + Marketing | Markets, brand kit, languages | None |
| Realtor outreach | Marketing + Team Leader | Markets, partner relationships, languages | None |
| Compliance review | Compliance | Languages, niche, disclosures required | Template-level review applies inside ALLY too |
| Marketing production | Marketing | All of the above | ALLY drafts get produced here too |
| TERA setup | TERA | All technical fields | ALLY config is one TERA task among several |
| Reporting | Marketing + TERA | Activity from every surface | ALLY activity is one input, not the only input |

## Failure modes

| Failure | Symptom | Response |
| --- | --- | --- |
| Intake row never reviewed | Submission sits past 48 hours | Jeremy escalates in Pilot Leader meeting and reminds Marketing |
| ALLY config blocked on auth | Cannot connect a channel | Marketing flags TERA, TERA contacts vendor support, Team Leader notified of expected delay |
| Branding drift between surfaces | Newsletter looks different from ALLY posts | Marketing reissues team kit, redeploys templates, logs the drift in launch tracking |
| Compliance template gap | A surface ships without a required disclosure | Compliance freezes the template, Marketing patches, all teams using the template get notified |
| Master record edits not propagated | Team renames itself, ALLY still uses old name | Edit master record, Jeremy runs propagation checklist across every surface listed above |
| Reporting roll-up incomplete | A surface's activity is missing from the launch tracking sheet | Surface owner files a TERA ticket, Jeremy flags in Pilot Leader meeting |

## SLAs

| Stage | SLA |
| --- | --- |
| Intake review | 24 to 48 hours |
| Branding kit | 5 business days |
| TERA setup across all surfaces | 10 business days |
| Compliance template review | 5 business days |
| First content batch ready | 5 business days from kit approval |
| Team Leader kickoff scheduled | Within 3 business days of all setup complete |

## Escalation path

- ALLY-specific issue → Marketing pod lead → TERA pod lead → Tara
- Compliance issue → Compliance lead → Tara
- Cross-surface drift → Jeremy → next Pilot Leader meeting
- Capacity issue (Marketing or TERA) → Tara → Andre or Thuan if material

## Phasing — what is manual now vs automated later

| Layer | Wave 1 (June 1) | Phase 2 (post-August 30) |
| --- | --- | --- |
| Intake | Google Form → Sheet | Form posts directly into TERA-backed master record |
| Master record | Google Sheet Tab 1 | TERA-backed DB |
| Branding kit | Marketing produces by hand | Templated generator with brand kit auto-applied |
| TERA setup | Manual per surface | TERA runbook with scripted steps where possible |
| ALLY config | Manual | Driven from master record via ALLY API or sync job (pending discovery) |
| Compliance | Template-level manual review | Same model, with template versioning |
| Reporting | Google Sheets | Unified Marketing + TERA dashboard |

Nothing in Phase 2 ships without the answers from `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md` and `tera_stack_alignment_questions.md`.

## Related workflows

- `WORKFLOWS/team_leader_onboarding.md` (when written)
- `WORKFLOWS/compliance_review_template_level.md` (when written)
- `WORKFLOWS/pilot_leader_meeting_run_of_show.md` (when written)

## Cross-references

- `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md`
- `MARKETING_SYSTEMS/brand_sync_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/tera_stack_alignment_questions.md`
- `REPORTING_AND_TRACKING/google_sheets_launch_tracking_framework.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md` D6, D7, D8, D9, D15, D17, D24, D25
- `NEXT_ACTIONS_QUEUE.md`
