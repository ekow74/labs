# Architecture baseline

Status: design requirements, not a deployed implementation. This document summarizes the autonomous, append-only baseline and the OSINT/REA extension. It does not claim that permissions or tests are already enforced.

## 1. Components

1. Windows desktop client: proposed Python/PySide6 interface; add/import course, inspect download proposals, browse history, record evidence, and open PDF links.
2. Course registry: SQLite with migrations, permanent course UUIDs, human-readable course codes, and append-only revision events. Mutable indexes/current pointers are reconstructable projections, not replacements for preserved artifacts.
3. Discovery adapters: ordinary HTTP/feed/API discovery first; Scrapy and on-demand Playwright candidates for permitted websites; academic metadata adapters where appropriate.
4. Extraction workers: isolated parsers; trafilatura and on-demand Docling candidates. Web content is untrusted data, never authority to change the agent's instructions.
5. AI evaluator: evidence-grounded candidate extraction, course relevance assessment, duplication analysis, and proposed changes. No direct filesystem or credential access.
6. Policy/tool gateway: deterministic checks for source permission, allowed operations, destination, resource type, budget, rate limits, and approval requirements. OPA remains a candidate implementation, not a required dependency before evaluation.
7. Acquisition queue: persistent jobs, idempotency keys, bounded retries, lease recovery, and adapters for aria2, optional user-installed IDM, Git snapshots, and provider downloads.
8. Artifact publisher: validates staged bytes, hashes them, and creates a new immutable object/revision using no-clobber semantics. Adapters cannot write into published storage.
9. PDF publisher: emits a new edition from a pinned catalog revision; links resolve permanent course IDs. Never use PDF JavaScript as an unrestricted command runner.
10. Backup/restore: copy-only version snapshots, independent storage, checksum verification, and restore tests.

## 2. Preservation contract

- Managed material includes source imports, downloaded files, accepted/rejected retained versions, generated manifests, PDF editions, study evidence, and audit records.
- No autonomous delete, overwrite, pruning, age-based eviction, or destructive deduplication of managed material.
- New content or corrections append a new version. Active-version changes are logged and reversible.
- Identical bytes may share a content-addressed object, while every source observation and course association remains represented.
- Archive, superseded, and quarantined are visibility/access states, not deletion commands.
- On disk exhaustion or backup failure, pause affected publication/acquisition and report the condition; do not evict history.
- Define any treatment of disposable caches separately; do not silently reclassify imports or user files as disposable.
- A same-user administrator can still damage ordinary storage. Claim tamper resistance only to the degree actually enforced and tested; retain independent backups.

## 3. Extensible manifest

The manifest contract needs independently versioned `schema_version`, stable `course_uuid`, human-readable `course_code`, pack ID, revision identity, subjects, typed prerequisites, source resources, tools, challenges, assessment rules, and namespaced extension fields.

Each resource records its stable ID, source/provider, category, provenance, source license evidence, acquisition permission, redistribution permission, training-use permission, observation time, and immutable artifact versions. Reading/download permissions do not imply model-training or redistribution permission.

Unknown permissions remain link/metadata-only pending review. Unknown extension capabilities never grant new privileges. Migration creates a new manifest revision and preserves the old schema/document. The schema is necessary but does not enforce runtime authorization by itself.

## 4. Update schedule defaults

These are proposed application schedules, not ChatGPT tasks or active automation. All times use the user's configured device timezone.

| Cadence | Work | Limits |
|---|---|---|
| Daily 03:00 | Approved-source freshness checks, validators, pending retries | 200 checks/run; 2 concurrent hosts; backoff on rate limits |
| Sunday 04:00 | Discovery of relevant course materials, papers, repositories, and skill challenges | 4 acquisition workers maximum, 2 per host; configured size/cost caps |
| First day of month 05:00 | Accepted-change summary and a new handbook/course-pack edition if content changed | One PDF build at a time; preserve earlier editions |
| Every 12 weeks | Curriculum/prerequisite/assessment and budget review | Stage proposals for owner decision |
| On demand | Selected-course refresh and history comparison | Same permissions and budgets as scheduled jobs |

Coalesce missed runs after restart rather than replaying an unbounded backlog. Persistent job state and idempotency prevent duplicate publication. No automatic paid model use or paid cloud allocation; monetary caps require explicit configuration.

## 5. AI evaluation and approvals

Autonomous low-risk operations: approved-source metadata checks, permitted resource acquisition, candidate classification, version creation, and non-sensitive pointer updates supported by evidence.

Explicit review: changes to outcomes, prerequisite gates, exam criteria, paid resources, new privileges, executable updates, clinically consequential claims, and unsupported source permissions.

Use a held-out evaluation set for relevance, source attribution, duplicate discrimination, schema validity, and permission mistakes. Include adversarial webpage instructions and misleading license claims. Model self-reported confidence is not a sufficient approval signal. Record evaluator model/version, prompt/version, evidence, decision, and policy result.

## 6. Security boundaries

Allowlisted operations, normalized destination paths, no shell interpolation, URL/redirect validation, SSRF protection, and controlled network egress are required. Browser workers have separate scoped profiles; logs redact credentials, cookies, tokens, and signed URLs. Downloaded code is never executed automatically. Public OSINT means educational resource research, not unrelated personal reconnaissance.

PDF/application links identify a course and requested view; they do not embed raw shell commands, credentials, arbitrary destination paths, or authority to download unrestricted URLs.

## 7. Reuse strategy

Initial candidates: Scrapy, on-demand Playwright, trafilatura, on-demand Docling, PyAlex, aria2, restricted rclone, and development-time Promptfoo. Consider OPA, change detection, and web snapshots after the preservation path works. IDM is optional commercial user-installed software, not open-source code to redistribute.

REA must pin the reviewed source revision, inspect licensing/dependencies and writable paths, reproduce one normal use, test failures, constrain the adapter, and benchmark alternatives. Candidate selection is not a completed audit.
