# 1+1+1=5 — Loan Factory Team Marketing Enhancement Program

Official operational planning repository for the Loan Factory 1+1+1=5 Team Marketing Enhancement Program.

This repository documents program strategy, language-group rollout, team and group onboarding, marketing workflows, ALLY social publishing alignment, email newsletter and drip campaign requirements, website template alignment, compliance guardrails, the LO Persona Profile and AI Twin integration strategy, tracking and reporting requirements, open technical and operational questions, and next actions. It is the single source of operational truth for the program.

## 1. Executive summary

1+1+1=5 is a Loan Factory language-based marketing and group collaboration program. It helps loan officers who speak the same language collaborate across different cities and states without competing in the same local market. Initial focus is language groups, not niche groups. The first wave prioritizes Chinese, Vietnamese, Russian, Spanish, Korean, and Latino communities, with Veteran/Military and Investor/DSCR/Fix-and-Flip as early expansion tracks.

The program connects existing Loan Factory infrastructure into one repeatable team marketing kit and gives group point persons the support to run it. It is intentionally a connected-systems program, not a new-software program. ALLY is the social publishing and AI caption layer inside the program. Email newsletters, drip campaigns, website templates, Google Business Profile, compliance review, and reporting remain separate connected layers. The LO Persona Profile is the reusable AI identity layer that supports ALLY captions, the broader Loan Factory AI Twin, and future AI LOA workflows.

## 2. Current status

- **Status:** Approved directionally. Execution mode.
- **Target launch:** June 1, 2026
- **Operational lead:** Jeremy McDonald
- **Cross-functional coordination:** Tara Bartoli (Marketing + TERA)
- **Strategic alignment:** Andre King, Edward Arvizo
- **Executive sponsor:** Thuan Nguyen
- **ALLY stack (TERA-confirmed):** React frontend, Python backend, PostgreSQL, Loan Factory SSO, Google Kubernetes Engine, GitHub + Claude Code workflow. Firebase not in use.
- **Persona data on hand:** AI Twin Persona Intake has 119 LO responses already collected.

## 3. June 1 MVP scope

June 1 is a working operating model for one language group, executed manually, with workflows and a master group record that prove the design before any automation is introduced.

Wave 1 ships:

- Master group record schema in Google Sheets, populated for the first approved language group
- Intake forms connected to the master record (notification path live, structured routing manual)
- One language group fully onboarded (brand approved, compliance reviewed, roster confirmed, market overlap checked)
- ALLY configured for that group's point person and ready members
- A 30-day social content calendar drafted, compliance-reviewed, and loaded into ALLY for scheduling
- One approved email newsletter template staged
- Compliance approval checklist documented (manual sign-off)
- Bi-weekly Pilot Team Leader meeting cadence active

## 4. What is in scope

- Language-group framing across each connected channel
- Intake → review → approval → activation workflow
- Master group record as the single source of truth
- Brand and content kit per group
- ALLY social publishing alignment
- Email newsletter and drip campaign requirements (platform owners to be confirmed)
- Website team page and LO landing page requirements (CMS owner to be confirmed)
- Google Business Profile workflows per market
- Realtor outreach templates
- Template-level compliance review with disclosure language locked
- LO Persona Profile strategy and AI Twin integration strategy
- Reporting and tracking, starting with Google Sheets and ALLY analytics

## 5. What is out of scope (for June 1)

- New software builds
- Custom dashboards
- Automated cross-system sync
- Full landing page CMS templates
- AI content generation pipelines beyond what ALLY already offers
- Automated compliance routing
- Any platform not already in the stack
- Per-piece compliance review (template-level review applies instead)

These items belong to Phase 2 work after the 90-day retro, and only if the pilot validates the need.

## 6. System layers

The program is one program with five connected layers. ALLY is one layer, not the whole program.

| Layer | Function | Channels and surfaces |
| --- | --- | --- |
| 1. Intake and approval | Capture group and LO data, route to review, approve | Google Forms, Marketing review, Compliance review |
| 2. Master group record | Single source of truth per group | Google Sheets (Wave 1) → Airtable (interim) → TERA-backed (Phase 2) |
| 3. Brand and content kit | Group identity, templates, disclosures | Drive folder per group, compliance-approved template library |
| 4. Channel execution | Publish in the group's brand | ALLY (social), email newsletter, email drip, website team and LO pages, Google Business Profile, YouTube where supported |
| 5. Tracking, reporting, governance | Activity, performance, compliance posture | Google Sheets, ALLY analytics, manual weekly rollup |

All channels reference the master group record. Channels do not own program data. The program owns the data and the channels execute against it.

## 7. Known ALLY stack

| Layer | Confirmed |
| --- | --- |
| Frontend | React |
| Backend | Python |
| Database | PostgreSQL |
| Authentication | Loan Factory SSO |
| Hosting | Google Kubernetes Engine (GKE) |
| Firebase | Not used |
| Development workflow | GitHub + Claude Code |

ALLY is the social media scheduling, publishing, campaign, and AI caption layer. ALLY supports "Enhance Caption with AI" today; whether that feature can read per-LO persona context, whether ALLY can scope content at the group level, and which downstream destinations ALLY publishes natively are open technical questions tracked in `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`.

## 8. LO Persona Profile strategy

The LO Persona Profile is the reusable AI identity layer for Loan Factory. One persona source per loan officer, multiple AI consumers. The approved persona supports:

- ALLY's "Enhance Caption with AI" so generated captions sound like the actual loan officer
- The broader Loan Factory AI Twin and any future AI LOA workflows
- Email drafts
- Text drafts
- Video scripts
- Language-group content
- Team-level content
- Coaching and training
- Future marketing automation

Persona controls voice, tone, style, relevance, and personalization. Persona does **not** replace compliance approval. Persona does **not** authorize publishing without human review. Template-level compliance, required disclosures (NMLS, EHL, state-specific, trigger terms, $2,000 Best Price Guarantee), and human review still apply on every channel.

The AI Twin Persona Intake (existing form, 119 LO responses) seeds the approved LO Persona Profile. The profile is keyed off Loan Factory SSO when technically possible, with a manual upload fallback inside ALLY profile settings until SSO mapping is wired. Storage, review, and approval are tracked in `FORMS_AND_ONBOARDING/ai_twin_persona_to_master_profile_record.md`. The bridge between the 1+1+1=5 program and Thuan's broader one-AI-agent-per-LO vision is this same persona layer; see `STRATEGY/` for the full strategic context.

## 9. Repository map

```
1-plus-1-plus-1-equals-5-Loan-Factory-Project/
├── README.md                                — this file
├── PROJECT_OVERVIEW.md                      — what the program is and why
├── VISION_AND_MISSION.md                    — long-arc direction
├── EXECUTION_ROADMAP.md                     — week-by-week and 90-day plan
├── PROJECT_DECISIONS_AND_CONTEXT.md         — locked decisions and context
├── CURRENT_TEAM_AND_STAKEHOLDERS.md         — roles and contacts
├── NEXT_ACTIONS_QUEUE.md                    — live operational queue
├── REPOSITORY_COLLABORATION_GUIDE.md        — how TERA, Marketing, and Compliance use this repo
├── PROJECT_SOURCE_INDEX.md                  — full document index
├── STRATEGY/                                — strategic source-document summaries
├── ARCHITECTURE/                            — five-layer system architecture and system maps
├── MEETING_NOTES/                           — leadership and Pilot Leader meeting recaps
├── EXECUTIVE_DECKS/                         — leadership deck and briefing references
├── WORKFLOWS/                               — onboarding, publishing, compliance, sync workflows
├── AUTOMATIONS/                             — light-automation requests and queue
├── MARKETING_SYSTEMS/                       — kit, templates, brand sync, persona content guidance
├── TEAM_LEADER_PROGRAM/                     — group profiles, scorecards, candidates
├── FORMS_AND_ONBOARDING/                    — intake forms, onboarding checklists, master records
├── LANGUAGE_DIVISIONS/                      — Chinese, Vietnamese, Russian, Spanish, Korean, Latino, Veteran, Investor
├── REPORTING_AND_TRACKING/                  — launch tracking framework and KPI rollups
├── TERA_AND_TECH_REQUIREMENTS/              — ALLY stack, persona integration, TERA stack alignment
├── PROMPTS/                                 — content drafting prompts for AI consumers
└── ARCHIVE/                                 — superseded docs preserved for reference
```

## 10. Current priority questions

| Audience | Top question |
| --- | --- |
| Thanh and Dat (TERA / ALLY) | Does ALLY support group-level publishing accounts and can "Enhance Caption with AI" use LO persona context? |
| TERA leadership | Where should the approved LO Persona Profile live long term, and can it be keyed off Loan Factory SSO? |
| Marketing | Which platform powers the Loan Factory newsletter and Email Drip, and who owns the website CMS for team and LO pages? |
| Compliance | Can compliance pre-approve template categories so language-group content does not require per-piece review, and is bilingual review staffed for Chinese, Vietnamese, Russian, Spanish, Korean, and Latino? |
| Leadership | What is the primary success measure for year one — recruiting, retention, production, or all three — and what activation authority belongs to whom? |

Full question lists by audience live in `STRATEGY/ai_boardroom_architecture_readout_summary.md`, `TERA_AND_TECH_REQUIREMENTS/ally_stack_and_integration_requirements.md`, `TERA_AND_TECH_REQUIREMENTS/lo_persona_profile_ally_integration_requirements.md`, and `NEXT_ACTIONS_QUEUE.md`.

## 11. Next action path

1. Confirm Marketing pod and TERA pod first-wave capacity
2. Send the ALLY architecture question set to Thanh and Dat
3. Confirm newsletter, Email Drip, and website CMS owners with Marketing
4. Confirm Compliance pod lead and bilingual reviewer pool
5. Stand up the master group record in Google Sheets
6. Finalize and publish the Google Form intake
7. Approve the team kit v1 at the template level with Compliance
8. Onboard the first language group (Spanish recommended) end to end as the Wave 1 proof point
9. Hold the first Pilot Team Leader meeting (~June 5)
10. Begin LO Persona Profile review for early-volunteer LOs in parallel; no June 1 dependency

Live ownership and dates are in `NEXT_ACTIONS_QUEUE.md`.

## 12. Governance and compliance reminder

Every published asset under any group brand carries Loan Factory's compliance posture. Template-level compliance review is required before any group-branded content goes live on any channel. Required disclosures (NMLS, EHL, state-specific marketing rules, trigger-term rules, and the $2,000 Best Price Guarantee where promoted) are baked into approved templates so they are never an afterthought. Persona influences voice; compliance enforces structure and disclosures; human review is required on every piece. Nothing autopublishes, and no group goes live on a channel until its compliance review is signed off.

This is a pilot. It is a learning loop. It is collaborative, not punitive. Fewer groups done well beats more groups done sloppy.

## Repository

https://github.com/jeremymac904/1-plus-1-plus-1-equals-5-Loan-Factory-Project
