# T-Rust I/O Standard v0.1

## AI I/O Trust Boundary Standard

Status: **Open Draft**  
Scope: **AI input/output trust boundaries**  
Version: **0.1**

---

## 1. Purpose

T-Rust I/O defines a practical trust boundary model for AI systems.

It focuses on two surfaces:

**IN** — what enters AI.  
**OUT** — what leaves AI.

The standard defines how AI systems should assign trust states, produce evidence packets, constrain unsafe inputs and outputs, escalate uncertain decisions and avoid silent failure.

T-Rust I/O is not a replacement for OWASP, NIST AI RMF, Google SAIF, MITRE ATLAS or ISO AI governance standards.

It is an implementation-oriented draft for the missing operational layer between AI risk frameworks and real AI systems:

    IN -> state -> evidence -> decision -> OUT

---

## 2. Problem

Modern AI systems often treat interaction as a simple pipeline:

    input -> model -> output

This is no longer enough.

Inputs may be untrusted, poisoned, manipulated, malformed or unclear.

Outputs may trigger tool calls, file writes, API requests, recommendations, legal or financial conclusions, autonomous actions or downstream workflows.

The pipeline needs a trust boundary:

    input -> trust state -> AI system -> boundary check -> output/action

The central operational question is:

> Can the system prove what it trusted before it acted?

If the answer is no, the system does not have a real AI I/O trust boundary.

---

## 3. Scope

T-Rust I/O covers:

- AI artifact ingestion;
- document and file trust;
- prompt payload inspection;
- RAG source classification;
- metadata and hidden content handling;
- tool manifest inspection;
- model output constraints;
- agent action boundaries;
- human review states;
- evidence packets;
- trust levels;
- failure and support status rules.

---

## 4. Non-goals

T-Rust I/O does not claim:

- to replace OWASP, NIST, SAIF, MITRE ATLAS or ISO AI governance standards;
- to make any AI system risk-free;
- to make software safe merely because it is written in Rust;
- to remove the need for human review;
- to solve all AI safety problems;
- to be a ratified formal standard today.

This document is an open draft.

---

## 5. Core concepts

### 5.1 AI I/O Trust Boundary

An **AI I/O Trust Boundary** is the control layer that governs what may enter an AI system and what may leave it.

It answers two questions:

**What may AI trust?**  
**What may AI do?**

### 5.2 T-Rust IN

**T-Rust IN** is the input side of the trust boundary.

It governs documents, files, prompts, RAG sources, metadata, API payloads, tool manifests, datasets, external content and user instructions.

### 5.3 T-Rust OUT

**T-Rust OUT** is the output and action side of the trust boundary.

It governs answers, decisions, tool calls, API requests, file writes, agent actions, recommendations, workflow triggers and autonomous operations.

### 5.4 Trust State

A **Trust State** is a machine-readable state assigned to an input, output, tool call, action, failure or escalation.

A trust state is not only a risk label.

It is an operational state inside the AI I/O boundary.

### 5.5 Evidence Packet

An **Evidence Packet** is a structured record explaining why a trust decision was made.

It should answer:

- what was inspected;
- what risk was found;
- which rules or policies applied;
- what decision was made;
- why the decision was made;
- what happened next.

### 5.6 Profile

A **Profile** is an adoption module for a specific boundary area, such as IN, OUT, Agent, RAG or Failure Modes.

---

## 6. Trust surfaces

### 6.1 IN surface

The IN surface includes everything that may become context, memory, retrieval, tool configuration, policy input or reasoning material.

Examples:

- user prompts;
- uploaded documents;
- files and archives;
- metadata;
- hidden text;
- RAG sources;
- retrieved chunks;
- APIs;
- datasets;
- tool manifests;
- system integrations;
- external content.

### 6.2 OUT surface

The OUT surface includes everything that may leave the AI system as information, recommendation, decision or action.

Examples:

- user-facing answers;
- summaries;
- legal, financial, medical or security conclusions;
- tool calls;
- API requests;
- file writes;
- database updates;
- workflow triggers;
- agent actions;
- multi-agent delegation;
- autonomous operations.

---

## 7. Draft trust states

Initial trust states:

| State | Meaning |
|---|---|
| `unseen` | The object has not entered the boundary. |
| `received` | The object has been received but not inspected. |
| `inspected` | The object has been inspected by one or more checks. |
| `classified` | The object has been assigned a type and risk category. |
| `trusted` | The object is allowed without additional constraints. |
| `constrained` | The object may be used only under limits. |
| `blocked` | The object is not allowed to proceed. |
| `quarantined` | The object is isolated until review or additional evidence. |
| `escalated` | The object or decision has been escalated. |
| `failed_with_trace` | Processing failed, but the failure produced a visible trace. |
| `pending_human_review` | Human review is required before proceeding. |

No critical object should remain in an invisible state.

---

## 8. Draft decision vocabulary

Initial decisions:

| Decision | Meaning |
|---|---|
| `allow` | Proceed without additional constraints. |
| `allow_with_warning` | Proceed, but expose warning or caution. |
| `constrain` | Proceed only with limits. |
| `block` | Do not allow the object or action. |
| `quarantine` | Isolate until further inspection or review. |
| `escalate` | Move to a higher review or control layer. |
| `request_human_review` | Require human decision before proceeding. |
| `fail_with_trace` | Stop and produce visible failure evidence. |

---

## 9. Draft trust levels

Initial levels:

| Level | Name | Meaning |
|---|---|---|
| L0 | Observe | Observe and record. |
| L1 | Warn | Warn but allow. |
| L2 | Constrain | Allow with limits. |
| L3 | Quarantine | Isolate until reviewed. |
| L4 | Enforce | Block or require formal approval. |
| L5 | Regulated | Evidence, audit trail, human review and compliance-grade handling. |

---

## 10. Evidence packet requirements

Every critical trust decision should produce an evidence packet.

Minimum fields:

    {
      "object_id": "obj_123",
      "object_type": "document | prompt | rag_source | tool_manifest | output | tool_call | api_request | file_write | agent_action | failure",
      "source": "upload | user_prompt | retrieval | api | tool_registry | system",
      "fingerprint": "sha256:...",
      "profile": "IN | OUT | Agent | RAG | FailureModes",
      "rules_applied": ["TRUST-IN-001", "RAG-002"],
      "risks_detected": [
        {
          "risk_id": "prompt_injection",
          "severity": "medium",
          "confidence": 0.78
        }
      ],
      "trust_state": "constrained",
      "trust_level": "L2",
      "decision": "allow_with_warning",
      "explanation": "The object was allowed with constraints because suspicious instruction-like text was detected inside retrieved content.",
      "timestamp": "2026-06-25T00:00:00Z",
      "escalation_path": "human_review_if_tool_action_requested"
    }

Evidence packets should be:

- traceable;
- explainable;
- timestamped;
- privacy-aware;
- connected to a policy version;
- connected to a profile;
- usable in audit context.

---

## 11. IN Profile

The IN Profile governs what enters AI.

Scope:

- documents;
- files;
- prompts;
- RAG sources;
- metadata;
- API payloads;
- tool manifests;
- datasets;
- external content;
- user instructions.

Core question:

> What may AI trust?

Minimum controls:

- object classification;
- source identification;
- fingerprinting or hashing where possible;
- hidden content inspection;
- prompt-like payload detection;
- metadata inspection;
- trust state assignment;
- evidence packet for critical decisions.

---

## 12. OUT Profile

The OUT Profile governs what leaves AI.

Scope:

- answers;
- decisions;
- tool calls;
- API requests;
- file writes;
- recommendations;
- workflow triggers;
- autonomous operations.

Core question:

> What may AI do?

Minimum controls:

- output classification;
- action intent classification;
- downstream impact assessment;
- permission scope check;
- trust state assignment;
- evidence packet for critical decisions;
- human review for high-impact actions.

---

## 13. Agent Profile

The Agent Profile governs AI systems that can act.

Scope:

- tool use;
- API calls;
- shell commands;
- file operations;
- workflow execution;
- multi-agent delegation;
- irreversible actions.

Required controls:

- least privilege;
- explicit action boundary;
- human review for high-impact actions;
- evidence packet for critical actions;
- stateful action approval;
- traceable escalation path.

Agent actions should not execute only because a model produced them.

They should pass through a boundary decision.

---

## 14. RAG Profile

The RAG Profile governs retrieved content and knowledge sources.

Scope:

- source trust;
- retrieval trust;
- vector and embedding weaknesses;
- poisoning resistance;
- citation evidence;
- source reputation.

Required controls:

- source classification;
- retrieval context inspection;
- hidden instruction detection;
- source reputation or provenance;
- citation evidence;
- trust state per retrieved object or chunk.

Retrieved content should be treated as data, not as instruction authority.

---

## 15. Failure Modes Profile

The Failure Modes Profile governs what happens when the system cannot proceed normally.

Scope:

- silent failures;
- silent support void;
- dry statuses;
- support delays;
- uncertain states;
- escalation paths.

Required controls:

- visible status;
- human-readable explanation;
- next update time;
- current known state;
- escalation path;
- failure evidence or trace.

Core rules:

- **No Silent Failure**
- **No Silent Support Void**
- **No Dry Status**

A critical system must not fail silently.

A critical system must not leave the user alone inside uncertainty.

Every delay, block, rejection or uncertainty state must reduce user uncertainty.

---

## 16. Human review

Human review is not an afterthought.

It is a boundary state.

A system should escalate when:

- the trust state is uncertain;
- the action has irreversible impact;
- the input contains conflicting instructions;
- the output affects legal, financial, medical, safety-critical or security decisions;
- the system cannot produce sufficient evidence;
- the decision exceeds the configured trust level.

Human review should be connected to an evidence packet.

---

## 17. Relationship to existing frameworks

T-Rust I/O does not compete with OWASP, NIST, SAIF or MITRE ATLAS.

It is intended to operationalize their concerns into an implementation-oriented boundary model.

- OWASP identifies LLM and agentic AI risks.
- NIST AI RMF frames AI risk governance.
- Google SAIF maps AI security architecture.
- MITRE ATLAS documents adversary behavior.

T-Rust I/O defines a practical boundary protocol:

    IN -> state -> evidence -> decision -> OUT

---

## 18. Mapping intent

Future versions should include explicit mappings to:

- OWASP LLM Top 10;
- OWASP Agentic AI guidance;
- NIST AI RMF;
- NIST GenAI Profile;
- Google SAIF;
- MITRE ATLAS;
- ISO/IEC AI governance standards.

The mapping should clarify:

- which risks are covered;
- which risks are only partially covered;
- which controls are outside scope;
- which T-Rust I/O profiles operationalize each risk or control.

---

## 19. Open questions

- How should trust states compose across multi-agent systems?
- How should evidence packets handle privacy and deletion requirements?
- What performance overhead is acceptable for production trust gates?
- Should the standard become a protocol with wire formats?
- Which trust states should be mandatory?
- Which failure states should be normative?
- How should trust states be represented in distributed systems?
- Should evidence packets be signed?
- Should trust events be append-only?
- How should support delay be measured in safety-critical contexts?

---

## 20. Status

This document is an early public draft.

It is intended for critique, discussion and iterative development.

The goal is not to claim that AI security starts here.

The goal is to define a missing operational layer:

> AI I/O trust boundaries with states, evidence, review and failure visibility.

**In T-Rust We Trust.**