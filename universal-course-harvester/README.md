# Universal Course Harvester

**Design baseline:** v2.0 autonomous versioned library, extended by v2.1 OSINT/REA design.
**Status:** Project workspace initialized. The desktop application and update worker have not been implemented or deployed.

Universal Course Harvester is a proposed local-first Windows application for discovering, collecting, organizing, studying, and preserving permitted educational resources for any subject. A curriculum is an importable Course Pack, not hard-coded application content.

## Start here

- [Architecture and preservation contract](docs/ARCHITECTURE.md)
- [Implementation backlog and acceptance gates](docs/BACKLOG.md)
- [Agent/developer working rules](AGENTS.md)
- [Existing open-source REA shortlist](https://github.com/ekow74/labs/blob/b3ea22618434bec70e31ef844c1103092cc0a02b/ai-research-engineer-curriculum/harvester/rea/2026-10-30-v1/reuse-plan.md)

## Project location

Repository: `ekow74/labs`
Branch: `project/universal-course-harvester`
Directory: `universal-course-harvester/`

This is a dedicated project directory and branch inside an existing repository, not a new standalone repository or a native GitHub Projects board. Issues were disabled when setup was attempted; the versioned backlog is the current task tracker. The default branch is not changed by this setup.

## Product scope

- Import courses from structured manifests, curriculum exports, syllabus documents, and manually supplied URLs.
- Discover relevant official courses, papers, repositories, datasets, and skill challenges with recorded provenance.
- Download permitted resources through replaceable adapters: aria2, optional user-installed IDM, Git snapshot capture, and approved provider APIs.
- Keep every managed artifact version; archive hides an item from the default view without deleting it.
- Use AI for candidate discovery, extraction, and comparison; deterministic policy remains the authority for side effects.
- Generate separate, clickable PDF editions that refer to stable course identifiers and the live catalog.
- Track setup readiness, learning progress, REA evidence, and mastery challenges separately from changing resource content.
- Support copy-only off-device backups and tested restoration.

## Preservation invariant

**No autonomous deletion or overwrite of managed learning materials, imports, manifests, evidence, or generated handbooks.** New bytes produce a new version. Rollback changes which revision is active; it does not remove another revision. Low storage pauses acquisition.

## Public repository boundary

Only public-safe source code, specifications, synthetic fixtures, and third-party source references belong here. Do not commit downloaded courseware, private study records, medication/patient data, credentials, cookies, signed URLs, personal Drive identifiers, or model-provider secrets. The public project may reference third-party repositories without copying their code; dependency licensing must be reviewed before redistribution.

## First deliverable

An offline-tested vertical slice: synthetic course manifest → permission decision → local fixture download → verified immutable artifact → second distinct version → restart → backup/restore → both original versions still readable.

The backlog contains acceptance criteria. An unchecked item is not implemented. No automated spending, production deployment, Claude submission, or background monitoring is activated by this workspace.
