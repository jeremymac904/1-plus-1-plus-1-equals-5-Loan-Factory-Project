# AI Twin Persona to Master Profile Record

**Owner:** Jeremy McDonald (operational), LO Development (review), Marketing (voice review), TERA (technical home), Compliance (boundaries)
**Status:** Schema defined, interim store TBD with TERA, no production build in this pass
**Last updated:** 2026-05-18
**Purpose:** Define a practical master LO Persona Profile record. One LO persona source. Multiple AI use cases. The record is fed by the AI Twin Persona Intake (existing form, 119 responses today) and read by ALLY caption generation, AI Twin, email and text drafting, video scripts, and team or language-group content tools.

## Why this exists

Persona data is being collected in one place (the AI Twin Persona Intake). It needs a stable home with a stable schema so every AI consumer reads from the same source instead of building its own. Without that, every tool ends up with its own duplicate, drift sets in, and the LO has to redo their voice every time.

## Master persona record schema

Each row is one LO. Field names are stable. The record is keyed off the LO's Loan Factory SSO identity when that mapping is wired.

### Identity

| Field | Notes |
| --- | --- |
| LO full name | Required |
| Loan Factory email | Required |
| Loan Factory SSO ID | Populated when SSO mapping is wired (P2) |
| NMLS number | Required for caption disclosures |

### Markets and licenses

| Field | Notes |
| --- | --- |
| Primary market | Used for content topic relevance |
| States licensed | Used for state-specific disclosure routing |
| Languages spoken | Drives language variant routing in ALLY and other AI tools |

### Audience and focus

| Field | Notes |
| --- | --- |
| Preferred audience | First-time buyers, move-up buyers, investors, veterans, refinancers, builders, realtors, etc. |
| Primary loan focus | Conventional, VA, FHA, USDA, DSCR, fix and flip, jumbo, etc. |
| Community focus | Cultural, faith, alumni, neighborhood, professional, etc. |

### Voice and tone

| Field | Notes |
| --- | --- |
| Communication style | LO's natural style described in plain language |
| Personality summary | A short paragraph the LO uses to describe themselves |
| Brand voice | Casual, warm, professional, analytical, energetic, etc. |
| Content tone | The feel of finished content (encouraging, no-hype, no-jargon, etc.) |
| Humor level | None / dry / playful / heavy |
| Directness level | Diplomatic / balanced / direct / very direct |
| Formality level | Casual / conversational / professional / formal |

### Word lists

| Field | Notes |
| --- | --- |
| Preferred words and phrases | Words and phrases the LO likes to use |
| Words or phrases to avoid | Words the LO never wants to see in their content |

### Background

| Field | Notes |
| --- | --- |
| Personal story highlights | Background, family, faith, military service, sports, etc. |
| Professional background | Years in mortgage, prior roles, education |
| Community focus | Already in audience and focus, repeated here for narrative use |

### Content

| Field | Notes |
| --- | --- |
| Content topics | Topics the LO is willing to talk about (rates, programs, market updates, education, lifestyle, etc.) |
| Social platforms used | Facebook, Instagram, LinkedIn personal, LinkedIn company, YouTube, TikTok, X, Threads, GBP |

### Compliance and operational

| Field | Notes |
| --- | --- |
| Compliance flags | Anything flagged during review (does not block voice approval) |
| Review status | Draft / In Review / Approved / Held / Archived |
| Reviewed by | LO Dev or Marketing reviewer |
| Last updated | ISO date |
| Source form response link | Link to the AI Twin Persona Intake response |
| Approved persona document link | Link to the approved persona document (PDF or Google Doc) used in the manual upload fallback path |
| ALLY profile sync status | Not synced / Manual upload / SSO-mapped |
| AI Twin sync status | Not synced / Manual / SSO-mapped |
| Notes | Free-form notes from reviewer or Jeremy |

## Fields that must NOT be stored

This is a marketing voice artifact. It is not a CRM record. Hard "do not store" list:

- Social Security numbers (SSN)
- Date of birth
- Credit data of any kind
- Borrower information
- Private client details
- Account numbers
- Non-public personal information (NPI)
- Health information
- Anything not needed for persona, voice, or marketing content

If a reviewer encounters one of these on an intake response, they strip it during review. The persona is not approved until clean.

## Review workflow

1. LO submits intake
2. LO Development reviewer checks completeness, voice usability, restricted-data scrubbing
3. Marketing reviewer checks voice and tone fit
4. Compliance flags noted but do not block voice approval
5. Reviewer sets review status to Approved or Held
6. If Approved, the record is created or updated
7. The LO is notified that their persona is active

## Versioning

- Each approved version of a persona gets a version number and date.
- LOs can submit updates; updates re-enter review.
- ALLY and other consumers always read the most recent Approved version.
- Old versions are retained for audit, not for live use.

## Phasing

| Layer | Wave 1 / Phase 1 | Phase 2 (post-August 30) |
| --- | --- | --- |
| Intake | Existing AI Twin Persona Intake form | Same form, posting to TERA-backed persona service |
| Review | LO Dev + Marketing review by hand | Same model, reviewed inside TERA review UI |
| Storage | Interim shared store (Sheet or doc set) | TERA-backed persona service in PostgreSQL, SSO-keyed |
| ALLY ingestion | Manual upload via ALLY profile settings | Automatic SSO-mapped fetch |
| AI Twin ingestion | Manual reference | Automatic SSO-mapped fetch |
| Reporting | None for Wave 1 | Persona coverage and freshness reported in the unified dashboard |

## Open questions

| # | Question | Owner | Target |
| --- | --- | --- | --- |
| MP1 | Confirm interim store location for Wave 1 (Sheet, Drive folder, or both) | Jeremy + LO Dev | May 25 |
| MP2 | Confirm Phase 2 persona service home with TERA | TERA leadership | June 12 |
| MP3 | Confirm review SLA target (5 business days proposed) | LO Dev + Marketing | May 25 |
| MP4 | Confirm reviewer access controls | TERA + Compliance | May 29 |
| MP5 | Confirm export-on-request flow for LOs | TERA + Compliance | June 12 |
| MP6 | Confirm whether AI Twin and ALLY both read the same record, or whether each has a derived view | TERA + Thanh + Dat | June 12 |

## Cross-references

- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `MARKETING_SYSTEMS/lo_persona_content_generation_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md` D31, D32, D33, D34
- `NEXT_ACTIONS_QUEUE.md`
