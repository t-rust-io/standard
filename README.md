# T-Rust I/O

## AI I/O Trust Boundary Standard

**In T-Rust We Trust.**

Modern AI systems have model layers, data layers, policy layers, agent layers and governance frameworks.

But many of them still lack a clear operational boundary for one critical question:

> **Can the system prove what it trusted before it acted?**

T-Rust I/O is an open, implementation-oriented draft for the **AI I/O Trust Boundary Standard**.

It defines how AI systems assign trust states, produce evidence packets and enforce decisions around what enters AI and what leaves AI.

---

## The missing layer

AI systems are no longer just answering questions.

They read documents.  
They index knowledge.  
They retrieve context.  
They call tools.  
They write files.  
They trigger workflows.  
They support legal, financial, medical, engineering and security decisions.

But the world around AI is noisy.

Files, prompts, RAG sources, metadata, APIs, tool manifests, agent commands and user instructions often enter AI systems without a clear trust state.

Outputs leave AI systems as answers, actions, recommendations, tool calls or decisions — often without enough evidence, boundary control or human-centered failure handling.

T-Rust I/O defines the missing I/O trust layer.

---

## Core idea

Every AI system has two critical trust surfaces:

**IN** — what enters the system.  
**OUT** — what leaves the system.

T-Rust I/O defines how AI systems should inspect, classify, constrain and document every input and output before it becomes:

- context;
- memory;
- retrieval;
- tool execution;
- agent action;
- workflow trigger;
- file write;
- user-facing decision.

**Trust In. Trust Out.**

---

## The missing question

Most AI security discussions ask:

- Is the model safe?
- Is the prompt malicious?
- Is the output harmful?
- Is the agent over-permissioned?
- Is the data poisoned?

T-Rust I/O asks a more operational question:

> **Can the system prove what it trusted before it acted?**

If the answer is no, the system does not have a real AI I/O trust boundary.

---

## What T-Rust I/O defines

T-Rust I/O introduces a practical language for AI trust boundaries:

- **Trust States** — visible states for inputs, outputs, actions and failures;
- **Evidence Packets** — structured proof of why something was allowed, blocked, constrained or escalated;
- **T-Rust IN** — inspection of documents, files, prompts, metadata, RAG sources, tool manifests and external content;
- **T-Rust OUT** — boundaries for responses, decisions, tool calls, API requests, file writes and agent actions;
- **Human Review States** — escalation as part of the boundary, not an afterthought;
- **Failure States** — no silent blocking, no silent loss, no silent uncertainty;
- **Human Trust Status Funnel** — every critical delay must reduce uncertainty.

---

## Where T-Rust I/O fits

T-Rust I/O does not replace existing AI security and governance frameworks.

It builds on them.

- **OWASP** identifies LLM and agentic AI risks.
- **NIST AI RMF** frames AI risk governance.
- **Google SAIF** maps AI security architecture.
- **MITRE ATLAS** documents adversary behavior against AI systems.

T-Rust I/O focuses on the implementation gap between those frameworks and real systems:

> **a stateful, evidence-producing AI I/O trust boundary.**

OWASP can tell you what can go wrong.  
NIST can tell you how to govern risk.  
SAIF can tell you where the attack surfaces are.  
MITRE ATLAS can tell you how adversaries behave.

T-Rust I/O defines how trust moves through the boundary:

**IN → state → evidence → decision → OUT**

---

## What makes this different

T-Rust I/O is not just another prompt filter, guardrail, AI firewall or governance checklist.

Its focus is narrower and more operational:

| Existing layer | Typical focus | T-Rust I/O focus |
|---|---|---|
| Risk taxonomy | What can go wrong | How trust is assigned and enforced |
| Governance framework | How risk is managed | How I/O decisions are made visible |
| Guardrail | Filter or block content | Produce trust states and evidence |
| AI gateway | Route, log or filter requests | Govern what enters and leaves AI |
| Agent framework | Execute tool chains | Prove why actions were allowed |
| Audit log | Record events | Explain trust decisions |

The goal is not to rename existing AI security work.

The goal is to define the missing boundary protocol.

---

## Core principles

### 1. Order, not restriction

T-Rust I/O is not here to make AI smaller.

It is not a censorship layer.  
It is not a cage.  
It is not a way to reduce intelligence, creativity or usefulness.

T-Rust I/O is here to make the environment around AI clearer.

We do not limit intelligence.  
We define trust.

### 2. Trust must be earned

AI should not trust inputs by default.

A document may contain hidden instructions.  
A RAG source may be poisoned.  
A prompt may carry a payload.  
A tool manifest may hide unsafe capabilities.  
An output may look confident while resting on unsafe input.

Every critical input and output should have a trust state.

### 3. Evidence over claims

A trust boundary must produce evidence.

Every trust decision should be traceable:

- what was inspected;
- which rules applied;
- what risks were found;
- what was allowed;
- what was blocked;
- what was constrained;
- what was escalated;
- which trust level was assigned.

Trust without evidence is only belief.

### 4. No Silent Failure

A trust system must not fail silently.

It must not lose, block, alter, reject or delay a critical object without a visible status, explanation and trace.

When trust breaks, explanation becomes part of security.

### 5. No Silent Support Void

Support delay is part of the trust boundary.

A critical system is not trustworthy only because it is internally safe.

It must also explain failure quickly, clearly and humanely.

A user must never be left alone inside uncertainty.

### 6. No Dry Status

A dry status like `ticket received`, `pending` or `processing` is not enough for critical systems.

Every status should reduce uncertainty.

Even without an LLM, status messages can be clear, warm and useful.

A trust system should not sound like a wall.

---

## Why Rust?

Rust is not magic.

T-Rust I/O does not claim that “written in Rust” automatically means safe.

Rust is chosen because an AI trust boundary must handle untrusted material with discipline:

- documents;
- files;
- payloads;
- metadata;
- archives;
- prompts;
- RAG sources;
- API responses;
- tool manifests;
- agent commands.

Memory safety, strong typing, explicit ownership, controlled concurrency and auditable implementation are not conveniences here.

They are part of the trust model.

**Rust is the foundation. Evidence is the trust.**

---

## Draft profiles

T-Rust I/O is modular by design.

Initial profiles:

- **IN Profile** — document, file, prompt, RAG and artifact ingestion trust;
- **OUT Profile** — response, decision, tool-call and action boundaries;
- **Agent Profile** — tool use, API calls, file writes and autonomous operations;
- **RAG Profile** — source trust, retrieval trust, poisoning resistance and citation evidence;
- **Failure Modes Profile** — no silent failure, no silent support void and human-centered status states.

A system can adopt one profile first and expand over time.

---

## Initial trust states

T-Rust I/O introduces machine-readable trust states.

Early draft states:

- `unseen`
- `received`
- `inspected`
- `classified`
- `trusted`
- `constrained`
- `blocked`
- `quarantined`
- `escalated`
- `failed_with_trace`
- `pending_human_review`

No critical object should remain in an invisible state.

---

## Initial evidence packet

Every trust decision should produce an evidence packet.

Minimum draft fields:

- object id;
- object type;
- source;
- hash or fingerprint;
- inspection profile;
- rules applied;
- risks detected;
- trust state;
- trust level;
- decision;
- explanation;
- timestamp;
- escalation path when needed.

---

## Non-goals

T-Rust I/O does not claim:

- to replace OWASP, NIST, SAIF, MITRE ATLAS or ISO AI governance standards;
- to make any AI system risk-free;
- to make software safe just because it is written in Rust;
- to remove the need for human review;
- to solve all AI safety problems;
- to be a ratified formal standard today.

This repository is an early public draft.

---

## Who we are

T-Rust I/O is maintained by an independent research and engineering initiative focused on AI trust boundaries, secure system design and evidence-producing AI infrastructure.

We are not a formal standards body, certification authority or security vendor claiming to replace existing frameworks.

We are building an open, implementation-oriented draft for a narrower missing layer:

> how AI systems should assign trust states, produce evidence and make visible decisions about what enters AI and what leaves AI.

Our work is intentionally public at the language, model, principle and interface level.

We welcome critique from AI security researchers, Rust engineers, agent framework builders, RAG system designers, auditors and practitioners working on real-world AI systems.

The goal is not to own the conversation.

The goal is to make AI trust boundaries easier to define, implement, test and challenge.

We believe AI systems should not only act.

They should be able to show what they trusted before they acted.


## Project status

T-Rust I/O is currently an open draft.

The goal is to develop a practical, implementation-oriented standard for AI I/O trust boundaries.

This is not a product launch.

This is a standard beginning.

**In T-Rust We Trust.**
