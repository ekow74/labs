# REA Course Template

Use this template for every curriculum module.

## 1. Target and scope
- Course ID:
- Course title:
- Target:
- Why this target represents the course:
- Source/provenance:
- License/authorization:
- REA question:

## 2. Inventory
- Components/modules:
- Dependencies:
- Entry points:
- Interfaces/APIs/protocols:
- Data/storage:
- Configuration:
- Build/runtime:
- Tests:
- External services:

## 3. Architecture
Provide a component diagram and describe:
- control flow;
- data flow;
- state;
- persistence;
- trust boundaries;
- failure domains;
- critical assumptions/invariants.

## 4. Behavior trace
Trace one important workflow end-to-end with evidence.

## 5. Implementation analysis
- Core algorithms/patterns:
- Important modules/functions/classes:
- Error handling:
- Observability:
- Performance choices:
- Security controls:
- Technical debt / surprising choices:

## 6. Runtime evidence
Capture appropriate logs, traces, metrics, profiles, requests, storage changes, outputs, or simulations.

## 7. Failure experiments
- Failure injected / edge case:
- Expected behavior:
- Observed behavior:
- Root cause:
- Classification: design / implementation / configuration / data / dependency / security / operator.

## 8. Reconstruction
Rebuild one meaningful bounded component without copying the reference implementation.

## 9. Benchmark
Compare reference vs reconstruction using course-appropriate metrics.

## 10. Security and reliability review
Document risks, mitigations, and residual weaknesses.

## 11. AI-assistance audit
- What AI generated:
- What I independently verified:
- What AI got wrong:
- What I changed/rejected:
- Evidence of code/analysis ownership:

## 12. Final review
- What the system does:
- How it works:
- Strongest design choices:
- Weakest design choices:
- What I would redesign:
- What I learned:
- What remains uncertain:

## Mastery defense
Be prepared to explain the target without notes, trace the workflow, locate likely failures, modify/rebuild a component, defend the benchmark, and critique incorrect AI output.
