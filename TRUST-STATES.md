# Trust States

Trust states exist because invisible AI decisions are dangerous.

If a system does not know whether something was received, inspected, trusted, constrained, blocked or escalated, the user is already inside uncertainty.

T-Rust I/O makes that uncertainty visible.

A trust state is not just a label.

It is the system saying: this is where the object is, this is what we know about it, and this is what may happen next.

---

## Purpose

A trust state answers:

- what is this object;
- has it been inspected;
- can it be used;
- can it leave the system;
- does it require constraints;
- does it require human review;
- did something fail visibly.

No critical object should remain invisible.

---

## Initial states

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

---

## Example transition paths

Minimal path:

    received -> inspected -> classified -> trusted

Constrained path:

    received -> inspected -> classified -> constrained -> evidence_packet

Blocked path:

    received -> inspected -> classified -> blocked -> evidence_packet

Human review path:

    received -> inspected -> classified -> pending_human_review -> decision

Failure path:

    received -> failed_with_trace -> status_update -> escalation_path

---

## Required properties

Every trust state should be:

- machine-readable;
- visible to logs;
- explainable to humans;
- connected to evidence;
- connected to a decision;
- timestamped;
- attributable to a profile, rule or policy.

---

## State visibility principle

A trust state should not exist only inside the system.

For critical systems, the state should be visible at the right level:

- machine-readable for automation;
- audit-readable for review;
- human-readable for users and operators.

A user does not need every internal detail.

But the user should not be forced to guess whether the system is working, blocked, uncertain or waiting for review.

---

## Open questions

- Should `trusted` be split into `trusted_low_risk` and `trusted_verified`?
- Should `blocked` and `quarantined` always require human-visible explanation?
- How should state transitions compose across multiple AI agents?
- Should trust states be signed or append-only in regulated environments?
- Which states should be mandatory for minimal compliance?
