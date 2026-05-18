# LO Persona Content Generation Requirements

**Owner:** Marketing pod lead (production), LO Development (persona review), Jeremy McDonald (operational), Compliance (template-level guardrails)
**Status:** Direction documented, applies once persona profiles are approved and an AI consumer can read them
**Last updated:** 2026-05-18
**Purpose:** Document how Marketing and LO Development should use the LO Persona Profile for content. Same persona, many AI consumers. Persona controls voice and style. Compliance controls structure and disclosures. Both apply together.

## Framing

ALLY is the social and campaign execution layer. The LO Persona Profile is one shared identity layer that lives outside ALLY and is read by many AI tools — ALLY captions, AI Twin, email and text drafting, video scripts, language-group content, team marketing content. Marketing's job is to make sure the persona gets used well in every place that consumes it, and that the same template-level compliance rules apply no matter which AI tool is generating the content.

## How persona improves AI captions

Generic captions sound corporate. Persona-driven captions sound like the LO.

- Tone, humor level, and formality stay consistent across every post
- Preferred words and phrases come through
- Avoided words and phrases stay out
- The audience focus shapes who the post is talking to (first-time buyers vs investors vs realtors)
- Language preference routes to the right model variant for bilingual LOs
- Content topics keep posts in lanes the LO can actually back up in conversation

Net effect: less editing per post, more authenticity, fewer captions that get tossed in review.

## How persona helps emails and text drafts

Email and SMS are higher-friction than social. A wrong tone in an inbox or a text reads worse than a wrong tone in a feed.

- Email subject lines and openers feel like the LO, not a template
- Drip sequences that read like one voice across 8 to 12 emails
- Text drafts that stay short and casual or short and direct depending on the LO's style
- Compliance disclosures still appear in their required positions
- Bilingual LOs get language-matched drafts on the same trigger

## How persona helps language-based groups

The Wave 1 priority is Chinese, Vietnamese, Russian, Spanish, Korean, Latino. Persona enables:

- Language-aware caption and email generation that doesn't read like a machine translation
- Cultural reference points appropriate to the audience (only what the LO has supplied in their persona; never assumed)
- Voice consistency inside the language even when multiple LOs contribute to a group's content
- Group-level voice on top of individual voice, where appropriate (e.g., a Vietnamese team's collective tone with each LO's individual quirks layered in for their own posts)

## How persona helps Team Leaders recruit and support LOs

For Team Leaders, persona is a recruiting and coaching asset:

- A new LO can see what their persona profile looks like and adjust it as they grow
- A Team Leader can use persona to identify content opportunities for each LO on their team (e.g., one LO leans veteran-focused, another leans first-time-buyer-focused)
- Persona makes "this is how we talk" concrete instead of abstract
- Helps a Team Leader spot when an LO's content drifts away from their declared persona — usually a sign the LO is overusing a generic template or relying too heavily on AI without review

## How persona should NOT override compliance

This is the line that cannot move. Per D9, D27, and D33:

- Persona controls voice and style **only**
- Persona does **not** approve content for publication
- Persona does **not** override required disclosures (NMLS, EHL, state-specific, trigger terms, $2,000 Best Price Guarantee)
- Persona does **not** replace template-level compliance review
- Persona does **not** replace human review (D8)
- Persona does **not** authorize rate quoting, scenario-specific guidance, or borrower-specific commentary

If an LO's persona says "I'm a no-jargon, no-hype communicator," compliance still requires the NMLS line. The persona makes the line sound like the LO. The line itself is non-negotiable.

## How template-level compliance still matters

Per D9, compliance reviews **templates**, not individual pieces. Persona changes how the template gets filled in for a specific LO. The template structure stays compliant:

1. Hook
2. Value
3. CTA
4. Disclosures

Persona affects 1, 2, and 3. Disclosures are immutable. Any AI consumer that uses persona must also use the approved template structure and disclosure block.

## Approved templates plus persona produce better, safer content

The combination is the goal:

- Approved template = safe structure, required disclosures, no compliance gaps
- Persona = voice, audience focus, preferred words, language preference
- AI consumer = ALLY captions, AI Twin, email drafting, etc.
- Human review = catches the things automation misses

Removing persona makes content generic. Removing template-level compliance makes content unsafe. Removing human review makes both unforgivable. All three apply.

## Marketing's responsibilities

- Maintain the team kit and template library that AI consumers (including ALLY) draw from
- Review LO persona profiles for voice and tone (alongside LO Development)
- Reissue templates if a persona pattern surfaces a recurring gap
- Spot brand drift across surfaces and reissue kits as needed (per `brand_sync_requirements.md`)
- Coach Team Leaders on how to use persona inside their team's content production
- Flag any persona that conflicts with brand voice for a kit-level conversation, not a one-off override

## LO Development's responsibilities

- Own the intake review process for new and updated personas
- Coach LOs on what a useful persona looks like
- Help LOs evolve their persona over time
- Strip restricted data on intake before approval
- Track persona freshness; nudge LOs whose persona is more than 12 months stale

## Open questions

| # | Question | Owner | Target |
| --- | --- | --- | --- |
| LP1 | Confirm review checklist content for persona review | Marketing + LO Dev | May 29 |
| LP2 | Confirm whether ALLY can honor preferred-word and avoided-word lists at caption time | Thanh + Dat | May 29 |
| LP3 | Confirm whether group-level persona (team or language group) layers on top of individual persona, or whether each LO posts in their own voice only | Marketing + Thanh + Dat | June 12 |
| LP4 | Confirm coaching cadence for Team Leaders on persona usage | Jeremy + LO Dev | June 12 |
| LP5 | Confirm review SLA for persona updates after initial approval | LO Dev | May 29 |

## Cross-references

- `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`
- `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`
- `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`
- `MARKETING_SYSTEMS/brand_sync_requirements.md`
- `PROJECT_DECISIONS_AND_CONTEXT.md` D8, D9, D27, D31, D32, D33
- `NEXT_ACTIONS_QUEUE.md`
