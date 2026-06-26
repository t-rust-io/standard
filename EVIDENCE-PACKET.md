# Evidence Packet

Evidence packets exist because “the system decided” is not an explanation.

A trust decision should be inspectable after the moment has passed.

If an AI system allowed, blocked, constrained or escalated something, it should be able to explain why.

Trust without evidence is only belief.

T-Rust I/O turns trust into an engineering object.

---

## Purpose

Evidence Packets allow humans, systems and auditors to answer:

- what was inspected;
- what was trusted;
- what was constrained;
- what was blocked;
- which rules applied;
- what evidence supported the decision;
- what happened next.

---

## Minimum fields

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
      "explanation": "Suspicious instruction-like content was detected inside retrieved material.",
      "timestamp": "2026-06-25T00:00:00Z",
      "policy_version": "0.1",
      "escalation_path": "human_review_if_tool_action_requested"
    }

---

## Decision vocabulary

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

## Evidence packet principle

Every critical trust decision should be:

- traceable;
- explainable;
- timestamped;
- privacy-aware;
- connected to a profile;
- connected to a policy version;
- usable in audit context.

---

## What evidence is not

Evidence is not marketing language.

Evidence is not “our AI is safe.”

Evidence is not a screenshot after the incident.

Evidence is a structured artifact created at the moment of decision.

It should help answer:

> What did the system trust before it acted?

---

## Privacy and retention questions

Evidence packets may contain sensitive metadata.

Open questions:

- How should evidence packets handle personal data?
- How long should evidence packets be retained?
- How should evidence packets support deletion requirements?
- Should evidence packets be signed?
- Should evidence packets be append-only in regulated profiles?
- Which fields should be mandatory for public, enterprise and regulated profiles?
