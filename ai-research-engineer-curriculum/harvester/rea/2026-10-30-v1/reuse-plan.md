# Universal Course Harvester — open-source REA shortlist

Compiled: 2026-10-30. Research/design only: no implementation, runtime benchmark or security certification is claimed. This is a public-source-safe summary; no private courseware or user data is included. No Claude review submission is requested.

## Decision

Prefer stable libraries and restricted adapters over copying whole applications. The initial stack is Scrapy, on-demand Playwright, trafilatura, on-demand Docling, PyAlex, aria2, rclone and Promptfoo for development-time evaluation. Deterministic policy tests are required from the start; OPA is a policy-engine candidate. Add change detection and web snapshots after the immutable publication path is proven. IDM remains an optional user-installed commercial backend through its official API, not an open-source component.

## Repository candidates

| Repository | License observation | Proposed role / boundary |
|---|---|---|
| [scrapy/scrapy](https://github.com/scrapy/scrapy) | BSD-3-Clause | Controlled website crawling; inspect scheduler, duplicate filtering, persistent jobs and throttling. |
| [microsoft/playwright-python](https://github.com/microsoft/playwright-python) | Apache-2.0 | Restricted on-demand browser rendering; inspect navigation, isolation and download lifecycle. |
| [adbar/trafilatura](https://github.com/adbar/trafilatura) | Apache-2.0 | Main-text and metadata extraction; test boilerplate removal and loss of instructional material. |
| [docling-project/docling](https://github.com/docling-project/docling) | MIT code; models/dependencies separately | Isolated document conversion with source-location provenance; text first, OCR only when needed. |
| [J535D165/pyalex](https://github.com/J535D165/pyalex) | MIT | Scholarly discovery adapter; API access, quotas and full-text rights are separate. |
| [aria2/aria2](https://github.com/aria2/aria2) | GPL family; verify selected distribution | Separate constrained download process; inspect retries, resume, destination control and RPC. |
| [rclone/rclone](https://github.com/rclone/rclone) | MIT | Versioned backup copy adapter; never expose arbitrary command execution. |
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | MIT core | Development/CI regression tests for relevance, attribution and injected instructions. |
| [open-policy-agent/opa](https://github.com/open-policy-agent/opa) | Apache-2.0 | Deterministic authorization rules; the broker/OS must actually enforce decisions. |
| [dgtlmoon/changedetection.io](https://github.com/dgtlmoon/changedetection.io) | Apache-2.0 | Phase-2 known-source monitoring; not the permanent artifact store. |
| [ArchiveBox/ArchiveBox](https://github.com/ArchiveBox/ArchiveBox/) | MIT core; dependencies separately | Phase-2 permitted web snapshots; keep capture storage separate from accepted versions. |
| [searxng/searxng](https://github.com/searxng/searxng) | AGPL-3.0 family | Optional metasearch service; no guarantee of unrestricted upstream access. |
| [unclecode/crawl4ai](https://github.com/unclecode/crawl4ai) | Apache-2.0 text plus appended Attribution Requirement | Alternative extraction adapter; benchmark against the core stack, not a second mandatory crawler. |
| [webrecorder/browsertrix-crawler](https://github.com/webrecorder/browsertrix-crawler) | AGPL-3.0 family | Optional high-fidelity browser archive worker, not always-on infrastructure. |
| [yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) | Unlicense source; some bundles GPLv3+ | Optional permitted-media downloads; no access-control/DRM bypass or execution hooks. |
| [restic/restic](https://github.com/restic/restic) | BSD-2-Clause | Optional encrypted snapshot backup; no autonomous forget/prune/retention expiry. |
| [smicallef/spiderfoot](https://github.com/smicallef/spiderfoot) | MIT | REA its plugin/event/provenance patterns; do not import unrelated reconnaissance or profiling. |

License observations are not redistribution clearance. Pin a release/commit and inspect LICENSE/NOTICE, dependencies, bundled binaries and any model weights before shipping. A process boundary is not a blanket exemption from GPL/AGPL duties. Free software does not imply free compute, storage or API access, nor permission to download or train on unrelated content.

## Important primary evidence

- Scrapy persistent jobs: https://docs.scrapy.org/en/master/topics/jobs.html
- Scrapy scheduler: https://docs.scrapy.org/en/latest/topics/scheduler.html
- Crawl4AI license: https://github.com/unclecode/crawl4ai/blob/main/LICENSE
- yt-dlp packaging licenses: https://github.com/yt-dlp/yt-dlp#licensing
- aria2 controls: https://aria2.github.io/manual/en/html/aria2c.html
- rclone immutable behavior: https://rclone.org/docs/
- rclone copy: https://rclone.org/commands/rclone_copy/
- restic deletion behavior: https://restic.readthedocs.io/en/stable/060_forget.html
- OpenAlex access documentation: https://help.openalex.org/
- IDM integration: https://www.internetdownloadmanager.com/support/idm_api.html

The Crawl4AI LICENSE was read in full (observed blob ade44a7824869fe57a3dfa98ad4b7ffb764c3cb0). Opening interfaces of scrapy/core/scheduler.py were inspected (observed blob 9ed5631eaf441491c57ae8f46458568cb886d534). These are file observations, not pinned whole-repository releases or completed code audits. No candidate has been installed or benchmarked in this research pass.

## No-delete / no-overwrite invariant

Accepted artifacts and prior course manifests are immutable. Only the publication service can create accepted objects; browser/parser/downloader/AI workers cannot write directly to that store. Use unique staging paths, create-only publication, content hashes and append-only revision/association records. Identical bytes can have several course references. Rollback appends a selection event and keeps later editions.

Rclone's --immutable does NOT prevent all deletion. Use a fixed allowlisted copy --immutable operation to unique version paths, not sync/move/delete/purge/cleanup/dedupe/bisync. Verify copied data and test recovery into a fresh destination. Do not enable cloud lifecycle expiry or deletion propagation. Restic forget/prune is outside autonomous authority.

Low storage pauses acquisition; it never triggers archive pruning. Quarantined content remains non-executable and hidden from normal previews. Do not disable security software to recover a file it has isolated. Application policy cannot guarantee preservation against hardware failure, administrators or independent cloud-provider action.

## Common adapter contract

Course UUID and manifest revision -> bounded research mission -> approved source collection -> extraction and evidence -> AI recommendation -> deterministic policy decision -> approved acquisition ticket -> isolated staging -> integrity/security checks -> new immutable artifact version -> course association -> versioned PDF and backup.

Discovery, download permission, redistribution permission and model-training permission are separate decisions. Unknown rights remain link-only/review. Browser redirects and resolved IPs must pass network policy; remote filenames cannot choose local paths. No arbitrary shell, personal browser credentials, fetched-code execution or provider-budget expansion is delegated to the AI.

## Proposed REA gates — not yet executed

1. Inventory: pinned repository version, licenses/notices, dependencies and security signals.
2. Architecture: interfaces, credentials, network access and all file-write/destructive operations.
3. Reproduction: minimal owned fixture with recorded environment/configuration and hashes.
4. Failures: timeouts, interruptions, source changes mid-resume, malformed documents and low space.
5. Adapter: typed requests and bounded outputs, default-deny policy, isolated writable staging.
6. Evaluation: common corpus and budgets; measure extraction fidelity, provenance, recovery, memory/runtime and cost.
7. Decision: integrate, isolate, fork with evidence, defer or reject.

Pilot course types: computing foundations, Linux, mathematics, distillation and pharmacology. Keep medical work at source/evidence collection until appropriate review; do not automatically certify drug facts or publish clinical training truth.

Pilot tests must include duplicate URLs, redirect loops, changed editions, unknown licenses, prompt injection, archive path traversal, disk-full behavior, restart/resume, identical files referenced by different courses, backup collision and restore. Report proposed tests as proposed until real execution evidence exists.

## Scope remaining

Build our own universal course registry, stable UUID routing, manifest migrations, evidence graph, rights ledger, immutable publisher, user interface, examiner/progress state, bounded scheduler and PDF generator. The shortlist reduces infrastructure work; it is not an already running Course Harvester.
