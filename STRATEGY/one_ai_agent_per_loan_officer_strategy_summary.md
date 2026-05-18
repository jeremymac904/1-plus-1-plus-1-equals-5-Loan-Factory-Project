# One AI Agent Per Loan Officer — Strategy Summary

**Owner:** Jeremy McDonald
**Status:** Internal summary of the broader Loan Factory AI-native strategic plan
**Last updated:** 2026-05-18
**Source:** "One AI Agent Per Loan Officer — Loan Factory Strategic Plan" (Google Drive)
**Purpose:** Capture Thuan's broader AI-native direction in a form that the 1+1+1=5 program can reference. The 1+1+1=5 program is one near-term execution layer inside the longer strategic arc this plan describes. The bridge between both is the LO Persona Profile.

## What the plan is

A strategic systems architecture for Loan Factory's AI-native future. The plan frames "one AI agent per loan officer" — not one AI for the company, not one AI for every borrower — as the right strategic frame. Each LO gets a persistent, personalized, action-capable AI operating layer embedded inside TERA, evolving with them over their entire career.

## Thuan's direction

Loan Factory has the infrastructure to win the decade — 2,500+ active LOs, 100K-LO database, TERA, ALLY, LF IQ. The strategic question is whether Loan Factory will define what AI-native mortgage brokerage looks like or whether someone else will. Thuan's instinct that there should be one AI per LO, embedded in the platform they already live in, is the right frame.

TERA becomes the operating system for AI-native loan officers. Every new LO gets a personalized AI copilot on day one. That copilot knows their pipeline, speaks their language, coaches their gaps, markets for them, follows up for them, and gets smarter every day they use it. The LOs who have it outperform those who do not. The performance gap becomes the recruitment story. The recruitment story brings in better LOs. Better LOs produce more data. More data makes the AI smarter. The flywheel closes.

## What this is not

- Not a chatbot
- Not a knowledge-base search box
- Not a generic "ask anything" widget
- Not a one-off internal tool

It is a persistent, personalized, action-capable AI operating layer that lives inside every LO's TERA account and evolves over a full career.

## LO AI Profile as the core asset

The product moat is not the LLM. Any company can call Claude or GPT-4o. The moat is the **accumulated LO profile** — the growing, persistent, increasingly accurate representation of each LO's behavior, relationships, knowledge, goals, and production patterns. The profile gets more valuable every day. It cannot be copied by a competitor. It belongs to the LO relationship.

Final strategic recommendation from the plan: **build the profile layer first**. Everything else (pipeline Q&A, email drafting, coaching, marketing, training) draws its value from the profile's depth and accuracy. The profile is what makes this a personalized copilot rather than a generic chatbot, and what creates the retention moat.

For 1+1+1=5, this is the same profile we are seeding with the AI Twin Persona Intake (119 responses) and shaping into the approved LO Persona Profile that ALLY's "Enhance Caption with AI" should eventually read from. The same persona supports the company-wide AI Twin / AI LOA, email and text drafting, video scripts, language-group content, and team content. One persona source. Many AI consumers. See `STRATEGY/lo_persona_profile_as_ai_identity_layer.md`.

## TERA as the long-term operating layer

TERA is the platform the LO already lives in. The AI operating layer must run inside TERA, not next to it. The plan calls for:

- AI Gateway Layer (enforces tenant isolation, compliance filters, rate limits, full audit logging)
- Agent Engine (orchestration brain that decides what tools to use and what actions to take)
- Profile Service (the LO AI profile, queried on every agent request and written back to)
- Tool Layer (discrete, permission-gated, audited actions the agent can take)
- Event-driven triggers (loan status changes, document uploads, rate alerts, lead-cold thresholds, training completions)

For 1+1+1=5, the implication is that the long-term home of the LO Persona Profile should align with TERA, not with ALLY. ALLY is one consumer of the profile, not the home of it.

## Five modes of operation

1. **Reactive** — answers questions with full TERA context
2. **Proactive** — surfaces insights without being asked (rate-lock expirations, lead-cold alerts)
3. **Execution** — takes actions inside TERA (create task, draft email, update note) with LO approval
4. **Coaching** — analyzes behavior, delivers feedback (response times, follow-up consistency)
5. **Learning** — tutors the LO on products, guidelines, scenarios, and compliance

## Personalization, memory, coaching, marketing, pipeline

- **Personalization:** identity, experience level, communication style, product expertise, production behavior, referral network health, goals, AI behavior settings
- **Memory:** three-tier model — working memory (session), episodic memory (30 to 90 days), profile memory (career-scoped)
- **Coaching:** personalized, timely, behavioral, non-judgmental; surfaced just-in-time when working on files
- **Marketing:** platform-specific content in the LO's voice, all passing through a compliance filter before any LO approval
- **Pipeline:** full read access and controlled write access to TERA — outstanding conditions, rate locks, document submission, lender communication, borrower context cards

## Security, privacy, audit, and compliance

Non-negotiable requirements lifted from the plan that 1+1+1=5 must honor by association:

- Tenant isolation at the database layer — every query filtered by `lo_id`
- Immutable audit logging on every AI action — who requested, what the AI did, inputs, outputs, approve/reject, timestamp
- Server-side-only LLM calls — no API keys in client code
- PII masking before any external API call — loan IDs and borrower names replaced with pseudonymous IDs
- LO ability to disable any AI tool category
- Compliance filter on all marketing content (NMLS, EHL, state-specific marketing, rate advertising, trigger terms, Loan Factory brand standards)
- AI Governance Committee (Compliance, Legal, Operations, Technology, Product) reviews behavior quarterly
- ECOA / Fair Lending: AI must never make lending recommendations based on protected class characteristics; coaching and scenario tools must be tested for disparate impact
- CFPB AI guidance: monitor evolving guidance; the AI assists the LO and never makes credit decisions

These requirements apply to the LO Persona Profile, to ALLY's caption service when persona context is integrated, and to any future AI consumer.

## Bridge to 1+1+1=5

- 1+1+1=5 is a connected-systems marketing program for language groups
- The plan's "one AI per LO" vision is a multi-year platform direction
- Both intersect at the **LO Persona Profile**
- 1+1+1=5 supplies a near-term, real-world use case (ALLY captions for language-group content) and a real persona dataset (119 AI Twin Persona Intake responses) that seed the profile layer the plan calls for
- Persona controls voice and personalization, not compliance — consistent across both the program and the plan
- The plan's tenant isolation, audit, compliance-filter, and PII-masking requirements set the bar for how 1+1+1=5 stores and uses persona data

## Open questions raised against 1+1+1=5

- Where should the long-term LO Persona Profile live — inside ALLY's Postgres, inside a dedicated TERA persona service, or both with a sync?
- Should the 1+1+1=5 program send its approved persona forward into the AI Twin profile schema automatically once that schema exists?
- Should ALLY's caption service read from the same profile service the AI Twin will use, or from a derived view scoped for social caption generation?
- Which Loan Factory governance forum signs off on the persona schema, versioning, and review SLA?

These questions are tracked in `NEXT_ACTIONS_QUEUE.md` and in `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`.

## Cross-references

- `STRATEGY/ai_boardroom_architecture_readout_summary.md`
- `STRATEGY/lo_persona_profile_as_ai_identity_layer.md`
- `ARCHITECTURE/five_layer_marketing_system_architecture.md`
- `ARCHITECTURE/lo_profile_to_ally_to_ai_twin_system_map.md`
- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md`
- `NEXT_ACTIONS_QUEUE.md`

## Source

Google Drive folder `13D0ys0Pp0l0Auao1lL7-tBmyhNXQo6VU` — document "One AI Agent Per Loan Officer — Loan Factory Strategic Plan" (May 2026 AI Boardroom).
