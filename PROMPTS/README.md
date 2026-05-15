# PROMPTS

AI drafting prompts for Gemini, NotebookLM, and any other AI tools used in the content production pipeline.

## What goes here

- GBP post drafting prompts
- Newsletter drafting prompts (per division if needed)
- Social post drafting prompts (per platform)
- Realtor outreach drafting prompts
- Podcast / video script drafting prompts
- Compliance language prompts (so AI bakes the $2,000 Lowest Rate and Fee Guarantee disclosure into every draft)
- In-language drafting prompts (Spanish, Vietnamese, Russian, Korean)

## What doesn't

- Customer-facing content output (that gets reviewed by Team Leader + Compliance, then published)
- Brand voice strategy (high-level voice notes live in `MARKETING_SYSTEMS/`)

## Naming

- Channel prompt: `prompt_[channel]_[variant].md`
- Example: `prompt_gbp_post_english.md`, `prompt_newsletter_vietnamese.md`, `prompt_realtor_outreach_investor.md`

## Prompt structure

Each prompt doc should include:

1. **Purpose** — what the prompt produces
2. **Input** — what data goes in (team name, division, market, recent news, etc.)
3. **The prompt itself** — the actual text fed to Gemini / NotebookLM
4. **Expected output structure** — format the AI returns
5. **Compliance hooks** — what disclosures/language must always appear
6. **Human review notes** — what the reviewer should check before publishing

## Iteration

Prompts evolve. When you find a phrasing that consistently produces better output, update the prompt doc. Old versions move to `ARCHIVE/` with a note about what changed.

## Compliance reminder

Every AI-drafted piece is reviewed by a human before publishing. No autopublish. The $2,000 Lowest Rate and Fee Guarantee disclosure must be present on every applicable piece — bake it into the prompt so it shows up by default.

## Cross-references

- `MARKETING_SYSTEMS/` — voice, brand variants, compliance language library
- `WORKFLOWS/` — content publishing workflow
- Drive: `LOAN_FACTORY_TEAM_MARKETING_EXECUTION_SYSTEM/MARKETING_AND_TERA_REQUIREMENTS.md` — human review checkpoints
