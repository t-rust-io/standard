# Mapping: Google Secure AI Framework

This document maps T-Rust I/O to Google's Secure AI Framework.

This is not an official Google mapping.

It is an implementation-oriented bridge showing how secure AI infrastructure concerns can be expressed as trust states, evidence packets and boundary decisions inside T-Rust I/O.

---

## What Google SAIF provides

Google's Secure AI Framework focuses on secure AI development and deployment.

It is especially useful for thinking about:

- security foundations for AI systems;
- detection and response;
- scalable protections;
- platform-level controls;
- adapting controls to AI-specific risks;
- privacy and security in AI-powered applications.

T-Rust I/O does not replace SAIF.

It focuses on the operational boundary around AI inputs, outputs and actions.

---

## Where T-Rust I/O fits

SAIF helps teams think about secure AI systems.

T-Rust I/O asks:

> At the moment an AI system receives data or attempts an action, what trust decision is made and what evidence exists?

T-Rust I/O can be used as a boundary layer inside a SAIF-aligned architecture.

---

## Core relationship

    SAIF secure AI principle
      -> T-Rust boundary control
      -> trust state
      -> evidence packet
      -> decision
      -> monitoring / escalation

---

## Example mapping

| SAIF-style concern | T-Rust I/O boundary expression |
|---|---|
| Secure foundations | Explicit IN and OUT trust boundary |
| Detection and response | Trust states, risk signals, failure traces |
| Automated defenses | Boundary decisions such as `constrain`, `block`, `quarantine` |
| Platform-level controls | Profiles and policy versions |
| Adaptive controls | State transitions and profile-specific enforcement |
| AI-specific risk context | Evidence packets tied to object type, source and decision |
| Privacy and security | OUT Profile checks and evidence-aware retention questions |
| Model and application protection | IN inspection, RAG Profile, Agent Profile |

---

## What T-Rust I/O adds

T-Rust I/O adds a specific operational vocabulary:

1. IN Boundary  
   What enters AI is inspected and assigned a trust state.

2. OUT Boundary  
   What leaves AI is classified before it becomes an answer, action, API call or file operation.

3. Evidence Packet  
   Trust decisions are recorded as structured evidence.

4. Agent Profile  
   AI tool use and autonomous operations are treated as boundary events.

5. Failure Modes Profile  
   The system must not leave users or operators inside unexplained uncertainty.

---

## Example: SAIF-aligned boundary

A secure AI architecture may include:

- identity and access controls;
- logging;
- monitoring;
- model security;
- data protection;
- deployment controls.

T-Rust I/O adds:

    AI input or output event
      -> trust boundary inspection
      -> state assignment
      -> evidence packet
      -> enforceable decision

---

## Non-replacement statement

T-Rust I/O does not replace Google SAIF.

SAIF is a broad secure AI framework.

T-Rust I/O is a narrower draft focused on the visible trust boundary around AI input, output and action execution.

The two can be complementary.

---

## Open questions

- Which SAIF-aligned controls should produce T-Rust evidence packets?
- How should platform-level controls expose boundary decisions?
- How should T-Rust states integrate with detection and response pipelines?
- How should T-Rust profiles map to enterprise AI security programs?
