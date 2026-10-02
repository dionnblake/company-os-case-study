# Company OS case study

A local-first, multi-agent operating system for routing business work, grounding decisions in private evidence, retaining only approved learning, and enforcing security and human review across multiple AI clients.

**Implementation note:** The source repositories are private because they contain proprietary operating logic and business context. This public repository is an architecture and engineering case study. It does not claim that the system is production-ready.

## Recruiter snapshot

- **What I built:** A layered company operating system that coordinates Codex, Claude, Hermes, and Antigravity without treating any single chat session as the source of truth.

- **Why I built it:** I needed AI tools to continue real business work safely across projects, agents, and sessions while preserving evidence, boundaries, and owner control.

- **What makes it different:** Routing, worker execution, retrieval, learning, security, and certification are separate systems with explicit contracts. Passing a test or retrieving an answer never becomes permission to publish, deploy, spend, or change policy.

- **How I approach the work:** I am an applied AI workflow and automation builder. I do not rely on a computer science degree as my credential. The systems, decisions, and evidence in my portfolio are the resume.

---

## The problem

Chat-based AI is useful, but it becomes fragile when real work spans multiple tools, projects, and days. Context gets lost. Different agents make conflicting assumptions. Retrieved information can be mistaken for authority. A successful test can be confused with permission to act. Learning systems can silently promote bad conclusions.

For business use, I needed a stronger operating model:

- one durable source of current state;
- clear routing to the right project and domain;
- bounded workers with traceable activity;
- private evidence retrieval with citations;
- governed learning instead of uncontrolled self-modification;
- security checks that apply across repositories;
- independent evidence that the layers work together safely;
- a human owner as the final authority for consequential actions.

## The solution

Company OS separates those responsibilities into focused layers. Each layer has a narrow job, explicit boundaries, and a defined relationship to the others. The result is a reviewable workflow rather than one large autonomous agent.

```text
                              OWNER INTENT
                                   |
                                   v
+------------------------------------------------------------------+
| BLAKE OS: operating safety, current state, authorization, handoff |
+------------------------------------------------------------------+
                                   |
                                   v
+------------------------------------------------------------------+
| PROJECT OS: understand the request and route it to the right home |
+------------------------------------------------------------------+
                                   |
                                   v
+------------------------------------------------------------------+
| ALPHA FOUNDRY: create a bounded, policy-aware worker environment  |
+------------------------------------------------------------------+
                                   |
                                   v
+------------------------------------------------------------------+
| AGENTIC WORKFORCE: perform domain-specific business work          |
+------------------------------------------------------------------+
                    |                              |
                    v                              v
+--------------------------------+   +-----------------------------+
| LIBRARY OF KNOWLEDGE           |   | LEARNING & MEMORY           |
| private evidence and citations |   | governed lessons and state  |
+--------------------------------+   +-----------------------------+
                    \                              /
                     \                            /
                      v                          v
                    REVIEWABLE OUTPUTS AND EVIDENCE
                                   |
                                   v
                             OWNER DECISION

Cross-cutting controls:
  SECURITY      secret, code, dependency, and policy gates
  CERTIFICATION independent read/test/evidence/certify workspace
```

---

## How work moves through the system

1. **Owner intent enters a controlled environment.** Blake OS establishes the current state, applicable authority, safety boundaries, and handoff context.

2. **The request is routed before it is executed.** Project OS determines which project, workflow, skill, or domain system owns the work.

3. **Execution is bounded.** Alpha Foundry creates a scoped worker environment with explicit policy decisions, provenance, and audit evidence.

4. **A specialist performs the work.** The agentic workforce applies the rules and workflows of the relevant business domain.

5. **Claims are grounded.** Workers can retrieve private source material from the Library of Knowledge and return cited evidence or abstain when support is weak.

6. **Experience becomes a proposal, not an automatic rule.** Learning & Memory records events and lessons, but only an explicit owner decision can promote evaluated learning into canonical memory.

7. **Controls remain independent.** Security gates inspect the work, while the certification workspace tests cross-system behavior and produces GO/NO-GO evidence.

8. **The owner remains the final authority.** A completed task, passing scan, or successful certification does not independently authorize an external or consequential action.

---

## Layer-by-layer breakdown

### 1. Blake OS

**Business purpose:** Keeps work continuous, controlled, and recoverable even when different AI clients are used across different sessions.

Blake OS is the local-first operating layer. It manages canonical state, client adapters, safe writes, recovery, authorization, evidence, handoffs, conflict handling, and privacy boundaries. Project files and verified project state remain authoritative; chat history and convenience retrieval layers do not.

### 2. Project OS

**Business purpose:** Sends each request to the right project and prevents unrelated systems from taking ownership of the work.

Project OS adds semantic project context, declarative routing, skills, workflows, output QA, approved references, and versioned contracts. It decides where work belongs. The receiving domain system decides how that work should be performed.

### 3. Alpha Foundry

**Business purpose:** Gives AI workers a controlled place to act without giving them unlimited access or authority.

Alpha Foundry is a local worker and control-plane workbench. It uses scoped workspaces, explicit policy decisions, worker provenance, append-only audit records, immutable artifacts, and bounded execution. The goal is reviewable delegation, not unrestricted autonomy.

### 4. Agentic workforce

**Business purpose:** Turns routed requests into useful work through specialists that understand the business domain.

The workforce consists of domain execution systems for activities such as research, strategy, content, quality assurance, claims review, product intelligence, and technical operations. Each domain preserves its own operating rules and stop lines rather than inheriting blanket authority from the orchestration layer.

### 5. Library of Knowledge

**Business purpose:** Lets workers answer from private source material instead of relying on model memory or unsupported guesses.

The local-first retrieval system ingests PDF, EPUB, TXT, and Markdown files. It uses SQLite FTS5 search, cited answers, weak-evidence abstention, OCR remediation, and review queues. Retrieved evidence can support a decision, but it cannot authorize one.

### 6. Learning & Memory

**Business purpose:** Helps the system improve from experience without allowing an agent to silently rewrite the rules.

The learning ledger separates event memory, episodic memory, proposed learning, evaluated learning, and canonical memory. A lesson moves through review stages. It becomes canonical only after an explicit owner promotion decision.

### 7. Security control plane

**Business purpose:** Applies consistent security checks across repositories before risky changes can move forward.

The security layer includes secret scanning, static application security testing, dependency and supply-chain scanning, reusable gate orchestration, security receipts, waivers, and severity-based blocking policy. The scanner lineup includes Gitleaks, TruffleHog, Semgrep, and OSV-Scanner.

### 8. Cross-system certification

**Business purpose:** Verifies that independently built layers can work together safely before anyone treats the integration as ready.

The certification workspace follows a read, test, evidence, certify model. It checks contracts, contention behavior, idempotency, rollback evidence, and integration readiness, then records GO/NO-GO evidence. It observes and certifies; it does not control or activate production systems.

---

## Selected technologies and patterns

**AI clients**

- Codex
- Claude
- Hermes
- Antigravity

**Knowledge and evidence**

- SQLite FTS5 retrieval
- PDF, EPUB, TXT, and Markdown ingestion
- Citation-backed responses
- Weak-evidence abstention
- OCR remediation and human review queues

**Governance and reliability**

- Local-first canonical state
- Declarative routing
- Versioned contracts
- Scoped workspaces
- Explicit authorization boundaries
- Worker provenance
- Append-only audit records
- Immutable artifacts
- Human-gated canonical learning
- Cross-system certification evidence

**Security tooling**

- Gitleaks
- TruffleHog
- Semgrep
- OSV-Scanner

## Key design decisions

### Separate evidence from authority

A retrieved source may support a claim, but it cannot approve a business action. A passing test may demonstrate technical behavior, but it cannot authorize deployment. This distinction runs through every layer.

### Prefer bounded specialists over one autonomous agent

Routing, execution, retrieval, memory, security, and certification have separate responsibilities. This limits blast radius, makes failures easier to diagnose, and keeps each system reviewable.

### Treat learning as a governed workflow

The system can record mistakes and propose lessons without allowing those lessons to become policy automatically. Human promotion protects the canonical memory layer from accidental or adversarial changes.

### Preserve evidence for continuation

Canonical state, provenance, audit records, immutable artifacts, and handoffs make it possible to continue work across agents and sessions without depending on a model's conversation memory.

### Keep consequential actions human-controlled

Publishing, deployment, messaging, spending, credentials, and policy changes remain outside default worker authority. Owner approval is a system boundary, not a conversational preference.

---

## What this demonstrates

A recruiter should be able to see the following in under 30 seconds:

- **Multi-agent orchestration:** I designed distinct operating, routing, worker, domain, evidence, learning, security, and certification layers that coordinate through explicit boundaries.

- **RAG over a large private library:** I built local-first ingestion and retrieval across multiple document formats, with citations, OCR recovery, review queues, and abstention when evidence is weak.

- **Governed memory and learning:** I separated raw events from proposed, evaluated, and canonical learning so the system can improve without silently changing its own authority.

- **Security-first engineering:** I integrated secret, code, dependency, and supply-chain scanning into a reusable control plane with blocking policy and reviewable evidence.

- **Reliable workflow design:** I used canonical state, safe writes, versioned contracts, provenance, immutable artifacts, recovery, handoffs, and independent certification to make long-running work inspectable.

- **Real business application:** I built the system around operating needs in my own businesses, not as a tutorial clone or a one-off demo.

## Scope and privacy

This repository intentionally contains the case study, not the implementation. Private source code, business data, credentials, internal prompts, local paths, and proprietary operating details are excluded.

The architecture is under active development. Labels such as tested, verified, or certified refer only to the evidence and scope defined by the relevant private repository. They do not imply blanket production readiness or autonomous authority.

---

## About the builder

I build practical AI workflows, automation systems, retrieval tools, websites, and applications for real operating needs. My focus is not training foundation models. It is designing reliable systems around them: deciding where work belongs, constraining how agents act, grounding outputs in evidence, preserving what was learned, and keeping a human in control.
