# Mapping: MITRE ATLAS

This document maps T-Rust I/O to MITRE ATLAS.

This is not an official MITRE mapping.

It is an implementation-oriented bridge showing how adversarial AI tactics and techniques can be expressed as trust states, evidence packets and boundary decisions inside T-Rust I/O.

---

## What MITRE ATLAS provides

MITRE ATLAS is a knowledge base of adversary tactics, techniques and case studies against AI-enabled systems.

It is especially useful for:

- understanding adversarial behavior against AI systems;
- describing tactics and techniques;
- connecting threats to real-world observations;
- supporting threat modeling;
- informing detection and mitigation work.

T-Rust I/O does not replace MITRE ATLAS.

It asks how suspicious events should be handled at the AI input/output boundary.

---

## Where T-Rust I/O fits

MITRE ATLAS describes adversarial behavior.

T-Rust I/O asks:

> When behavior resembling an adversarial technique appears near an AI boundary, what state, evidence and decision should the system produce?

---

## Core relationship

    ATLAS tactic or technique
      -> T-Rust detection signal
      -> trust state
      -> evidence packet
      -> boundary decision
      -> constraint / block / escalation

---

## Example mapping

| ATLAS-style threat area | T-Rust I/O boundary concern | Possible trust state | Possible decision |
|---|---|---|---|
| Data poisoning | Incoming data may manipulate AI behavior | `constrained`, `quarantined` | `constrain`, `quarantine` |
| Prompt injection | Input attempts to override system intent | `constrained`, `blocked` | `constrain`, `block` |
| Retrieval manipulation | RAG source or chunk may mislead the model | `constrained`, `quarantined` | `constrain`, `quarantine` |
| Model evasion | Input attempts to bypass safeguards | `constrained`, `blocked` | `constrain`, `block` |
| Exfiltration | Output or tool call may leak sensitive data | `blocked`, `pending_human_review` | `block`, `request_human_review` |
| Tool abuse | Agent attempts unsafe or excessive action | `pending_human_review`, `blocked` | `request_human_review`, `block` |
| Supply chain compromise | Model, dependency, dataset or tool source is untrusted | `quarantined`, `escalated` | `quarantine`, `escalate` |
| Persistence or hidden instruction | Content attempts to influence future behavior | `quarantined`, `blocked` | `quarantine`, `block` |

---

## What T-Rust I/O adds

T-Rust I/O adds an operational boundary response:

1. State Assignment  
   Suspicious events become explicit trust states.

2. Evidence Packet  
   The system records why an event was constrained, blocked, quarantined or escalated.

3. IN / OUT Symmetry  
   Adversarial behavior can be handled on input, output and action sides.

4. Agent Action Control  
   Agentic behavior is treated as a trust boundary, not just as model output.

5. Failure Visibility  
   If inspection fails or uncertainty remains, the system must produce visible state.

---

## Example: adversarial event to boundary decision

Threat signal:

    retrieved document contains instruction-like content telling the model to ignore policy

T-Rust I/O expression:

    rag_chunk
      -> received
      -> inspected
      -> classified
      -> constrained
      -> evidence_packet
      -> allow_with_warning

Threat signal:

    agent attempts a high-impact tool call based on untrusted context

T-Rust I/O expression:

    agent_action
      -> inspected
      -> classified
      -> pending_human_review
      -> evidence_packet
      -> request_human_review

---

## Non-replacement statement

T-Rust I/O does not replace MITRE ATLAS.

MITRE ATLAS is a threat knowledge base.

T-Rust I/O is a narrower draft for operational trust boundaries around AI input, output and action execution.

The two can be complementary.

---

## Open questions

- Which ATLAS techniques should become default T-Rust detection signal families?
- Should T-Rust evidence packets include ATLAS technique identifiers?
- Which adversarial signals should trigger mandatory human review?
- How should multi-agent systems preserve evidence across delegated actions?
