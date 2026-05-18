# LO Persona Profile and ALLY Integration Requirements

**Owner:** Jeremy McDonald
**Audience:** TERA leadership (via Tara), Thanh, Dat, Marketing pod lead, LO Development, Compliance, Thuan, Andre
**Status:** Discovery and requirements, no build yet
**Last updated:** 2026-05-18
**Purpose:** Document how an approved LO Persona Profile should eventually integrate with ALLY's AI caption generation and with the broader Loan Factory AI Twin / AI LOA strategy. Frame the persona as one shared identity layer that multiple AI tools can read from.

## Framing

**ALLY is the social media scheduling, publishing, campaign, and AI caption layer.** It is not the whole program. The full 1+1+1=5 system is the broader language-based and niche-based marketing program, which includes website, newsletters, drips, GBP, realtor outreach, compliance review, marketing production, TERA setup, and reporting (per `WORKFLOWS/team_marketing_system_sync_workflow.md`).

The LO Persona Profile is **one source** with **many use cases**. ALLY's enhanced caption generation is one of those use cases. The future AI Twin / AI LOA is another. Email and text drafting, video scripts, language-group content, and team-level marketing are others. The persona belongs to the LO. The AI tools read from it.

## Known facts

### ALLY stack (confirmed by TERA)

- **Frontend:** React
- **Backend:** Python
- **Database:** PostgreSQL
- **Authentication:** Loan Factory SSO
- **Hosting:** Google Kubernetes Engine (GKE)
- **Firebase:** Not used
- **Workflow:** GitHub + Claude Code

### Existing persona source

- Jeremy already has an **AI Twin Persona Intake form** with **119 loan officer responses**.
- That form captures useful persona data for emails, text messages, social media content, AI Twin assistant behavior, LO communication style, market focus, personality, tone, audience, and content preferences.
- This is not a one-off data set. It is the seed for a shared LO persona identity layer.

### What ALLY does today (assumed)

- ALLY supports "Enhance Caption with AI" today, generating captions from a post template.
- ALLY does not currently read per-LO persona context (assumption to be confirmed with Thanh and Dat).
- ALLY does not currently expose a per-LO persona upload, editor, or selection in profile settings (assumption to be confirmed).

## How persona data supports ALLY

Tying the LO Persona Profile to ALLY's caption generation means:

- Captions sound like the actual loan officer, not generic corporate copy.
- Tone, humor level, formality level, directness level, preferred words, and avoided words all carry through.
- Language preference can route to the right language model variant for bilingual or multilingual LOs.
- Content topics, audience focus, and market focus help the model write captions that are relevant to the LO's book, not generic mortgage filler.
- Compliance guardrails (NMLS, EHL, state-specific, trigger term, $2,000 Best Price Guarantee) stay layered separately from persona so persona never overrides compliance.

## How persona data supports AI Twin / AI LOA

The same persona profile, with no duplication, drives:

- AI Twin assistant tone and voice
- AI LOA workflows (when the program defines them)
- Email drafts
- Text message drafts
- Video scripts
- Long-form content like blog posts and podcast notes
- Language-group content variants
- Team-level marketing content where a Team Leader speaks on behalf of a team

If persona lives in one place and is read from by many systems, brand voice stays consistent and updates propagate.

## How this fits the ALLY stack

| Layer | How persona fits |
| --- | --- |
| React frontend | Profile settings page can include a persona section — view, edit, request review, see review status |
| Python backend | Persona service exposes per-LO profile via an internal API; ALLY caption service reads from it when "Enhance Caption with AI" fires |
| PostgreSQL | Persona profiles stored in a tenant-scoped schema; row-level scoping by Loan Factory SSO identity |
| Loan Factory SSO | Persona record keyed off the LO's SSO subject claim; only the authenticated LO and authorized reviewers can read or write their own profile |
| GKE | Persona service can run as a workload alongside the existing ALLY services |
| Firebase | Not used; no change |
| GitHub + Claude Code | All persona service work lives in TERA's standard workflow; no shadow repo |

This slots cleanly into the stack TERA already runs. No new infrastructure required.

## What should be stored in the LO Persona Profile

Suggested fields (full schema lives in `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`):

- Identity (full name, Loan Factory email, Loan Factory SSO ID, NMLS number)
- Markets and licenses (primary market, states licensed, languages spoken)
- Audience focus (preferred audience, primary loan focus)
- Voice and tone (communication style, personality summary, brand voice, content tone, humor level, directness level, formality level)
- Word lists (preferred words and phrases, words or phrases to avoid)
- Background (personal story highlights, professional background, community focus)
- Content (content topics, social platforms used)
- Compliance flags (flags raised during review)
- Operational (review status, reviewed by, last updated, source form response link, approved persona document link, ALLY profile sync status, AI Twin sync status, notes)

## What should NOT be stored in the LO Persona Profile

Hard line. The persona profile is a marketing voice artifact. It is not a CRM, an LOS, or a borrower record. Do not store:

- Social Security numbers
- Dates of birth
- Credit data of any kind
- Borrower information
- Private client details
- Account numbers
- Any non-public personal information (NPI)
- Health information
- Anything not needed for persona, voice, or marketing content

If a field cannot be answered with "would the LO post this on LinkedIn", it does not belong in the persona profile.

## Security and privacy considerations

- **Identity scoping:** every read and write is scoped to the authenticated LO's SSO subject claim. No cross-LO reads.
- **Reviewer access:** Marketing and LO Development reviewers get scoped read or read-write only during the review window.
- **Audit:** every change to a persona profile is logged with timestamp and SSO subject claim, append-only.
- **Encryption:** at rest in PostgreSQL and in transit over TLS.
- **Backup:** standard TERA database backup applies.
- **Retention:** persona retained while the LO is active at Loan Factory; archived or deleted on offboarding per TERA's standard data retention policy.
- **Export and portability:** the LO can request an export of their own persona profile.
- **No third-party sharing:** persona data is not shared with ALLY's upstream vendor (if ALLY uses a third-party AI provider, only minimum necessary persona context is sent at inference time, and TERA confirms the vendor's data handling posture before integration ships).

## Compliance boundaries

Per D9 and D27, compliance review happens at the **template level**. Persona controls voice and style. Persona does **not**:

- Override required disclosures (NMLS, EHL, state-specific, trigger terms, $2,000 Best Price Guarantee)
- Approve content for publication
- Replace human review
- Bypass any Loan Factory marketing policy
- Touch borrower-specific or rate-quote content

When ALLY generates a caption with persona context, the caption must still pass template-level compliance review and human review before publishing (per D8).

## Open questions

Captured for TERA, Thanh, Dat, Marketing, Compliance, and leadership:

| # | Question | Owner | Target |
| --- | --- | --- | --- |
| P1 | Who owns the AI Twin Persona Intake data today? | Jeremy + LO Dev | May 22 |
| P2 | Can TERA map AI Twin profile data to Loan Factory SSO identity? | TERA via Tara | May 27 |
| P3 | Can ALLY store a per-LO persona profile? | Thanh + Dat via Tara | May 27 |
| P4 | Can ALLY's "Enhance Caption with AI" use per-LO persona context at inference time? | Thanh + Dat via Tara | May 27 |
| P5 | Can ALLY profile settings include a persona upload, persona editor, or persona selection UI? | Thanh + Dat via Tara | May 27 |
| P6 | Can persona also be scoped at the team or language-group level (group voice on top of individual voice)? | Thanh + Dat + Marketing | May 29 |
| P7 | Can Marketing or LO Development review and approve persona profiles before they become active? | Marketing + LO Dev | May 29 |
| P8 | Can Compliance guardrails sit separately from persona voice so persona never overrides disclosures? | Compliance + TERA | May 29 |
| P9 | Can persona-generated content still use approved disclosure templates automatically? | Compliance + TERA | May 29 |
| P10 | Where should the approved LO Persona Profile live long term — inside ALLY's Postgres, inside a separate TERA persona service, or both? | TERA leadership | June 12 |
| P11 | What should Jeremy avoid building separately so TERA does not end up with two persona systems? | TERA leadership | May 22 |
| P12 | Does ALLY's caption service call a third-party AI provider, and if so, what is the data handling posture? | Thanh + Dat | May 29 |

These map into `NEXT_ACTIONS_QUEUE.md` as persona discovery items.

## What we are NOT building

- No persona dashboard for June 1.
- No custom persona app.
- No production code in this pass.
- No change to June 1 MVP scope.
- No replacement for the existing Google Form intake until TERA confirms a Phase 2 home.

## Cross-references

- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md` — desired workflow
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md` — master persona record schema
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md` — Marketing and LO Dev usage
- `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md` — broader ALLY discovery
- `TERA_AND_TECH_REQUIREMENTS/tera_stack_alignment_questions.md` — TERA stack questions
- `PROJECT_DECISIONS_AND_CONTEXT.md` D8, D9, D27, D31, D32, D33, D34
- `NEXT_ACTIONS_QUEUE.md`
