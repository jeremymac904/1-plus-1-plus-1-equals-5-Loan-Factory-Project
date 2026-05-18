# ALLY Stack and Integration Requirements

**Owner:** Jeremy McDonald
**Audience:** TERA leadership (via Tara), Khai, Thanh, Marketing pod lead, Compliance lead, Thuan, Dat
**Status:** Discovery in progress, awaiting TERA confirmation
**Last updated:** 2026-05-18
**Purpose:** Document what is known and what still needs confirmation about ALLY so it can be slotted correctly inside the larger Loan Factory team marketing system.

## Framing — ALLY is one layer, not the whole program

ALLY is the **social and campaign execution layer** for the 1+1+1=5 Team Marketing Enhancement Program. It is not the whole marketing program. The full system also has to coordinate:

- Intake (Google Form → master team marketing record)
- Branding and team kits (Marketing pod)
- Loan Factory website team pages and LO landing pages (TERA + Marketing)
- Loan Factory portal newsletters (TERA)
- Loan Factory portal Email Drip campaigns (TERA)
- Google Business Profile workflows (TERA + Marketing)
- Realtor outreach templates (Marketing)
- Compliance review templates (Compliance, template-level per D9)
- Marketing pod production workflow (Marketing)
- TERA technical setup workflow (TERA)
- Reporting and tracking dashboards (Marketing + TERA)

ALLY plugs into this system. It does not replace it. Documentation should treat ALLY as the social and campaign execution surface inside a larger coordinated stack.

## What we are trying to learn

For each layer below we capture two things... what we currently believe (Known / Assumed) and what we still need TERA, Dat, or Marketing to confirm (Open). Anything unconfirmed gets flagged and added to `NEXT_ACTIONS_QUEUE.md`.

## 1. Front end

- **Known / Assumed:** ALLY presents a web-based dashboard for LOs and Team Leaders. Used inside browser sessions on desktop, with at least basic mobile responsiveness.
- **Open:**
  - Framework in use (React, Next.js, Vue, internal)
  - Whether there is a Loan Factory branded shell or a vendor white label
  - Whether Team Leaders see a different UI from LOs
  - Whether the UI supports team-level vs LO-level views in the same login
  - Whether there is an admin console TERA controls

## 2. Back end

- **Known / Assumed:** ALLY is a hosted product. Loan Factory consumes it. Backend is not internally owned.
- **Open:**
  - Is ALLY a third-party SaaS, a Loan Factory-built layer, or a hybrid
  - Backend framework and language
  - Whether Loan Factory has any backend extension points (functions, plug-ins, custom logic)
  - Whether content templates can be stored backend-side and reused across teams

## 3. Database

- **Open:**
  - Where account, content, schedule, and engagement data are stored
  - Whether Loan Factory has direct DB access or only API access
  - How team and LO data are structured (per-LO accounts, team accounts, parent/child accounts)
  - Data retention and PII rules
  - Whether intake data could ever be reflected into ALLY data or vice versa

## 4. Authentication

- **Known / Assumed:** LOs log into ALLY individually. SSO posture is unclear.
- **Open:**
  - SSO support (Google Workspace, Microsoft, Auth0, internal Loan Factory SSO)
  - Whether Loan Factory portal credentials extend to ALLY
  - Multi-factor enforcement
  - How a Team Leader gains scoped access over a team of LOs

## 5. Hosting

- **Open:**
  - Whether ALLY is vendor-hosted, hosted on Loan Factory infrastructure, or hybrid
  - Region and uptime expectations
  - Any Loan Factory-owned subdomain in use

## 6. Repository structure

- **Open:**
  - Whether there is a Loan Factory-controlled repo that customizes or extends ALLY
  - Whether TERA owns any code that talks to ALLY (sync jobs, importers, webhooks)
  - If yes, where the repo lives and what branching model is used

## 7. Workflow architecture

- **Known / Assumed:** Content flows roughly draft → review → schedule → publish per channel.
- **Open:**
  - Exact workflow states (draft, in review, approved, scheduled, published, failed)
  - Whether approval can be required by role (e.g., Team Leader approves LO drafts)
  - Whether a Marketing or Compliance approval gate can be inserted
  - Whether bulk actions across a team are supported
  - How content rejection and revision are handled

## 8. Admin controls

- **Open:**
  - Org-level admin console
  - Ability to suspend an LO, transfer ownership, or move an LO between teams
  - Audit log of admin actions
  - Ability to enforce required disclosures at the template level

## 9. User permissions

- **Open:**
  - Built-in roles (Admin, Team Leader, LO, Reviewer, Read-only)
  - Whether custom roles are possible
  - Whether a Marketing reviewer can be added with non-publishing permissions
  - Whether a Compliance reviewer can be added with non-publishing permissions

## 10. Team or group account support

- **Open:**
  - Whether ALLY natively supports a Team construct that owns multiple LO accounts
  - Whether a Team Leader can publish on behalf of an LO
  - Whether content can be authored at the team level and pushed to each LO's channels
  - Whether content authored at the LO level can roll up into a team view

## 11. Content scheduling

- **Open:**
  - Channels supported (Facebook, Instagram, LinkedIn personal, LinkedIn company, YouTube, GBP, TikTok, X, Threads)
  - Whether GBP scheduling is native or pushed elsewhere
  - Recurring schedule support
  - Time zone handling for multi-state teams
  - Bulk scheduling and CSV import
  - Queue management at the team level

## 12. Social channel integrations

- **Open:**
  - Native integrations and connection method (OAuth, page tokens, business manager)
  - Re-auth cadence
  - Whether each LO connects their own channels or whether the team connects centrally
  - Whether Meta Business Suite, LinkedIn Page Admin, or YouTube Studio access is required
  - Known limitations per channel (e.g., reels, carousels, GBP photo size)

## 13. Analytics and reporting

- **Open:**
  - Native metrics (impressions, engagement, clicks, follower growth)
  - Whether metrics roll up at team and division levels, not just LO level
  - Whether reports can be exported (CSV, scheduled email, API)
  - Whether ALLY data can feed a unified Loan Factory reporting dashboard
  - Whether UTM tagging is automatic, manual, or unsupported

## 14. API or webhook availability

- **Open:**
  - Public API or developer documentation
  - Auth model (API key, OAuth, service account)
  - Webhook events available (publish, fail, engagement threshold)
  - Rate limits
  - Whether TERA can ingest webhooks into the portal or a TERA service

## 15. How ALLY currently connects to other Loan Factory systems

- **Known / Assumed:** Today the connection is mostly manual. LOs log into ALLY, draft content, schedule, and publish. There is no documented automated bridge to:
  - Loan Factory website team pages
  - Loan Factory portal newsletters
  - Loan Factory portal Email Drip
  - GBP workflows
  - Realtor outreach
  - Compliance review
  - Reporting dashboards
- **Open:**
  - Confirm whether any of these bridges exist today
  - Confirm whether TERA has any existing sync jobs touching ALLY
  - Confirm whether there is a planned roadmap to consolidate ALLY data into the Loan Factory portal

## 16. Compliance posture inside ALLY

- **Open:**
  - Whether required disclosures (NMLS, EHL, state-specific, trigger terms, $2,000 Best Price Guarantee) can be enforced at the template level
  - Whether template-level compliance review (per D9) can be wired into ALLY
  - Whether a Compliance reviewer role can sit upstream of publish
  - Whether failed compliance content can be flagged and not auto-rescheduled

## Integration requirements for 1+1+1=5

For the program to work, ALLY must support or be wired to support:

1. **Per-team setup** triggered from the master team marketing record after intake review.
2. **Template-level compliance** matching the templates already used in newsletters, drips, GBP, and website team pages.
3. **Team Leader oversight** so a Team Leader can review and approve LO drafts before they publish.
4. **Consistent branding** drawn from the same team kit used by website, newsletter, drip, GBP, and realtor outreach.
5. **Channel coverage** that matches each team's intake selections (which channels they committed to in Section 3 of the intake form).
6. **Reportable activity** that can feed the launch tracking sheet and, later, a Marketing + TERA dashboard.

If ALLY cannot do one of these natively, document the workaround (manual step, parallel system, deferred to Phase 2) in `WORKFLOWS/team_marketing_system_sync_workflow.md`.

## Open questions for stakeholders

| # | Question | Owner | Target |
| --- | --- | --- | --- |
| Q1 | Is ALLY a third-party SaaS, internal build, or hybrid | TERA via Tara | May 22 |
| Q2 | Does ALLY support team or group accounts natively | TERA via Tara | May 22 |
| Q3 | What user roles and permissions are configurable | TERA via Tara | May 22 |
| Q4 | Is there an API or webhook surface | TERA via Tara | May 22 |
| Q5 | How does ALLY currently connect to the Loan Factory portal | TERA via Tara | May 22 |
| Q6 | Can template-level compliance review be enforced in ALLY | Compliance + TERA | May 27 |
| Q7 | Can branding from the team kit be applied at the team level | Marketing + TERA | May 27 |
| Q8 | What reporting can ALLY surface at team and division level | TERA + Marketing | May 27 |
| Q9 | Does Thuan want ALLY positioned as the social layer or a broader content hub long term | Thuan via Andre | May 29 |
| Q10 | Does Dat have any existing TERA integration work touching ALLY | Dat via Tara | May 27 |

These map into `NEXT_ACTIONS_QUEUE.md` as ALLY discovery items.

## Cross-references

- `WORKFLOWS/team_marketing_system_sync_workflow.md` — desired end-to-end sync flow
- `FORMS_AND_ONBOARDING/intake_to_marketing_system_master_record.md` — intake → master record mapping
- `MARKETING_SYSTEMS/brand_sync_requirements.md` — branding consistency across surfaces
- `TERA_AND_TECH_REQUIREMENTS/tera_stack_alignment_questions.md` — broader TERA stack questions
- `PROJECT_DECISIONS_AND_CONTEXT.md` D6, D7, D8, D9, D17
- `NEXT_ACTIONS_QUEUE.md` — live items tracking the questions above
