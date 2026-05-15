# TERA Stack Alignment Questions

**Owner:** Jeremy McDonald
**Audience:** TERA leadership (via Tara) + Khai + Thanh
**Status:** Open, awaiting TERA response
**Purpose:** Get explicit stack guidance so any technical build for 1+1+1=5 aligns with TERA's current architecture before deeper development begins.

## Why this doc exists

Thuan asked whether Jeremy should work independently, work with TERA on features for company projects like National Teams, or use Google Sheets for now. Working answer for June 1... use Google Sheets and existing systems first. In parallel, get TERA's stack guidance so any later technical build slots into TERA's stack cleanly.

Jeremy keeps moving on docs, workflows, intake form, and planning while these answers come back.

## Questions for TERA

### Frontend

- What frontend framework does TERA standardize on? (React, Next.js, Vue, other)
- What component library or design system should be used? (shadcn, MUI, Tailwind only, internal Loan Factory system)
- Are there existing TERA UI components Jeremy should reuse rather than rebuild?
- Static site, server-rendered, or SPA preference?

### Backend

- What backend framework does TERA standardize on? (Node, Fastify, Next.js API routes, Python, other)
- What language(s) are preferred?
- Are there shared backend services or APIs the program should plug into?
- Is there an existing TERA monorepo or service mesh structure?

### Database

- What database does TERA use for new projects? (Postgres, MySQL, Firebase, Supabase, other)
- Is there a shared schema or org-scoping pattern (e.g., RLS in Supabase)?
- Where should program data live... TERA-managed DB, separate DB, Google Sheets exported later?
- Any data retention or PII rules to know?

### Authentication

- How does TERA handle auth? (Supabase Auth, Firebase Auth, Auth0, internal SSO, Google Workspace SSO)
- Should program-related apps inherit Loan Factory SSO?
- Role-based access control... what model does TERA use?

### Hosting and deployment

- Where does TERA host new projects? (Vercel, Netlify, AWS, GCP, Loan Factory-owned)
- Preferred CI/CD pipeline?
- Any approved domains for internal apps?
- Environment management (dev, staging, prod) standards?

### Firebase usage

- Is Firebase part of TERA's current stack?
- If yes, what services are in active use (Auth, Firestore, Storage, Functions, Hosting)?
- If no, is there a roadmap consideration that might shift toward or away from Firebase?
- Should the program avoid Firebase if TERA is moving away from it?

### GitHub repo standards

- What is TERA's preferred repo structure? (monorepo, polyrepo, naming conventions)
- Branching model? (main only, gitflow, trunk-based)
- PR review requirements?
- CODEOWNERS expectations?
- Required CI checks?
- Any secrets management standards (Doppler, AWS Secrets Manager, GitHub Actions secrets)?

### Preferred folder structure

- For a documentation repo like 1+1+1=5, any preferred folder structure to mirror TERA conventions?
- For a future code repo aligned with TERA, what scaffold should we use?

### Claude Code usage

- Is TERA using Claude Code in any project?
- Any preferred Claude Code workflow, plugin set, or agent definitions?
- Should Jeremy share Claude skills, agents, and MCP configurations with TERA?
- Any internal tooling Jeremy should know about?

### API standards

- REST, GraphQL, or RPC preference?
- API versioning convention?
- Request and response envelope standards?
- Auth header standards?
- Rate limiting and idempotency standards?

### Reporting data sources

- Where does TERA expose reporting for Ally, portal (Email Campaign, Email Drip, IQ), GBP, and CRM?
- Are there existing dashboards or APIs the program should pull from?
- Any plans to consolidate reporting under a single TERA-managed surface?

### What TERA wants Jeremy to avoid building independently

- Anything Jeremy should not touch because TERA is already building or planning it?
- Anything Jeremy should not stand up in Google Sheets because it conflicts with a planned TERA system?
- Any custom forms, intake systems, or trackers TERA wants centralized?

### What TERA is comfortable with Jeremy building independently

- Documentation in markdown, in this repo. Confirm OK.
- Google Forms for intake. Confirm OK or suggest alternative.
- Google Sheets for launch tracking. Confirm OK or suggest alternative.
- Lightweight prompts, checklists, workflows. Confirm OK.
- Anything else green-lit for Jeremy to own without TERA review?

## What we need

A short written reply covering the questions above. Bullet answers are fine. We are not looking for a 20-page architecture doc. We are looking for clarity so the program doesn't end up rebuilding something TERA already plans to ship.

## Timeline

- Initial questions sent: May 15, 2026
- Target reply: May 22, 2026
- Stack alignment doc finalized in repo: May 27, 2026
- Phase 2 technical build planning (post-launch): begins August 30, 2026

## Cross-references

- `PROJECT_DECISIONS_AND_CONTEXT.md` D24, D25
- `NEXT_ACTIONS_QUEUE.md` A16, A17
- `REPORTING_AND_TRACKING/google_sheets_launch_tracking_framework.md`
