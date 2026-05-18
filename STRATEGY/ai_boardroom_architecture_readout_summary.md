# AI Boardroom Architecture Readout — Program Summary

**Owner:** Jeremy McDonald
**Status:** Internal summary of an external strategic readout used as a pre-build pressure test
**Last updated:** 2026-05-18
**Source:** "1+1+1=5 LANGUAGE GROUP PROGRAM — AI Boardroom Architecture Review — May 2026" (Google Drive)
**Purpose:** Capture the architectural framing, the master-record requirement, the June 1 MVP definition, the cross-channel consistency requirement, the audience-specific question lists, and the risk and guardrail set so the program team can act on them without re-reading the source document.

## What the readout is

The AI Boardroom Architecture Review is a pre-build pressure test of the 1+1+1=5 language-group program. It was prepared as an internal architectural review before engaging Thanh, Dat, TERA, Marketing, Compliance, and leadership. The readout treats the program as a connected-systems program rather than a new-software program and recommends locking the data model before any channel goes live.

## Executive framing

The program has a social media layer (ALLY). It also has four other layers that do not yet exist in any coordinated form. The risk is not that ALLY is built wrong. The risk is that each channel is built independently, by different teams, without a shared data model. The single most important architectural decision before June 1 is a data decision: what is the master record for a language group, where does it live, and which fields are captured in intake so every downstream system can reference one source of truth?

## ALLY as one layer, not the program

ALLY is the social publishing layer only — connecting accounts, scheduling, publishing, and AI captioning. The program is the orchestration layer above ALLY. The program also coordinates:

- Email newsletter and drip campaign platform (TBD with Marketing)
- Web and landing pages, including Google Business Profile (CMS TBD with Marketing)
- Compliance template library (Loan Factory Compliance)
- Tracking and reporting (Marketing + TERA, manual in Wave 1)

TERA is the LO identity system. The program references TERA for LO profile data but does not live inside TERA. Every group-facing channel references the master group record.

## Master group record requirement

The master group record is the single source of truth. It must exist before the first channel goes live. Storage progression:

- Short term (now through 30 days): Google Sheets, with form intake feeding the sheet
- Medium term (30 to 90 days): Airtable for better API, relational LO roster, and integrations
- Long term (Phase 2): TERA-backed storage pending TERA confirmation of a group/team data model

Field families required at intake:

- Group identity (group_id, language, display name, legal name, tagline, status)
- Brand package (logo, primary and secondary colors, brand-kit URL, approver, approval date)
- Leadership (point person, TERA LO ID, NMLS, email, state, city)
- Roster (member count, member LO IDs, geographic coverage, market_overlap_flag)
- Channel configuration (ally_group_id, email_list_id, drip_sequence_id, landing_page_url, gbp_profile_url, social handles per platform)
- Compliance (approved bio template, approved messaging themes, disclosure language, approver, approval date, state-specific restrictions)
- Tracking (activation date, last publish date, reporting dashboard URL)

The detailed program-side mapping lives in `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md`.

## June 1 MVP

What ships:

- Master group record schema in Google Sheets with all required fields
- Intake forms connected to the master record
- One language group fully onboarded (Spanish recommended) — brand approved, compliance reviewed, roster confirmed, no market overlap
- ALLY configured for that group's point person and ready members
- A 30-day social content calendar drafted, compliance-reviewed, and loaded into ALLY for scheduling
- One approved email template staged
- Compliance approval checklist documented (manual sign-off)

What stays manual:

- Approval workflow over email between Jeremy, Andre, Tara, and the Compliance reviewer
- Cross-channel asset distribution
- Newsletter and drip setup (pending platform identification)
- Landing pages (pending CMS identification)
- Reporting (weekly manual summary from ALLY analytics and the intake sheet)

What is explicitly out of scope for June 1:

- Custom dashboards
- Automated cross-system sync
- Full landing page CMS templates
- AI content generation pipelines beyond ALLY's existing feature
- Automated compliance routing
- Any platform not already in the stack

## Cross-channel consistency requirement

Across every channel where a language group appears, the following fields must be identical:

- Group legal name as it appears in NMLS disclosures
- Group approved tagline
- Approved brand colors and logo version
- Member roster (names, NMLS numbers, states)
- Point person name and contact
- Compliance-approved disclosure language (state-specific variants)
- Active/inactive status

Drift on any of these fields triggers a kit reissue and a full redeploy across surfaces, per `MARKETING_SYSTEMS/brand_sync_requirements.md`.

## Questions captured for each audience

The readout produced explicit question lists. Each list has been mirrored into the appropriate repo file and into `NEXT_ACTIONS_QUEUE.md` for tracking. Headline questions per audience:

| Audience | Headline question |
| --- | --- |
| Thanh and Dat (ALLY) | Does ALLY support group-level publishing accounts, or only individual LO accounts? |
| Thanh and Dat (ALLY) | What does the ALLY data model look like for LOs and groups in the PostgreSQL schema? |
| Thanh and Dat (ALLY) | Does ALLY expose an API or webhook system that external coordinators can call? |
| Thanh and Dat (ALLY) | How does ALLY handle NMLS disclosures for group accounts with multiple licensed LOs? |
| Thanh and Dat (ALLY) | What analytics does ALLY expose, and how are they exportable? |
| TERA leadership | Does TERA have a concept of LO groups or teams beyond the branch/manager hierarchy? |
| TERA leadership | Is there a languages-spoken field on the LO profile in TERA, or a path to add one? |
| TERA leadership | Can TERA provide an API endpoint for LO profile data downstream consumers can use? |
| Marketing | Which platform powers the Loan Factory newsletter? Email Drip? Are they the same? |
| Marketing | What is the current website CMS, and can language groups have their own landing pages? |
| Marketing | Who owns compliance review for email and web templates and what is the SLA? |
| Compliance | Can compliance pre-approve template categories so individual posts do not require per-piece review? |
| Compliance | How are non-English content pieces reviewed, and is there a bilingual reviewer per language? |
| Compliance | Is the language-group program a "marketing entity" for licensing purposes in any state? |
| Leadership | Is the primary goal recruiting, retention, production, or all three? |
| Leadership | What is the expected scale in year one, and who has final activation authority per language group? |
| Leadership | Is there per-group marketing budget, and is the program borrower-facing, LO-facing, or both? |

Full lists live in the source document and in `NEXT_ACTIONS_QUEUE.md`.

## Risks and guardrails

| # | Risk | Guardrail |
| --- | --- | --- |
| R1 | ALLY scope creep — once ALLY is set up, the program is assumed "done" | Every conversation frames ALLY as one layer of five |
| R2 | No master record means five orphan systems | Master group record exists before the first channel goes live |
| R3 | Conflicting templates across channels | All approved brand assets live in one Drive folder; every channel pulls from it |
| R4 | Unapproved content drift by point persons | Written guidelines plus ALLY scheduling requires admin approval before publishing |
| R5 | Translation inconsistency | All translated content comes from compliance-approved translation templates with a single bilingual reviewer |
| R6 | Market overlap not caught at intake | Explicit market_overlap_flag required at intake review |
| R7 | Data-model debt from weak intake | Finalize master group record schema before finalizing the next intake form |
| R8 | Overbuilding before validation | June 1 is manual; July 1 is semi-automated; nothing automates that has not first worked manually |
| R9 | Platform decisions made without stack knowledge | No email or web work begins until Marketing answers platform questions |
| R10 | ALLY compliance gap on group-account NMLS disclosures | Do not activate group publishing in ALLY until Thanh and Dat confirm in writing |

## Cross-references

- `STRATEGY/one_ai_agent_per_loan_officer_strategy_summary.md`
- `STRATEGY/lo_persona_profile_as_ai_identity_layer.md`
- `ARCHITECTURE/five_layer_marketing_system_architecture.md`
- `ARCHITECTURE/lo_profile_to_ally_to_ai_twin_system_map.md`
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `WORKFLOWS/team_marketing_system_sync_workflow.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md`
- `MARKETING_SYSTEMS/brand_sync_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md`
- `NEXT_ACTIONS_QUEUE.md`

## Source

Google Drive folder `13D0ys0Pp0l0Auao1lL7-tBmyhNXQo6VU` — document "5_Architecture_Readout" (May 2026 AI Boardroom Architecture Review for 1+1+1=5 Language Group Program).
