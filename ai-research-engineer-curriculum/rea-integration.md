# REA Mandatory Integration Standard

REA (Reverse Engineering & Analysis) is mandatory across all 153 modules in the AI/CS Research Engineer curriculum.

## Core REA cycle
1. Acquire a legal/authorized target.
2. Inventory components, dependencies, interfaces, configuration, tests, data, and build/runtime requirements.
3. Map architecture, data flow, control flow, state, trust boundaries, persistence, and failure domains.
4. Trace one important workflow end to end.
5. Inspect implementation choices, abstractions, algorithms, error handling, observability, performance, and security controls.
6. Characterize runtime behavior with logs, metrics, profiling, requests, storage behavior, or simulations as appropriate.
7. Introduce controlled failures or edge cases in an authorized environment.
8. Diagnose root cause.
9. Reconstruct a meaningful subsystem, algorithm, protocol, model component, or workflow.
10. Compare against the reference implementation using correctness, performance, memory, cost, reliability, security, and maintainability metrics.
11. Modify or improve the design.
12. Defend the analysis in a technical review.

## Required evidence package
Each course must produce:
- target + provenance;
- authorization/license note;
- architecture/component map;
- dependency/interface inventory;
- data-flow/control-flow trace;
- key implementation notes;
- runtime evidence where applicable;
- failure/edge-case evidence;
- reconstruction or reproduction artifact;
- benchmark/comparison results;
- security/reliability observations;
- AI-assistance audit;
- final technical review.

## Course-family interpretation
- Foundations/programming: reverse engineer CLI tools, parsers, interpreters, libraries, and build systems.
- Mathematics/statistics: derive and reimplement numerical/statistical algorithms, test stability and complexity.
- Algorithms: infer invariants, generate adversarial inputs, reimplement, benchmark.
- OS/architecture: inspect xv6/Linux/RISC-V mechanisms and rebuild a bounded subsystem.
- Databases: trace query/storage/transaction/recovery lifecycles and rebuild selected operators or indexes.
- Compilers: trace source → IR → optimization → machine code; implement a pass/parser/code generator.
- Distributed systems: reconstruct protocols from papers/specs and fault-test safety/liveness.
- Cloud/DevOps/SRE: reverse engineer deployment stacks, CI/CD, Kubernetes, IaC, observability, and recovery.
- Cybersecurity/DevSecOps: authorized labs only; reverse engineer defensive tooling, deliberately vulnerable targets, malware training samples, rules, and controls.
- ML/DL: derive objectives, trace training/evaluation pipelines, reproduce core algorithms and benchmarks.
- AI systems/GPU: inspect kernels, batching, caching, memory managers, quantization, distributed execution, and serving systems.
- Post-training/RL/distillation: reverse engineer training recipes, losses, sampling, teacher/student flows, rewards, pruning/quantization, and evaluation across multiple research groups.
- Retrieval/RAG: trace ingestion → index → retrieval → rerank → synthesis → provenance → eval.
- Agents/MCP: reverse engineer state, planning, context, tool calls, permissions, retries, memory, termination, and evaluation.
- Multimodal/robotics/AI4Science: reproduce a bounded subsystem or published experiment.
- Research apprenticeship: paper reproduction is REA at research depth.
- Advanced lab engineering: REA becomes independent architecture review of unfamiliar systems.

## Mastery gate
A course is not Mastered unless the learner can explain the target without notes, trace the core workflow, identify assumptions and likely failure points, modify/rebuild a meaningful component, design a fair benchmark, distinguish observation from inference, critique incorrect AI output, and document the work reproducibly.

### Scoring
- 20% architecture/system understanding
- 20% reconstruction
- 15% experiments/benchmarking
- 15% debugging/failure analysis
- 10% security/reliability
- 10% documentation/reproducibility
- 10% oral/code-review defense

Pass: 80% with no zero-score category. Research/PhD modules: 90% plus an independent extension or ablation.

## Default per-course layout
```text
REA/
  00_target_and_scope.md
  01_inventory/
  02_architecture/
  03_behavior_traces/
  04_source_or_artifact_analysis/
  05_runtime_evidence/
  06_failure_experiments/
  07_reconstruction/
  08_benchmarks/
  09_security_reliability/
  10_ai_assistance_audit/
  11_final_review.md
```

## Boundaries
Only open-source, public, owned, licensed, classroom, CTF, deliberately vulnerable, or explicitly authorized targets may be instrumented or tested. Paid/proprietary learning material may inform personal study and notes but must not be republished. Security work remains within authorized environments.

Every future course, niche topic, framework, or repository added to the curriculum inherits this REA requirement automatically.
