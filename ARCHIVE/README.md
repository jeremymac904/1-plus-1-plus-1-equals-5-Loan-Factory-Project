# ARCHIVE

Superseded documents. Kept for reference. Never deleted.

## What goes here

- Old workflow versions (when a workflow is rewritten)
- Old templates (when a template gets replaced)
- Old meeting recaps from prior cycles (optional — `MEETING_NOTES/` can hold them all)
- Decision context that's been overridden (the override goes in `PROJECT_DECISIONS_AND_CONTEXT.md`; the original moves here)
- Drafts that didn't ship

## What doesn't

- Active documents — leave them where they live
- Anything containing secrets, credentials, or PII (those get scrubbed before archiving)

## Naming

Keep the original filename. Prepend the archive date if it helps disambiguate:

- `2026-07-15_team_kit_v1_archived.md`
- `2026-08-30_workflow_v1_archived.md`

## Why archive instead of delete

- Decision trail matters
- Future "why did we change this?" questions need a record
- Team Leaders and pod members joining later need context for why current docs look the way they do

## How to archive

1. Move the file from its original location to `ARCHIVE/`
2. Add a header note at the top of the file with archive date and reason
3. Update `PROJECT_SOURCE_INDEX.md` — change Status to Archived, update the path
4. If anything links to the old path, update those links to point to the new (current) doc

## Don't fear archiving

Aggressive archiving keeps the active repo clean. If a doc isn't useful in the next 30 days, it might belong here. The repo is faster to navigate when active = current.

## Cross-references

- `PROJECT_SOURCE_INDEX.md` — full document index with status flags
