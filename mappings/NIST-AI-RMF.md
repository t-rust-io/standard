# Mapping: NIST AI Risk Management Framework

This document maps T-Rust I/O to the NIST AI Risk Management Framework.

This is not an official NIST mapping.

It is an implementation-oriented bridge showing how AI risk management concerns can be expressed as trust states, evidence packets and boundary decisions inside T-Rust I/O.

---

## What NIST AI RMF provides

The NIST AI Risk Management Framework helps organizations manage AI risks in a structured way.

It is especially useful for:

- governance;
- risk mapping;
- risk measurement;
- risk management;
- organizational accountability;
- trustworthy AI practices;
- lifecycle-level risk thinking.

T-Rust I/O does not replace NIST AI RMF.

It focuses on a narrower implementation layer:

> how a real AI system records, explains and enforces trust decisions at its input and output boundaries.

---

## Where T-Rust I/O fits

NIST AI RMF helps organizations ask:

- What AI risks exist?
- Who is responsible?
- How are risks governed?
- How are risks measured?
- How are risks managed?

T-Rust I/O asks:

- What entered the AI system?
- What did the system trust?
- What evidence supported that trust?
- What decision was made?
- What left the system?
- Was failure visible?

---

## Core relationship

    NIST AI RMF governance concern
      -> T-Rust profile requirement
      -> trust state
      -> evidence packet
      -> boundary decision
      -> audit trace

---

## Example mapping

| NIST-style concern | T-Rust I/O implementation object |
|---|---|
| Govern AI risk | Profiles, policy versions, boundary ownership |
| Map AI context | IN and OUT object classification |
| Measure AI risk | Trust states, risk signals, confidence, severity |
| Manage AI risk | Boundary decisions, constraints, escalation paths |
| Transparency | Evidence packets and visible trust states |
| Accountability | Traceable decisions and policy versions |
| Human oversight | `pending_human_review` and escalation paths |
| Incident handling | Failure Modes Profile and `failed_with_trace` |
| Documentation | Evidence packets and profile-level records |

---

## What T-Rust I/O adds

T-Rust I/O adds operational artifacts that may support risk management:

1. Trust States  
   Machine-readable state labels for objects, actions and failures.

2. Evidence Packets  
   Structured records explaining why a trust decision was made.

3. IN / OUT Boundary  
   A clear distinction between what enters AI and what leaves AI.

4. Profiles  
   Modular adoption paths for IN, OUT, Agent, RAG and Failure Modes.

5. Failure Visibility  
   Requirements for visible status, explanation and escalation when systems cannot proceed normally.

---

## Example: governance to runtime

Governance statement:

    AI systems should manage risks from untrusted external data.

T-Rust I/O runtime expression:

    external_document
      -> received
      -> inspected
      -> classified
      -> constrained
      -> evidence_packet
      -> allow_with_warning

Governance statement:

    High-impact AI actions should require human oversight.

T-Rust I/O runtime expression:

    agent_action
      -> inspected
      -> classified
      -> pending_human_review
      -> evidence_packet
      -> request_human_review

---

## Non-replacement statement

T-Rust I/O does not replace NIST AI RMF.

NIST AI RMF is a broad risk management framework.

T-Rust I/O is a narrower implementation-oriented draft focused on visible AI input/output trust boundaries.

The two can be complementary.

---

## Open questions

- Which NIST AI RMF outcomes should map to mandatory T-Rust evidence requirements?
- Should T-Rust maintain profile-specific mappings for high-impact systems?
- How should T-Rust evidence packets support organizational risk reporting?
- How should T-Rust distinguish public, enterprise and regulated adoption levels?
