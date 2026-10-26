# FND-001 — Computing Fundamentals

**Stage:** 0 — Bridge Foundations  
**Level:** Novice  
**Nominal effort:** 20 hours  
**Format:** 4 weeks × ~5 hours  
**Prerequisites:** None  
**REA:** Mandatory  
**Mastery threshold:** 80% overall plus all required evidence

## Purpose

Build the systems mental model required for the rest of the AI/CS Research Engineer curriculum. The learner must be able to trace behavior across hardware, operating systems, files, processes, networks, applications, data, and cloud services, then collect evidence and diagnose safe local failures instead of guessing.

## Learning outcomes

By completion the learner can:

1. Explain CPU, RAM, storage, firmware, OS, process, thread, file system, driver, and application roles.
2. Distinguish bits, bytes, binary, hexadecimal, encodings, file formats, and serialization at an introductory level.
3. Explain client/server systems and IP, DNS, ports, TCP, UDP, TLS, HTTP, URLs, APIs, JSON, and browsers.
4. Distinguish local apps, VMs, containers, cloud services, databases, front ends, back ends, and APIs.
5. Inspect a process and relate it to executable files, memory, and network activity.
6. Trace a web request end-to-end.
7. Use basic evidence tools: Task Manager, Resource Monitor, PowerShell, curl, nslookup/Resolve-DnsName, tracert, netstat, and browser DevTools.
8. Draw an evidence-based architecture diagram.
9. Perform a safe REA investigation and record observation vs inference.
10. Audit AI assistance and independently verify important claims.

## Core resources

- Harvard CS50x: https://cs50.harvard.edu/x/
- MIT Missing Semester: https://missing.csail.mit.edu/
- Charles Petzold, *Code: The Hidden Language of Computer Hardware and Software*
- MDN Web Docs: https://developer.mozilla.org/
- Cloudflare Learning Center: https://www.cloudflare.com/learning/
- Microsoft Windows documentation

## Assessment

- Weekly quizzes — 20%
- Weekly labs — 25%
- REA evidence packages — 20%
- Final mastery project — 25%
- Oral defense — 10%

A failed category is repaired and resubmitted; mastery, not one-shot grading, is the goal.

# Week 1 — How a Computer Works

Topics: abstraction; hardware/software; CPU; cache/registers conceptually; RAM vs storage; SSD/HDD; firmware/boot; OS responsibilities; kernel/user applications; processes/threads; files/paths/extensions; bits/bytes; binary/hex; ASCII/Unicode/UTF-8; executable vs data files.

### Lab 1 — Inventory Your Computer

Collect evidence for CPU, logical processors, RAM, storage, network adapters, Windows version, architecture, uptime, three running processes, and three file types. Explain the important fields rather than pasting raw output.

Suggested commands: `systeminfo`, `Get-ComputerInfo`, `Get-Process`, `Get-Volume`, `ipconfig /all`.

### REA 1 — Process Autopsy

Inspect one benign local application. Identify PID and executable, observe idle and active resource behavior, close it, verify process termination, and draw: user action → application → OS → CPU/memory/storage/display.

Deliver architecture diagram, evidence, explanation, and AI-assistance audit.

### Quiz 1

10 short-answer questions covering CPU/RAM/storage, program vs process, PID, OS role, bits/bytes, hex, UTF-8, executable size vs memory usage, hardware/software examples, and evidence of process termination.

# Week 2 — Networks, the Web, and APIs

Topics: client/server; interfaces; LAN vs Internet; IPv4/IPv6; private/public addressing; routing/NAT; DNS; ports/sockets; TCP/UDP; TLS; HTTP; URLs; status codes; headers/body; rendering; APIs; JSON; latency/bandwidth.

### Lab 2 — Trace a Web Request

For an authorized public website collect URL anatomy, DNS resolution, route evidence where available, browser Network-panel evidence, request method, status, headers, content type, response size, and timing.

Explain: URL → DNS → connection → TLS → HTTP request → response → browser processing → rendering.

### REA 2 — Safe Failure Experiments

Perform three or more safe failures such as nonexistent path, closed local port, or stopped local test service. For each record prediction, action, evidence, diagnosis, and recovery. Do not probe systems you do not own or have authorization to test.

### Quiz 2

10 short-answer questions on DNS, IP/domain/URL, ports, TCP/UDP, TLS, HTTP 404/500, JSON, and evidence-driven troubleshooting.

# Week 3 — Applications, Data, Virtualization, and Cloud

Topics: front end, back end, API, database, structured/unstructured data, SQL vs non-SQL conceptually, local/web apps, VM, container, image, cloud, IaaS/PaaS/SaaS, identity/authorization, least privilege, logs/observability, SDLC, source → build → deploy → runtime.

### Lab 3 — Map a Software System

Create context and component diagrams for a familiar system. Label each component as **observed**, **documented**, or **inferred**. Include user/client, front end, API/back end, data store, identity boundary, dependencies, monitoring, and likely failure points.

### REA 3 — Source to Runtime

Take a tiny local/open-source utility or static web project. Trace input/source → launch/build → process → files/resources → optional network behavior → output. Modify one visible property and prove runtime behavior changed as predicted.

### Quiz 3

10 short-answer questions on front/back end, APIs, databases, authn/authz, VMs/containers, cloud service models, least privilege, logs, source/runtime drift, and proving deployed version.

# Week 4 — System Thinking, Troubleshooting, and Mastery

Topics: dependencies; state; configuration; contracts; observability; failure domains; hypothesis-driven troubleshooting; reproducibility; root cause vs symptom; change isolation; rollback; postmortems; architecture documentation; AI-assisted engineering judgment.

### Lab 4 — Controlled Troubleshooting

Create a simple local workflow such as browser/curl → local test server → static file. If Python is installed, `python -m http.server 8000` may be used as a no-code local server.

Collect baseline evidence. Introduce at least four controlled failures such as stopping server, wrong port, missing file, renamed file, or wrong working directory. Predict first, change one thing, capture evidence, identify failed layer, restore, verify.

# Final Mastery Project — Anatomy of a Computing System

Trace a local web request and compare it with a public web request.

Required evidence:

1. problem statement;
2. architecture diagram;
3. evidence inventory;
4. successful baseline trace;
5. four controlled failure experiments;
6. diagnosis and repair verification;
7. reconstruction from your own notes;
8. local-vs-public comparison;
9. three security/reliability observations;
10. AI-assistance audit;
11. five-minute oral defense.

## REA evidence tree

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

## Mastery rubric

- Architecture and mental model — 20
- Evidence quality — 15
- Troubleshooting method — 15
- REA reconstruction — 15
- Networking/web trace — 10
- Systems concepts — 10
- Security/reliability reasoning — 5
- AI-assistance audit — 5
- Oral defense — 5

**Pass:** 80/100 plus all mandatory evidence.

## Mastery gate

Before FND-002, explain without notes:

- application launch from executable to running process;
- program vs process;
- HTTPS request path;
- DNS vs TCP vs TLS vs HTTP;
- why ports exist;
- RAM vs SSD vs database;
- container vs VM;
- cloud as computing infrastructure;
- evidence-driven website troubleshooting;
- DNS-failure vs server-failure evidence;
- observation vs inference;
- verification after repair;
- how to independently verify an AI-generated systems explanation.

## Remediation

Below 80%: explain missed concepts in your own words, add an evidence exercise, and retake an alternate assessment. Preserve failed project versions and repair only weak rubric categories so progress remains auditable.

## AI teaching protocol

Diagnostic → intuition → vocabulary → worked example → learner teach-back → guided lab → REA → closed-book quiz → correction review → mastery project → oral defense.

## Next course

**FND-002 — Linux Command Line and Shell**
