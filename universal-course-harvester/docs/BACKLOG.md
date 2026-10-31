# Implementation backlog

Status: all implementation items below are NOT STARTED. These checkboxes are the project tracker because Issues are disabled in the host repository. A checked item requires linked reproducible evidence; documentation alone does not prove implementation.

## UCH-001 — Course contract and registry

- [ ] Publish an extensible versioned course-manifest JSON Schema and synthetic example packs.
- [ ] Implement schema/semantic validation, stable UUIDs, safe path mapping, typed prerequisites, and migration rules.
- [ ] Implement SQLite registry, append-only revision events, and import/export.

Acceptance: a course from an unrelated subject imports without changing application code; renaming it preserves identity/history; malformed and privilege-escalating manifests are rejected; migrations preserve original manifest bytes. Document unknown-extension behavior. Validate UUID/date formats explicitly rather than assuming every JSON Schema library enforces formats.

## UCH-002 — Immutable artifact store and recovery

Depends on UCH-001.

- [ ] Implement fresh staging paths, hash verification, no-clobber object publication, resource-version records, and reversible active pointers.
- [ ] Enforce service-level authority separation: downloader and AI cannot modify published storage.
- [ ] Implement crash recovery and disk-capacity refusal.

Acceptance: two different versions both survive restart/restore; unchanged bytes retain distinct observations without destructive deduplication; traversal and collision attempts fail; interrupted publication cannot mark incomplete bytes as complete. No deletion/overwrite is exposed through the agent interface. Test backup independence and document limits of OS-level protection.

## UCH-003 — Download queue and adapters

Depends on UCH-002.

- [ ] Implement durable jobs, leases, restart recovery, retries, rate limits, quotas, and audit events.
- [ ] Add a controlled direct/aria2 adapter, then optional user-installed IDM integration.
- [ ] Add permission-aware provider and Git snapshot interfaces without assuming every website has a reusable download endpoint.

Acceptance: interrupted downloads resume where the source supports it; credentials stay out of logs; 401/403/429 produce the right states rather than access-control bypass; invalid file types, redirects to private network targets, oversized responses, and directory escapes are blocked; no adapter overwrites a managed version.

## UCH-004 — Educational OSINT and extraction

Depends on UCH-001; acquisition requires UCH-003.

- [ ] Define connector contracts for discovery, provenance, rights evidence, extraction, and update observation.
- [ ] REA and benchmark Scrapy, Playwright, trafilatura, Docling, and scholarly-metadata candidates.
- [ ] Add course-specific relevance and duplicate detection using official sources first.

Acceptance: distinguish authors' implementations from unrelated forks; recover source citations; separate free-to-read, download, redistribution, and training-use permissions; unknown permissions stay link-only. Website content cannot change permissions or execute tools. Record source commit/license and measured results before adopting a component.

## UCH-005 — Autonomous update manager

Depends on UCH-002 through UCH-004.

- [ ] Implement staged AI proposals, deterministic policy decisions, held-out evaluation, review queue, and audit trace.
- [ ] Add daily/weekly/monthly jobs and 12-week review checkpoints with missed-run coalescing.
- [ ] Add configurable storage, bandwidth, API/model, and concurrency limits; default paid-model spending is zero.

Acceptance: duplicates and restarts do not create duplicate published versions; major syllabus/assessment changes and clinically sensitive changes cannot self-approve; adversarial source instructions cannot bypass policy; paused jobs retain history; no automatic paid service purchase or deletion occurs. Every change records evidence and model/policy revisions.

## UCH-006 — Windows interface and clickable PDFs

Depends on UCH-001 through UCH-003; AI updates are separately gated.

- [ ] Build course import/catalog, per-course acquisition, history browsing, progress, REA evidence, and error views.
- [ ] Implement validated app deep links and fallback navigation.
- [ ] Generate a new immutable PDF edition from a pinned catalog revision.

Acceptance: an older handbook still resolves stable course IDs; newly added courses appear in the live catalog; malformed links cannot run commands or choose arbitrary filesystem paths; PDF generation preserves all earlier editions, annotations, and progress. Verify on a Windows test environment, not only a Linux build runner.

## UCH-007 — Backup, packaging, and pilot qualification

Depends on UCH-002 and UCH-006.

- [ ] Implement copy-only snapshots to an independent destination, initially through a restricted adapter.
- [ ] Add content verification, database-consistent backups, and restore drill documentation.
- [ ] Package a Windows installer with explicit permissions and dependency/license inventory.
- [ ] Pilot a small mixed-subject/course fixture set before enabling a large catalog.

Acceptance: restoration on a fresh location recovers every original artifact/version and course association; no sync-delete/move/prune command is reachable through the autonomous interface; low space pauses work; uninstall and upgrade do not delete the library. Report actual runtime results and unresolved failures.

## Delivery rules

Preserve existing user materials and prior revisions. Use a narrow implementation branch and reviewable changes. Record exact test commands, environment, revision, expected output, actual output, and remaining limitations. Do not change a failing criterion simply to obtain a pass.

No commercial credentials, proprietary courseware, private learner data, or personal Drive identifiers belong in this public project. Do not submit this work to Claude without a new explicit instruction.

## First runnable milestone

UCH-001 + UCH-002 + a minimal UCH-003 fixture adapter: import a synthetic course, acquire a known local fixture, verify and version it, append a changed fixture, restart, and restore a backup while preserving both versions. A GUI, external web crawler, AI model, and real paid account are not required for this first test.
