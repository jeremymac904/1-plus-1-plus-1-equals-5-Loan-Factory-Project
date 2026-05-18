# Project Decisions and Context

The living record of every decision made on this program. If something is in this file, treat it as settled. Don't reopen unless something material has changed — and if you do reopen it, document the new decision below the old one with the date and reason.

## Master decision log

| # | Decision | Decided by | When |
| --- | --- | --- | --- |
| D1 | Program framework approved directionally | Andre + Thuan | May 2026 |
| D2 | Target launch: June 1, 2026 | Andre + Thuan + Jeremy | May 2026 |
| D3 | Operational lead: Jeremy McDonald | Andre + Thuan | May 2026 |
| D4 | Cross-functional coordination: Tara Bartoli | Andre | May 2026 |
| D5 | Strategic alignment owners: Andre King + Edward Arvizo | Self-evident | May 2026 |
| D6 | Pilot uses existing systems (Ally, TERA, portal, GBP, Email Drip, IQ) | Andre + Jeremy | May 2026 |
| D7 | No new software builds for June 1 | Jeremy | May 2026 |
| D8 | Human-in-the-loop AI review for all published content | Jeremy + Marketing + Compliance | May 2026 |
| D9 | Template-level compliance (not per-piece) wherever possible | Marketing + Compliance | May 2026 |
| D10 | $2,000 Lowest Rate and Fee Guarantee disclosure on every applicable template | Compliance | Pre-pilot |
| D11 | Minimum 3 LOs per team, **no cap on max** | Jeremy + Andre | May 2026 |
| D12 | LOs across at least 2 cities or states per team | Jeremy + Andre | May 2026 |
| D13 | Bi-weekly Pilot Team Leader meeting cadence | Jeremy | May 2026 |
| D14 | 90-day pilot framework (June 1 → August 30) | Andre + Jeremy | May 2026 |
| D15 | Open Google Form intake (not invite-only) | Jeremy | May 2026 |
| D16 | Existing teams (e.g., Legends Mortgage Team) welcome — same onboarding path | Jeremy + Andre | May 2026 |
| D17 | Capacity gates first wave team count (not policy) | Jeremy | May 2026 |
| D18 | Comp design happens in parallel (does not gate June 1 launch) | Andre + Edward + Jeremy | May 2026 |
| D19 | Bi-weekly Pilot Team Leader meeting chaired by Jeremy through August | Jeremy | May 2026 |
| D20 | LOs may sit on multiple teams (e.g., bilingual + niche) — pick one primary for attribution | Jeremy | May 2026 |
| D21 | Thuan confirmed ASAP start with a few teams (open program, capacity-based waves) | Thuan | May 15, 2026 |
| D22 | Initial target divisions for Wave 1: Chinese, Vietnamese, Russian, Spanish, Korean | Thuan + Jeremy | May 15, 2026 |
| D23 | Early expansion or pilot tracks: Latino, Veteran or Military, Investor or DSCR or Fix and Flip | Thuan + Jeremy | May 15, 2026 |
| D24 | Google Sheets and existing systems are acceptable for launch tracking until TERA stack alignment is confirmed | Jeremy (working answer) | May 15, 2026 |
| D25 | Jeremy may continue independently on docs, workflows, intake, and planning while coordinating with TERA on technical fit | Jeremy + Thuan (working answer) | May 15, 2026 |
| D26 | Repo renamed: `1-plus-1-plus-1-equals-5-Loan-Factory-Project` (https://github.com/jeremymac904/1-plus-1-plus-1-equals-5-Loan-Factory-Project) | Jeremy | May 15, 2026 |
| D27 | ALLY is the social and campaign execution layer inside a larger Loan Factory team marketing system, not the whole program | Jeremy | May 18, 2026 |
| D28 | Every team-facing surface (website, LO pages, newsletter, drip, ALLY, GBP, realtor outreach, optional video and podcast, reporting) reads from one master team marketing record sourced from intake | Jeremy | May 18, 2026 |
| D29 | Wave 1 master team marketing record lives in Tab 1 of `1+1+1=5 Intake Submissions`; Phase 2 home is TERA-backed once stack alignment is confirmed | Jeremy | May 18, 2026 |
| D30 | Same branding and content structure must carry across every team-facing surface; drift triggers a kit reissue and a full redeploy, not piecemeal patches | Jeremy + Marketing | May 18, 2026 |
| D31 | LO Persona Profile becomes the reusable AI identity layer; one persona source, multiple AI use cases (ALLY captions, AI Twin, email, text, video scripts, language groups, team content) | Jeremy | May 18, 2026 |
| D32 | AI Twin Persona Intake (existing form, 119 responses) is the seed for the approved LO Persona Profile and can support ALLY's "Enhance Caption with AI" once integration is wired | Jeremy | May 18, 2026 |
| D33 | Persona controls voice and style only; persona does not approve content, override compliance, or replace human review | Jeremy + Compliance | May 18, 2026 |
| D34 | LO Persona Profile maps to Loan Factory SSO identity when technically possible; manual upload via ALLY profile settings is the fallback until SSO mapping is wired | Jeremy | May 18, 2026 |
| D35 | 1+1+1=5 initial focus is language groups, not niche groups; niche groups follow once the language-group operating model is proven | Jeremy + Andre + Thuan | May 18, 2026 |
| D36 | Email newsletters, drip campaigns, website templates, Google Business Profile, YouTube, and reporting require separate platform-owner discovery before any technical work begins | Jeremy + Marketing | May 18, 2026 |
| D37 | A master group record is required for language-group setup and must exist before the first channel goes live | Jeremy | May 18, 2026 |
| D38 | Wave 1 (June 1) stays manual and lightweight; no custom dashboard, no new software, no automated cross-system sync; technical alignment runs in parallel for Phase 2 | Jeremy | May 18, 2026 |

## Context behind the major decisions

### D2 — June 1, 2026 target launch

Not aspirational. The pilot opens June 1 with whatever first wave Marketing + TERA capacity supports. Delay only if Andre + Thuan explicitly call it.

**Why this date:** Loan Factory loses 90 days of compounding for every month we delay. The pilot is designed to learn fast — the worst version of June 1 is still better than the best version of August 1.

### D6 — Existing systems first

Ally, the Loan Factory portal (Email Campaign / Send Email / Email Drip), Loan Factory IQ, Google Business Profile, Gemini, and NotebookLM already exist. We connect them. We do not replace them.

**Why this matters:** New software builds are 3–6 month projects minimum. The pilot is 90 days. Capacity for new builds doesn't exist on the June 1 path.

### D7 — No new software builds for June 1

Any custom dashboard, microsite generator, AI personalization pipeline, or analytics rollup is **Phase 2 work** — explicitly post-August 30. If the pilot proves a build is mandatory, it gets prioritized in Phase 2.

### D8 — Human-in-the-loop AI review

AI drafts everything: GBP posts, newsletter copy, social captions, Realtor outreach, podcast notes. Humans review before publishing. **No autopublish on any channel.** This protects compliance posture and brand quality while letting AI handle production load.

### D9 — Template-level compliance

Compliance reviews **templates**, not individual pieces. The $2,000 Lowest Rate and Fee Guarantee disclosure is baked into every template that mentions the program — so no one has to remember to add it.

**Why this matters:** Per-piece compliance review doesn't scale. Template-level review does. This is the unlock that lets the Marketing pod support 10–20 teams instead of 200 LOs.

### D11 — Minimum 3 LOs, no cap

Three is the floor — below that, team marketing doesn't generate enough shared load. There's no ceiling. A team of 8, 12, or 20 LOs is fine if the Team Leader can run it.

### D14 — 90-day pilot framework

- **June 1 – June 30:** Stand up first wave. Capture friction.
- **July 1 – July 31:** Iterate. Refine. Onboard second wave.
- **Aug 1 – Aug 30:** Productize. Open intake broadly. Define long-term Team Leader role.

September 1 is the decision point: open intake broadly or extend the pilot.

### D15 — Open Google Form intake

Anyone with the link can apply. Not invite-only. Not gated by leadership pre-approval. Marketing + Jeremy review every submission with a 24–48 hour SLA.

**Why this matters:** Invite-only programs become political. Open intake surfaces who actually wants to lead a team — which is the signal we want.

### D16 — Existing teams welcome

The Legends Mortgage Team and any other existing Loan Factory team can join the pilot under the same onboarding workflow. They can keep their existing brand or adopt the new kit. Their lessons feed the pilot.

**Why this matters:** Existing teams are an asset, not an exception. Making them go through a different process would slow everyone down.

### D17 — Capacity gates team count

Marketing pod and TERA pod confirm how many teams they can support in June. That number is the first wave count. Not a policy decision. Not a strategic preference. A capacity reality.

### D18 — Comp parallel, not gating

Team Leader comp design (Andre + Edward + Finance) runs in parallel. Locked model target: August 30 (pilot retro). First wave Team Leaders operate under current comp during the pilot.

**Why this matters:** Waiting for comp design to finish before launching would push June 1 to September or later. The pilot doesn't require new comp.

### D21 — Thuan confirmed ASAP start

Thuan explicitly directed the team to start with a few teams now rather than wait. Program is open, implementation is capacity-based, intake remains open continuously. Wave 1 begins June 1 with prioritized divisions.

### D22 — Initial target divisions for Wave 1

Chinese, Vietnamese, Russian, Spanish, Korean. These five lead because they are language-anchored, community-anchored, and have clear Team Leader candidates already known to LO Development.

### D23 — Early expansion or pilot tracks

Latino division, Veteran or Military focused team, and Investor or DSCR or Fix and Flip division are tracked as early expansion. They roll in as Marketing and TERA capacity opens. Latino is distinct from Spanish... Spanish anchors language identity, Latino anchors community identity. Both can coexist.

### D24 — Google Sheets first for launch tracking

For June 1, no custom dashboard, no app, no automation build. Manual tracking in Google Sheets covers team roster, division, status, kit status, TERA status, Compliance status, channel activity, and Pilot Leader meeting attendance. See `REPORTING_AND_TRACKING/google_sheets_launch_tracking_framework.md`.

### D25 — Jeremy works independently while coordinating with TERA

Jeremy continues on documentation, workflow design, intake form, planning, and operational coordination without waiting for TERA. Any technical build aligns with TERA's stack guidance before deeper development. TERA provides stack input (frontend, backend, database, auth, hosting, Firebase, repo standards, Claude Code or GitHub workflow). See `TERA_AND_TECH_REQUIREMENTS/tera_stack_alignment_questions.md`.

### D26 — Repo renamed

GitHub repo is now `1-plus-1-plus-1-equals-5-Loan-Factory-Project`. URL: https://github.com/jeremymac904/1-plus-1-plus-1-equals-5-Loan-Factory-Project. Local working folder retains its existing path. All external references use the new URL.

### D27 — ALLY is one layer, not the program

ALLY is the social and campaign execution layer. The full team marketing system also coordinates intake, branding, website team pages, LO landing pages, portal newsletters, Email Drip, GBP, realtor outreach, compliance review, marketing production, TERA setup, and reporting. Documentation, planning, and any future build treat ALLY as one surface inside the stack, not the stack itself.

**Why this matters:** If we treat ALLY as the program, we under-resource website, newsletters, drip, GBP, and compliance. Framing ALLY as one execution layer keeps the rest of the system funded and visible.

See `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md` for the ALLY discovery questions.

### D28 — Master team marketing record drives every surface

Intake produces one master record per team. Every downstream surface (website, LO pages, newsletter, drip, ALLY, GBP, realtor outreach, optional video and podcast, reporting) reads from the master record. No shadow data, no duplicate entry.

**Why this matters:** Without a single source of truth, every surface drifts from every other one. The team's name, brand, languages, niche, channels, cadence, and disclosures live in one place and propagate from there.

See `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md`.

### D29 — Master record lives in Sheets for Wave 1, TERA-backed in Phase 2

For Wave 1, Tab 1 (Teams) of `1+1+1=5 Intake Submissions` Google Sheet is the master record. In Phase 2, the master record migrates into TERA-backed storage once `tera_stack_alignment_questions.md` and `ally_stack_and_integration_requirements.md` are answered. Migration path is documented before migration begins, not after.

### D30 — Brand consistency across every surface

Same logo, palette, voice, structure, and disclosures across website, LO pages, newsletter, drip, ALLY, GBP, realtor outreach, video and podcast (when teams opt in), and internal reporting. Drift triggers a kit reissue and a full redeploy across surfaces — not a patch on one channel.

**Why this matters:** A borrower who finds a team via GBP, then opens its newsletter, then sees its Instagram post, then visits its website should see one consistent team. Drift kills trust faster than slow growth does.

See `MARKETING_SYSTEMS/brand_sync_requirements.md`.

### D31 — LO Persona Profile is the reusable AI identity layer

One LO persona source. Multiple AI consumers. The approved LO Persona Profile is read by ALLY caption generation, AI Twin, email and text drafting, video script generation, language-group content, and team-level content tools. We do not let every AI tool maintain its own persona store.

**Why this matters:** If each tool keeps its own persona, brand voice drifts, LOs have to redo their voice every time, and updates never propagate. One source means consistency and faster iteration.

See `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`.

### D32 — AI Twin Persona Intake supports ALLY caption generation

The existing AI Twin Persona Intake form (already at 119 responses) feeds the approved LO Persona Profile. ALLY's "Enhance Caption with AI" feature should eventually read that profile so generated captions sound like the actual loan officer.

**Why this matters:** Generic AI captions are easy to spot and easy to dismiss. Persona-aware captions land better, get edited less, and protect brand voice without forcing the LO to write from scratch.

See `WORKFLOWS/ai_twin_to_ally_caption_workflow.md`.

### D33 — Persona controls voice and style only

Persona affects tone, audience, word choice, formality. Persona does not approve content, override required disclosures (NMLS, EHL, state-specific, trigger terms, $2,000 Best Price Guarantee), replace template-level compliance review, or replace human review. Compliance and persona layer separately and both apply.

**Why this matters:** Persona that overrides compliance is a compliance gap waiting to ship. The line stays bright.

### D34 — Persona profile maps to SSO when possible, manual upload fallback otherwise

The LO Persona Profile is keyed off the LO's Loan Factory SSO subject claim when technical mapping is wired. Until SSO mapping is wired, the fallback is for the LO to upload or paste their approved persona document into ALLY's profile settings. Both paths produce the same persona-aware captions.

**Why this matters:** Waiting for full SSO integration would push every ALLY caption improvement to Phase 2. The manual upload path unblocks LOs now while TERA completes the long-term integration.

### D35 — Initial focus is language groups, not niche groups

Wave 1 prioritizes Chinese, Vietnamese, Russian, Spanish, Korean, and Latino language groups. Niche groups (Veteran/Military, Investor/DSCR/Fix-and-Flip) are tracked as early expansion but follow the language-group operating model after it is proven.

**Why this matters:** Language anchors community, distinct geography, and clear point-person candidates. Niche groups are valuable but they fragment audience more than language groups do. Proving the model on one language group first gives every later group a working playbook.

### D36 — Newsletter, drip, website, GBP, YouTube, and reporting require separate discovery

Each of these channels has its own platform owner. None of them are assumed to be ALLY's responsibility. Marketing must confirm platform ownership for each before any technical work begins. Confirming this is in `NEXT_ACTIONS_QUEUE.md`.

**Why this matters:** Building inside the wrong platform burns calendar and budget. The June 1 path does not require these channels to be automated, but Phase 2 will, and Phase 2 cannot start without these answers.

### D37 — Master group record is required before any channel goes live

A single source of truth per language group must exist before the first channel goes live. Wave 1 home: Tab 1 of `1+1+1=5 Intake Submissions` Google Sheet. Phase 2 home: TERA-backed once stack alignment confirms a group/team data model.

**Why this matters:** Without one record, every channel drifts. The team name, brand, languages, niche, roster, channels, and disclosures live in one place and propagate from there.

### D38 — Wave 1 stays manual and lightweight; technical alignment runs in parallel

No custom dashboard. No new software. No automated cross-system sync. ALLY and LO Persona Profile discovery supports Phase 2 and is not a June 1 blocker. Marketing, TERA, and Compliance technical work proceeds independently of June 1 manual execution.

**Why this matters:** The June 1 launch's job is to prove the operating model with one language group. The longer technical work has its own clock. Confusing the two slips launch.

## Explicit bets

We are betting on:

1. **AI drafting + human review** scales faster than human-only drafting. If wrong, we burn out the Marketing pod.
2. **Existing systems are enough** for the pilot. If wrong, we'll know which new tooling is mandatory and build it in Phase 2.
3. **Team Leaders will self-select** once we open intake. If wrong, we have to recruit Team Leaders proactively.
4. **Application growth lags marketing activity by 30–60 days.** If wrong, we'll see growth faster (great) or much slower (we recalibrate at 90 days).
5. **Language division wins translate to niche divisions** and vice versa. If wrong, divisions need separate playbooks.

Each bet is revisited at the 90-day retro.

## Operating philosophy (the rules of the road)

- **ACTION > THEORY**
- **EXECUTION > PRESENTATION**
- **SPEED > PERFECTION**
- Use existing systems before building new ones
- Templates over per-piece review
- AI drafts, humans approve
- Capacity gates scope
- Friction surfaced fast at the bi-weekly Pilot Leader meeting
- Fewer teams done well beats more teams done sloppy
- Collaborative, not punitive
- Open the door June 1 with what we have

## How to update this file

When a new decision is made:

1. Add a row to the master decision log
2. Add context below if it's non-obvious
3. Note any decision it supersedes (with date)
4. Reference it in the next leadership update if leadership made the call

Don't delete superseded decisions. Move them to a "Superseded decisions" section at the bottom so the trail is preserved.

## Superseded decisions

_(None yet. As decisions evolve, archive prior versions here with the date of replacement and the reason.)_

## Cross-references

- `EXECUTION_ROADMAP.md` — week-by-week execution plan
- `NEXT_ACTIONS_QUEUE.md` — live operational queue
- `PROJECT_OVERVIEW.md` — what the program is and why
- `MEETING_NOTES/` — meeting recaps where decisions get made
