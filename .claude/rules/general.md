# General Project Rules

## New Project Detection (MANDATORY)
Before starting ANY work, check if the project has been initialized. Both files are already loaded into every session through CLAUDE.md, so check them there without reading them again:
1. `docs/PRD.md` - if it still contains placeholder text like "_Describe what you are building_", the project is NOT initialized
2. `features/INDEX.md` - if the features table is empty, no features have been defined

**If the project is not initialized:**
- Do NOT write any code or create any components
- Do NOT skip ahead to implementation
- Instead, tell the user: "This project hasn't been set up yet. Let's start by defining what you want to build. Run `/init` with a description of your idea (e.g. `/init I want to build a task management app`)."
- If the user already described their idea in the current message, run `/init` automatically with their description

**If the project is initialized but the user requests a feature not yet in INDEX.md:**
- Guide them to run `/write-spec` first to create the feature spec before any implementation

## Feature Tracking
- All features are tracked in `features/INDEX.md`
- Feature specs live in `features/PROJ-X-feature-name.md`
- Feature IDs are sequential: check INDEX.md for the next available number
- One feature per spec file (Single Responsibility)
- Never combine multiple independent functionalities in one spec

## Git Conventions
- Commit format: `type(PROJ-X): description`
- Types: feat, fix, refactor, test, docs, deploy, chore
- Check existing features before creating new ones: `ls features/ | grep PROJ-`
- Check existing components before building: `git ls-files src/components/`
- Check existing APIs before building: `git ls-files src/app/api/`

## Human-in-the-Loop
- Always ask for user approval before finalizing deliverables
- Present options using clear choices rather than open-ended questions
- Never proceed to the next workflow phase without user confirmation

## Status Updates (MANDATORY)
After completing work on any feature, update the tracking files with the Edit tool before you report the work as done. Describing an update in chat does not replace writing it to the file. A successful Edit call is the confirmation; do not re-read the file afterwards.

**What to update in the feature spec:**
- Status field in the header (same value as in `features/INDEX.md`)
- Implementation notes: what was built, what changed, any deviations from the original spec
- Bug fixes or design changes discovered during implementation

**What to update in `features/INDEX.md`:**
- Feature status column must match the feature spec header
- Valid statuses: Roadmap → Planned → Architected → In Progress → In Review → Approved → Deployed
  - **Roadmap**: after `/init` — feature identified, no spec file yet
  - **Planned**: after `/write-spec`
  - **Architected**: after `/architecture`
  - **In Progress**: after `/frontend` or `/backend` starts
  - **In Review**: after `/qa` starts
  - **Approved**: after `/qa` passes (no critical/high bugs)
  - **Deployed**: after `/deploy`

## File Handling
- ALWAYS read a file before modifying it - never assume contents from memory
- After context compaction, re-read the files you are working on and run `git diff` to see what has already been changed
- When unsure about current project state, read `features/INDEX.md` first
- Never guess at import paths, component names, or API routes - verify by reading

## Handoffs Between Skills
- After completing a skill, suggest the next skill to the user
- Format: "Next step: Run `/skillname` to [action]"
- Handoffs are always user-initiated, never automatic
