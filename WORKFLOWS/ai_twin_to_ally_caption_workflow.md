# AI Twin to ALLY Caption Workflow

**Purpose:** Define how AI Twin Persona Intake becomes an approved LO Persona Profile, gets mapped to Loan Factory SSO, and is referenced by ALLY's "Enhance Caption with AI" feature so generated captions sound like the actual loan officer.
**Owner:** Jeremy McDonald (operational), LO Development (intake review), Marketing (voice review), TERA (technical wiring), Compliance (template-level guardrails)
**Last updated:** 2026-05-18
**Status:** Direction documented, implementation pending TERA discovery answers (`lo_persona_profile_ally_integration_requirements.md`)

## Framing

ALLY is the social and campaign execution layer. This workflow describes how persona data flows **into** ALLY at caption time without making ALLY the owner of persona. Persona is one shared identity layer. ALLY is one consumer.

## Trigger

LO completes the AI Twin Persona Intake form (existing form with 119 responses already collected).

## End state

When the LO clicks "Enhance Caption with AI" inside ALLY, ALLY generates a caption that:

1. Uses the selected post template
2. Reflects the LO's approved persona (tone, voice, word lists, audience focus)
3. Uses the LO's selected language if applicable
4. Carries Loan Factory compliance guardrails (template-level)
5. Includes the required LO and Loan Factory NMLS information
6. Is presented to the LO for review before any publishing

Human review and compliance rules still apply. No autopublish.

## Primary workflow

```
LO completes AI Twin Persona Intake
            ↓
LO Dev or Marketing reviews the intake
            ↓
System creates or updates the approved LO Persona Profile
            ↓
Profile mapped to the LO's Loan Factory SSO identity
            ↓
LO opens ALLY → selects a post template → clicks "Enhance Caption with AI"
            ↓
ALLY reads or references the approved LO Persona Profile via SSO claim
            ↓
ALLY generates a caption using:
   - the selected post template
   - the loan officer's persona
   - the selected language if applicable
   - Loan Factory compliance guardrails (template-level)
   - required LO and Loan Factory NMLS information
            ↓
LO reviews the generated caption
            ↓
LO edits or accepts, schedules or publishes inside ALLY
            ↓
Activity logged in launch tracking and any TERA reporting surface
```

## Steps

### Step 1 — Intake submitted

- **Owner:** LO
- **Input:** AI Twin Persona Intake form (existing, 119 responses)
- **Output:** Raw intake response stored in the source-of-record (TBD with TERA)
- **Time:** Minutes
- **Tools:** Existing AI Twin Persona Intake form

### Step 2 — Intake review

- **Owner:** LO Development (primary) + Marketing (voice review)
- **Input:** Raw intake response
- **Output:** Approved, requested-changes, or held with reason
- **Time:** 3 to 5 business days
- **Tools:** Source-of-record (TBD), review checklist

Reviewers check that the intake is complete, the voice description is usable, the word lists are reasonable, and that nothing in the intake belongs in a CRM or LOS rather than a persona profile. Compliance flags (if any) get noted but do not block voice approval.

### Step 3 — Approved LO Persona Profile created or updated

- **Owner:** LO Development (operational), TERA (technical)
- **Input:** Approved intake
- **Output:** A row in the LO Persona Profile store (schema in `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`) with review status set to Approved
- **Time:** Same day after review approval
- **Tools:** Persona store (Phase 1: shared Google Sheet or interim store; Phase 2: TERA-backed persona service per `lo_persona_profile_ally_integration_requirements.md`)

### Step 4 — SSO identity mapping

- **Owner:** TERA
- **Input:** Approved profile + LO's Loan Factory SSO identity
- **Output:** Profile keyed off the SSO subject claim so any system that authenticates the LO can fetch their profile
- **Time:** Once configured, automatic per LO
- **Tools:** Loan Factory SSO + TERA persona service

If SSO mapping is not yet wired, the workflow falls back to the alternate workflow below.

### Step 5 — ALLY caption request

- **Owner:** LO inside ALLY
- **Input:** Selected post template, optional language selection, optional content topic
- **Output:** Caption request fired to ALLY's caption service with the LO's SSO context
- **Time:** Seconds
- **Tools:** ALLY (React frontend, Python backend, GKE)

### Step 6 — ALLY pulls persona context

- **Owner:** ALLY caption service
- **Input:** SSO claim from the authenticated LO
- **Output:** Persona profile fetched from the persona store
- **Time:** Sub-second
- **Tools:** ALLY backend + persona service or persona table

Only the fields needed for caption generation are fetched. NPI and other restricted fields are not stored anywhere on the persona profile, so there is nothing sensitive to leak.

### Step 7 — Caption generated

- **Owner:** ALLY caption service
- **Input:** Template + persona + language + compliance template metadata + required NMLS information
- **Output:** Draft caption presented to the LO
- **Time:** Sub-second to a few seconds depending on model
- **Tools:** ALLY backend + the AI provider ALLY uses (per P12 in the requirements doc)

Compliance guardrails are layered separately. Persona influences tone and word choice. Compliance enforces structure, disclosures, and prohibited phrasing.

### Step 8 — LO review

- **Owner:** LO
- **Input:** Generated caption
- **Output:** Approved (proceed), edited (proceed with edits), or rejected (regenerate or skip)
- **Time:** Minutes
- **Tools:** ALLY

### Step 9 — Publish or schedule

- **Owner:** LO (or Team Leader if approval gates are in place)
- **Input:** Approved caption
- **Output:** Caption scheduled or published per the team's cadence
- **Tools:** ALLY

### Step 10 — Activity logged

- **Owner:** ALLY + TERA reporting
- **Input:** Publish event
- **Output:** Activity flows into the launch tracking sheet (Wave 1) and any unified Marketing + TERA dashboard (Phase 2)
- **Tools:** ALLY + Google Sheets (Wave 1) + dashboard (Phase 2)

## Alternate workflow — manual persona upload

If persona data cannot be pulled automatically yet (P3 or P4 still open), use a manual fallback:

```
LO completes AI Twin Persona Intake
            ↓
LO Dev or Marketing reviews and approves
            ↓
Approved persona document produced (PDF or Google Doc)
            ↓
LO logs into ALLY → opens profile settings → persona section
            ↓
LO uploads or pastes their approved persona document into ALLY
            ↓
When LO clicks "Enhance Caption with AI", ALLY uses the persona document
content the LO loaded into their own ALLY profile
            ↓
Same review and compliance steps as the primary workflow
```

This fallback unblocks ALLY caption personalization while TERA finalizes the SSO-mapped persona service. It also gives LOs a path to keep their persona current without a full SSO round-trip if review windows are slow.

## Phasing

| Layer | Wave 1 (June 1) | Phase 2 (post-August 30) |
| --- | --- | --- |
| Intake | Existing AI Twin Persona Intake form (Google Form) | Form posts into TERA-backed persona service |
| Review | LO Dev + Marketing review by hand | Same model, reviewed inside TERA review UI |
| Persona store | Interim store (Sheet or doc) | TERA-backed persona service, SSO-keyed |
| ALLY ingestion | Manual upload via ALLY profile settings | SSO-mapped automatic fetch |
| Compliance guardrails | Template-level review (no change) | Template-level review (no change) |
| Reporting | Google Sheets | Unified dashboard |

Nothing in Phase 2 ships until the questions in `lo_persona_profile_ally_integration_requirements.md` are answered.

## End-to-end timeline (per LO)

| Day | Step |
| --- | --- |
| Day 0 | LO submits intake |
| Day 0 to 5 | Review |
| Day 5 to 7 | Approved persona profile created or updated |
| Day 7 onward | ALLY caption generation references the approved persona |

## SLAs

| Stage | SLA |
| --- | --- |
| Intake review | 5 business days |
| Profile creation after approval | Same day |
| ALLY caption response | Sub-second to a few seconds |
| LO review of caption | LO's discretion; no SLA |
| Manual upload alternate path | LO can upload anytime once their approved persona document is delivered |

## Failure modes

| Failure | Symptom | Response |
| --- | --- | --- |
| Persona profile not found | Caption falls back to generic template-only output | Log it, surface a banner to the LO suggesting they complete the intake |
| Persona contains restricted data | Caught at review time | Reviewer strips the field, persona is not approved until clean |
| SSO mapping fails | Caption service cannot identify the LO's profile | Fallback to manual upload path |
| Compliance guardrail conflict | A required disclosure is missing | Caption is rejected by the compliance layer before reaching the LO for review |
| Persona too broad or contradictory | Captions sound off | LO Dev edits the persona, version bumps, ALLY picks up the new version on next call |

## Escalation path

- Persona review backlog → LO Dev lead → Marketing pod lead → Tara
- ALLY caption integration issue → Thanh + Dat via Tara
- Compliance conflict → Compliance lead
- Privacy concern → Compliance + TERA leadership

## Related workflows

- `WORKFLOWS/team_marketing_system_sync_workflow.md`
- `WORKFLOWS/compliance_review_template_level.md` (when written)

## Cross-references

- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md` D8, D9, D27, D31, D32, D33, D34
- `NEXT_ACTIONS_QUEUE.md`
