# AI / CS Research Engineer Curriculum — Executable Architecture v1.4

This directory mirrors the public, source-safe, version-controlled parts of the user's long-term AI/CS research-engineering curriculum. The complete 153-course workbook and polished PDF remain canonical Drive artifacts; GitHub carries the engineering methodology, policies, REA templates, course mirrors and release controls.

## Architecture

The curriculum is now a **knowledge library plus execution paths**, not one mandatory 153-course linear sequence.

- **Tier 1 — Applied AI / KSP Engineer:** fast path to Linux/Python/platform/security/ML/RAG/agents/MCP/KSP capability.
- **Tier 2 — ML / AI Systems Engineer:** model training, GPU/inference systems, post-training, distillation and selected specialist bundles.
- **Tier 3 — Research Engineer:** advanced theory, paper reproduction, ablation-driven research and independent laboratory practice.

See `v1.4-executable-architecture.md` for the complete policy.

## Mastery

**Build → Break → Diagnose → REA/Reconstruct → Benchmark → Improve → Defend.**

REA means **Reverse Engineering & Analysis**. Every course ends in evidence. AI coding/research assistants are allowed, but the learner must demonstrate system/code ownership, independent evaluation, debugging ability and the ability to identify incorrect AI output.

Prerequisites are typed as **HARD, SOFT, JIT or ENRICHMENT**. Only HARD edges block course entry. See `prerequisite-policy-v1.4.md`.

## Key files

- `v1.4-executable-architecture.md` — current execution/tier architecture.
- `prerequisite-policy-v1.4.md` — typed prerequisite semantics and applied-path examples.
- `distillation-niche-track.md` — multi-source knowledge-distillation and small specialist-model track.
- `mastery-standard.md` — evidence required before a course is marked mastered.
- `osint-source-index.md` — curated starting sources across the curriculum.
- `rea-integration.md` / `rea-course-template.md` — cross-cutting reverse-engineering requirements.
- `courses/` — course-level version-controlled curriculum material.
- `tooling/` — tooling/readiness documentation.

## Resource policy

Prefer, in order:
1. official university courses and labs;
2. canonical papers and authors' repositories;
3. official open-source project documentation;
4. established training organizations;
5. high-quality paid material as a structured supplement;
6. community tutorials only when independently validated.

Research discovery must not depend on a single aggregator. Use maintained official sources, Hugging Face evaluation/leaderboard resources, arXiv, OpenReview, ReScience C and authors' source repositories as appropriate.

All fast-moving resources must be re-reviewed before use. The branch includes `.github/workflows/ai-curriculum-links.yml` as an automated Markdown link-check release gate.

## Repository boundary

This branch does **not** contain private Drive curriculum files, proprietary courseware, licensed textbooks, credentials or private user data. It mirrors only public/source-safe curriculum logic and reproducibility controls.
