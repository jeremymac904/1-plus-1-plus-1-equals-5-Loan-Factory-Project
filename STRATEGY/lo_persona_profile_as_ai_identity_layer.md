# LO Persona Profile as the AI Identity Layer

**Owner:** Jeremy McDonald
**Status:** Direction documented; implementation pending TERA discovery
**Last updated:** 2026-05-18
**Purpose:** State the strategic role of the LO Persona Profile as the reusable AI identity layer that connects the 1+1+1=5 language-group program to Thuan's broader one-AI-agent-per-LO vision, and lock the line between voice and compliance.

## The role

The LO Persona Profile is the reusable AI identity layer for Loan Factory. One persona source per loan officer. Multiple AI consumers. The profile is the bridge between:

- 1+1+1=5 — a near-term, manual-first language-group marketing program
- The broader Loan Factory AI-native strategy — one AI agent per LO, embedded in TERA, evolving over a career

Both efforts depend on the same data structure. Both efforts get better if that structure lives in one place and is read by many tools.

## What the persona supports

The approved LO Persona Profile is read by:

- ALLY enhanced captions (sound like the actual LO, not generic copy)
- The Loan Factory AI Twin assistant
- Future AI LOA workflows
- Email drafts (warm, on-voice, in the LO's tone)
- Text drafts
- Video scripts
- Language-group content variants (Chinese, Vietnamese, Russian, Spanish, Korean, Latino)
- Team-level content where a point person speaks for a group
- Coaching and training (just-in-time, behavioral, non-judgmental)
- Future marketing automation across newsletters, drips, GBP, realtor outreach

The same profile drives every AI consumer. Updates propagate. Voice stays consistent across channels.

## What the persona controls

Persona controls voice, tone, style, relevance, and personalization. Specifically:

- Communication style
- Brand voice (casual, warm, professional, analytical, energetic)
- Content tone
- Humor, directness, and formality levels
- Preferred words and phrases
- Words and phrases to avoid
- Audience focus (first-time buyers, investors, veterans, refinancers, builders, realtors)
- Primary loan focus (conventional, VA, FHA, USDA, DSCR, fix and flip, jumbo)
- Language preferences for bilingual or multilingual LOs
- Content topics the LO is willing and credible to speak to
- Personal story highlights that humanize the content
- Community focus that anchors the LO in a local market

## What the persona does not do

Persona does **not** replace compliance approval. Persona does **not** authorize publishing without human review. Specifically:

- Persona does not override required disclosures (NMLS, EHL, state-specific marketing, trigger terms, $2,000 Best Price Guarantee)
- Persona does not approve content for publishing
- Persona does not replace template-level compliance review
- Persona does not replace human review on any channel
- Persona does not authorize rate quoting, scenario-specific guidance, or borrower-specific commentary
- Persona does not bypass the AI Governance posture the broader plan defines (tenant isolation, audit logging, PII masking, server-side-only LLM calls)

## The line

Persona is voice. Compliance is structure and disclosures. Human review is the final gate. All three apply on every piece. Removing any one of them breaks the system.

## Why one persona, many consumers

If every AI tool stores its own persona, the LO has to redo their voice every time, brand drifts, and updates never propagate. One persona source means:

- LOs maintain one identity, not five
- Brand voice stays consistent across surfaces
- Updates flow once and reach every consumer
- Audit and governance apply to one record, not five
- Compliance review can target one schema and one storage location
- The profile asset compounds in value over time, as the strategic plan calls for

## Anchor the bridge

For 1+1+1=5, the persona seeds ALLY captions and language-group content production.
For the broader AI Twin / AI LOA direction, the same persona evolves into a career-long, behavior-rich profile that powers a personalized AI copilot inside TERA.
The bridge is the same record. The schema lives where TERA leadership directs (`P10` in the persona requirements doc), with a near-term store in Google Sheets or Drive and a long-term home aligned with TERA's stack (React, Python, PostgreSQL, Loan Factory SSO, GKE).

## Operating principles

1. One persona source per LO, keyed off Loan Factory SSO when technically possible
2. Manual upload fallback inside ALLY profile settings until SSO mapping is wired
3. Approved persona only — drafts are not consumable by AI tools until LO Development and Marketing have reviewed
4. Versioning required — every approved version stored with a date and a reviewer, with old versions retained for audit
5. Restricted data never stored — no SSN, DOB, credit data, borrower information, account numbers, NPI, or health information
6. Transparency to the LO — every inferred profile update is visible to the LO and editable by the LO
7. Compliance guardrails layer separately — never embedded inside persona logic

## Cross-references

- `STRATEGY/ai_boardroom_architecture_readout_summary.md`
- `STRATEGY/one_ai_agent_per_loan_officer_strategy_summary.md`
- `ARCHITECTURE/five_layer_marketing_system_architecture.md`
- `ARCHITECTURE/lo_profile_to_ally_to_ai_twin_system_map.md`
- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md` D31, D32, D33, D34
- `NEXT_ACTIONS_QUEUE.md`
