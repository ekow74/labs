# FND-001 REA Workspace

Use this workspace to collect evidence for the four REA exercises and the final mastery project.

## Required structure

```text
REA/
├── 00_target_and_scope.md
├── 01_inventory/
├── 02_architecture/
├── 03_behavior_traces/
├── 04_source_or_artifact_analysis/
├── 05_runtime_evidence/
├── 06_failure_experiments/
├── 07_reconstruction/
├── 08_benchmarks/
├── 09_security_reliability/
├── 10_ai_assistance_audit/
└── 11_final_review.md
```

## Evidence rules

- Distinguish **observed**, **documented**, and **inferred** claims.
- Record enough context that another person can reproduce the result.
- For safe failure experiments: predict first, change one thing, capture evidence, diagnose, restore, verify.
- Never probe or modify systems you do not own or have explicit authorization to test.
- Record important AI-generated claims and independently verify them.
- Preserve failed attempts when they teach something; do not rewrite history to make the project look cleaner.

## Weekly targets

### Week 1 — Process Autopsy
Inspect one benign local application and map user action → app → OS → hardware/resources.

### Week 2 — Web Request / Safe Failures
Trace an authorized request and perform safe local/nonexistent-resource failure experiments.

### Week 3 — Source to Runtime
Trace a tiny local/open-source artifact from source/input to runtime behavior, modify one property, and verify the predicted change.

### Week 4 — Controlled Troubleshooting
Build a simple local workflow and introduce at least four controlled failures with evidence-based recovery.

## Final review

`11_final_review.md` should contain:

1. system and scope;
2. architecture summary;
3. strongest evidence;
4. important failed hypotheses;
5. four failure/recovery summaries;
6. security/reliability observations;
7. what AI contributed;
8. what you independently verified;
9. unresolved questions;
10. readiness recommendation: PASS / REPAIR / REPEAT.
