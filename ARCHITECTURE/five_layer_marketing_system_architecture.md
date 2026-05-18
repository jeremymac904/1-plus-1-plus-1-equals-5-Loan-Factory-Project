# Five-Layer Marketing System Architecture

**Owner:** Jeremy McDonald (operational), TERA (technical surfaces), Marketing (production), Compliance (template-level guardrails)
**Status:** Architecture documented; June 1 Wave 1 implementation is manual end to end
**Last updated:** 2026-05-18
**Purpose:** Define the five-layer architecture for the 1+1+1=5 language-group marketing program. The program is one program with five connected layers. ALLY is one execution layer, not the whole system.

## The five layers

```
┌─────────────────────────────────────────────────────────────┐
│ Layer 1 — Intake and approval                                │
│ Google Forms, Marketing review, Compliance review            │
└───────────────────────────────┬─────────────────────────────┘
                                 ↓
┌─────────────────────────────────────────────────────────────┐
│ Layer 2 — Master group record (single source of truth)       │
│ Google Sheets (Wave 1) → Airtable (interim) → TERA (Phase 2) │
└───────────────────────────────┬─────────────────────────────┘
                                 ↓
┌─────────────────────────────────────────────────────────────┐
│ Layer 3 — Brand and content kit                              │
│ Logo, palette, typography, tagline, templates, disclosures   │
└───────────────────────────────┬─────────────────────────────┘
                                 ↓
┌─────────────────────────────────────────────────────────────┐
│ Layer 4 — Channel execution                                  │
│ ALLY (social)    Newsletter   Email Drip   Website / LO page │
│ Google Business Profile      YouTube (where supported)       │
└───────────────────────────────┬─────────────────────────────┘
                                 ↓
┌─────────────────────────────────────────────────────────────┐
│ Layer 5 — Tracking, reporting, governance                    │
│ Activity logs, KPI rollups, compliance posture, retros       │
└─────────────────────────────────────────────────────────────┘
```

## Layer 1 — Intake and approval

**Purpose:** Capture group, LO, and persona data and route it through Marketing review and Compliance review before activation.

- **Inputs:** Google Form intake (Team Leader Interest, LO Team Interest, Team Branding Intake, AI Twin Persona Intake)
- **Steps:** Submission → notification → review (24 to 48 hours) → request changes, hold, or approve
- **Outputs:** Approved intake row promoted to the master group record; persona intake routed to persona review
- **Owners:** Jeremy (operational), Marketing pod lead (brand and voice), LO Development (persona), Compliance (gate)
- **Wave 1 reality:** Manual review; notification by Apps Script email; approvals captured in writing in the launch tracking sheet

## Layer 2 — Master group record

**Purpose:** One source of truth per language group, read by every downstream channel.

- **Schema:** identity, brand package, leadership, roster, channel configuration, compliance, tracking (see `STRATEGY/ai_boardroom_architecture_readout_summary.md` and `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md`)
- **Wave 1 home:** Tab 1 (Teams) of `1+1+1=5 Intake Submissions` Google Sheet
- **Phase 2 home:** Airtable (interim, 30 to 90 days), then TERA-backed once stack alignment confirms a group/team data model
- **Update rule:** Intake fields are immutable; operational fields are editable; brand-kit fields are versioned; every edit triggers a propagation check across channels

## Layer 3 — Brand and content kit

**Purpose:** Lock the visual identity, voice, structure, and disclosure language each channel inherits.

- **Components:** logo lockup set, color palette, typography, tagline, division or language variant, photography direction, voice and tone guidelines, content structure per format, required disclosures baked into every template
- **Approver:** Marketing (production), Compliance (template-level review per D9)
- **Versioning:** team_kit_v1, team_kit_v2, etc., with version bumps applied across every channel in one pass
- **Drift response:** kit reissue and full redeploy across surfaces (per `MARKETING_SYSTEMS/brand_sync_requirements.md`)

## Layer 4 — Channel execution

**Purpose:** Publish in the group's brand, on the group's cadence, with the right disclosures, on every surface the group commits to.

| Channel | Owner | Reads from master record | Notes |
| --- | --- | --- | --- |
| ALLY (social publishing and AI captioning) | TERA + Marketing + Team Leader | group_id, ALLY group config, brand kit, LO roster, channels committed, language preferences, persona reference | Confirmed stack: React, Python, PostgreSQL, Loan Factory SSO, GKE; "Enhance Caption with AI" feature today |
| Email newsletter | Marketing + TERA | group_id, brand kit, email_list_id, language, audience | Platform owner TBD |
| Email drip campaign | Marketing + TERA | group_id, brand kit, drip_sequence_id, niche, language | Platform owner TBD |
| Website team page / LO landing page | TERA + Marketing | group_id, brand kit, LO roster, languages, markets, programs | CMS owner TBD |
| Google Business Profile | Marketing + Team Leader | group_id, markets, brand kit, languages | Per-market posts |
| YouTube (where teams opt in) | Marketing + Team Leader | group_id, brand kit, language preference, content topics | Optional channel; long-form and Shorts |

All channels reference the master group record. Channels do not own program data. The compliance guardrail layer applies on every channel.

## Layer 5 — Tracking, reporting, governance

**Purpose:** Surface activity, performance, compliance posture, and friction so the program team can iterate.

- **Wave 1:** Google Sheets launch tracking framework (team status, kit status, TERA status, compliance status, channel activity, cadence adherence, Pilot Leader meeting attendance), ALLY native analytics, manual weekly rollup
- **Phase 2:** Unified Marketing + TERA dashboard reading from the master record and channel activity logs
- **Governance:** Bi-weekly Pilot Team Leader meeting (chaired by Jeremy), 30/60/90-day reviews, AI Governance posture for any persona or AI-twin work per the broader strategic plan

## Layer interactions

- Layer 1 produces approved data only. No raw intake reaches Layer 4.
- Layer 2 is the only system that downstream channels read for group state. Channel-specific configuration (ALLY group ID, email list ID, drip ID, landing page URL, GBP URL) is captured here.
- Layer 3 templates are produced once per group and re-used across channels. Compliance reviews templates, not pieces.
- Layer 4 channels execute in parallel. Drift between channels is detected at the Pilot Leader meeting and at the weekly Marketing rep check-in.
- Layer 5 reports activity from each channel back to the program, and feeds the iteration queue.

## What is in scope by June 1

- Layer 1 manual review and routing
- Layer 2 schema in Google Sheets, populated for the first language group
- Layer 3 team kit v1 with compliance-approved templates
- Layer 4 ALLY configured for the first group's point person and ready members, with a 30-day content calendar loaded and scheduled
- Layer 4 one staged newsletter template
- Layer 5 weekly manual rollup

## What is out of scope by June 1

- Layer 2 automated propagation to channels
- Layer 4 full landing page templates
- Layer 4 automated email/drip platform sync (pending platform identification)
- Layer 4 AI content pipelines beyond ALLY's existing feature
- Layer 5 custom dashboards

## Cross-references

- `STRATEGY/ai_boardroom_architecture_readout_summary.md`
- `STRATEGY/one_ai_agent_per_loan_officer_strategy_summary.md`
- `STRATEGY/lo_persona_profile_as_ai_identity_layer.md`
- `ARCHITECTURE/lo_profile_to_ally_to_ai_twin_system_map.md`
- `WORKFLOWS/team_marketing_system_sync_workflow.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md`
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`
- `MARKETING_SYSTEMS/brand_sync_requirements.md`
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md`
- `NEXT_ACTIONS_QUEUE.md`
