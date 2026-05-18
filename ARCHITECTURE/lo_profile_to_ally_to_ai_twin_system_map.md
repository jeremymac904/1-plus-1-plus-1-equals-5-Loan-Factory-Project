# LO Profile → ALLY → AI Twin System Map

**Owner:** Jeremy McDonald (operational), TERA (technical), Marketing (production), LO Development (persona review), Compliance (template-level guardrails)
**Status:** Architecture documented; SSO-mapped flow gated by TERA discovery answers
**Last updated:** 2026-05-18
**Purpose:** Show how an LO's persona moves from the AI Twin Persona Intake into an approved profile, gets mapped to Loan Factory SSO, and is read by ALLY's caption generation while remaining the same record consumed by the broader Loan Factory AI Twin and future AI LOA workflows. Compliance guardrails remain separate from persona logic.

## High-level map

```
┌────────────────────────────────┐
│ AI Twin Persona Intake (form)  │  119 responses to date
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ LO Dev + Marketing review      │  voice + restricted-data scrub
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ Approved LO Persona Profile    │  schema in `ai_twin_persona_to_master_profile_record.md`
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ Loan Factory SSO mapping       │  profile keyed off SSO subject claim
└──────────────┬─────────────────┘
               ↓
       ┌───────┴────────────────────────────┐
       ↓                                    ↓
┌───────────────────────┐         ┌─────────────────────────────┐
│ ALLY caption service  │         │ Loan Factory AI Twin        │
│ "Enhance Caption with │         │ (and future AI LOA          │
│ AI" reads persona     │         │ workflows) — same persona   │
└──────────┬────────────┘         └──────────────┬──────────────┘
           ↓                                     ↓
┌──────────────────────────────────────────────────────────────┐
│ Compliance template layer — disclosures, structure, review   │
│ Persona never overrides this. Templates apply everywhere.    │
└──────────────────────┬───────────────────────────────────────┘
                       ↓
┌──────────────────────────────────────────────────────────────┐
│ Human review (LO + Team Leader where applicable)             │
└──────────────────────────────────────────────────────────────┘
                       ↓
                  Publish / send
```

## Step 1 — AI Twin Persona Intake produces raw persona data

The existing AI Twin Persona Intake form captures voice, tone, audience focus, market focus, content topics, preferred and avoided words, personal story highlights, communication style, language preferences, and content platform usage. Today's volume: 119 LO responses.

## Step 2 — LO Development or Marketing reviews the intake

LO Development is the primary reviewer; Marketing layers on a voice and brand check. The review:

- Confirms completeness and usability of the voice description
- Scrubs any restricted-data fields that should not live on a persona profile (see schema doc)
- Notes compliance flags (without blocking voice approval)
- Sets review status to Approved, Held, or Requested-Changes

SLA target: 5 business days from intake submission.

## Step 3 — Approved LO Persona Profile is created or updated

The approved profile is created (first-time submission) or updated (subsequent revisions). Schema lives in `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`.

Wave 1 storage: shared Google Sheet or Drive folder per LO, pending TERA confirmation.
Phase 2 storage: TERA-aligned persona service, keyed off SSO subject claim and aligned with the broader AI Twin profile architecture.

## Step 4 — Profile maps to Loan Factory SSO when possible

The profile record is keyed off the LO's Loan Factory SSO subject claim. Any AI consumer the LO authenticates into can look up that LO's persona without a separate auth round trip.

When SSO mapping is not yet wired, the fallback is for the LO to upload or paste their approved persona document into ALLY's profile settings. The fallback produces the same persona-aware caption output, just without the automatic SSO fetch.

## Step 5 — ALLY uses the persona for "Enhance Caption with AI"

When the LO clicks "Enhance Caption with AI" inside ALLY:

1. ALLY identifies the LO via SSO claim
2. ALLY pulls the approved persona profile (or the LO's uploaded persona document, if SSO fetch is not wired)
3. ALLY composes the caption using the selected template, the persona, the selected language if applicable, the compliance template metadata, and the required LO and Loan Factory NMLS information
4. The LO reviews and edits before scheduling or publishing

The full ALLY caption flow lives in `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`.

## Step 6 — AI Twin and future AI LOA use the same profile layer

The Loan Factory AI Twin and any future AI LOA workflows read from the **same** persona record. No duplicate persona stores. The persona schema lives in one place and is consumed by:

- ALLY captions
- AI Twin assistant (per `STRATEGY/one_ai_agent_per_loan_officer_strategy_summary.md`)
- AI LOA workflows (when defined)
- Email and text drafting
- Video script generation
- Language-group content (1+1+1=5)
- Team-level content
- Coaching and training

This is the architectural premise of the broader Loan Factory AI-native plan: build the profile layer first; everything else draws value from it. 1+1+1=5's ALLY caption integration is the first concrete use case.

## Step 7 — Compliance guardrails remain separate from persona

Persona influences voice and style. Compliance enforces structure and disclosures. Both apply together. The template layer:

- Locks structure (hook, value, CTA, disclosure block)
- Locks required disclosures (NMLS, EHL, state-specific marketing, trigger terms, $2,000 Best Price Guarantee)
- Routes state-specific variants where applicable
- Gets reviewed at the template level by Compliance (per D9)

Persona never overrides any of this. Persona never approves content. Human review is the final gate (per D8).

## What this design protects against

- Persona drift: one source means voice updates flow once and reach every AI consumer
- Compliance gaps: structure and disclosures live separately and apply on every channel
- Duplicate persona stores: AI Twin, AI LOA, ALLY, email tools, and video tools all read from the same record
- Restricted-data leakage: the schema explicitly omits SSN, DOB, credit data, borrower data, account numbers, NPI, and health information
- LO surprise: every inferred profile update is visible and editable by the LO (per the broader strategic plan's transparency requirement)

## Open architectural questions

| # | Question | Owner |
| --- | --- | --- |
| P2 | Can TERA map AI Twin profile data to Loan Factory SSO identity for downstream consumers? | TERA via Tara |
| P3 | Can ALLY store a per-LO persona profile inside its PostgreSQL schema, or should it pull from an external profile service? | Thanh + Dat |
| P4 | Can ALLY's "Enhance Caption with AI" use per-LO persona context at inference time? | Thanh + Dat |
| P5 | Can ALLY profile settings include persona upload, persona editor, or persona selection UI for the SSO-fallback path? | Thanh + Dat |
| P10 | Long-term home for the approved LO Persona Profile — ALLY Postgres, separate TERA persona service, or both with a sync? | TERA leadership |

These remain open. Wave 1 does not depend on them. Phase 2 design begins once they are answered.

## Cross-references

- `STRATEGY/ai_boardroom_architecture_readout_summary.md`
- `STRATEGY/one_ai_agent_per_loan_officer_strategy_summary.md`
- `STRATEGY/lo_persona_profile_as_ai_identity_layer.md`
- `ARCHITECTURE/five_layer_marketing_system_architecture.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `WORKFLOWS/team_marketing_system_sync_workflow.md`
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md` D31, D32, D33, D34
- `NEXT_ACTIONS_QUEUE.md`
