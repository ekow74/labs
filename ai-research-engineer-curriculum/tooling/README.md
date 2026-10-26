# Course Tooling Layer v1.2

The curriculum now assigns tools to **all 153 courses** using three tiers:

- **Required** — install at the start of the course and use in labs/REA/mastery work.
- **Recommended** — install when the syllabus first calls for it.
- **Advanced / Optional** — install only for specialist, performance, or extension work.

The canonical detailed mapping is maintained in the Drive workbook `04_COMPLETE_AI_CS_RESEARCH_ENGINEER_STUDY_PLAN_v1.2_TOOLING.xlsx`, which adds:

1. `Course Tooling` — one row per course with required/recommended/optional tools, environment, mastery use, install timing, and safety notes.
2. `Tool Registry` — de-duplicated tools with official URLs, purpose, cost/license, first course, and every course that uses the tool.
3. `Course Catalog` columns for Required Tools, Recommended Tools, and Advanced/Optional Tools.

## Examples

- **FND-001 Computing Fundamentals**: Windows 11, PowerShell 7, Windows Terminal, VS Code, curl, GitHub; recommended draw.io, Wireshark, WSL2.
- **FND-002 Linux Command Line & Shell**: Windows Terminal, WSL2, Ubuntu 24.04 LTS, Git, VS Code; recommended PowerShell, curl, jq, strace; optional tmux, bpftrace, Docker.
- **CS-230 Operating Systems**: Ubuntu/WSL, GCC/Clang, GDB, xv6, QEMU; recommended strace/ltrace/perf and sanitizers.
- **OPS-380 Advanced Kubernetes / Helm / GitOps**: Kubernetes, kubectl, kind, Helm, Argo CD, GitHub Actions; recommended k9s, OPA/Rego, Kyverno, Prometheus.
- **AI-842 Model Distillation**: Hugging Face TRL, DistillKit, Microsoft LMOps/MiniLLM, NVIDIA Model Optimizer, LLM Compressor, PyTorch; recommended Transformers, vLLM, W&B, bitsandbytes.
- **AI-860 Niche AI Systems Engineering**: Transformers, Datasets, PEFT, TRL, DistillKit, Qdrant, lm-evaluation-harness; recommended Model Optimizer, LLM Compressor, vLLM, BGE/FlagEmbedding, MLflow.
- **AISEC-1030 Agent/MCP Security**: PyRIT, garak, Promptfoo, Inspect AI, OWASP GenAI, MCP SDK, MCP Inspector, OPA/Rego; security testing restricted to owned/authorized labs.

## Policy

Tools are included only when they support a lab, REA exercise, benchmark, deployment, evaluation, or mastery artifact. Do not install the entire registry at once. Security/offensive tools are limited to localhost, CTFs, deliberately vulnerable environments, or systems the learner owns or has explicit permission to test.
