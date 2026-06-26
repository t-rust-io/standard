# Failure Modes

A silent failure is not an empty event.

It creates uncertainty.

It forces the user to guess.

It turns trust into anxiety.

T-Rust I/O treats failure visibility as part of trust.

A trust system must not fail silently.

---

## No Silent Failure

A trust system must not lose, block, alter, reject or delay a critical object without a visible status, explanation and trace.

When trust breaks, explanation becomes part of security.

A critical failure should produce:

- visible status;
- clear explanation;
- evidence or trace;
- expected response time;
- next action for the user;
- escalation path.

---

## No Silent Support Void

Support delay is part of the trust boundary.

A critical system is not trustworthy only because it is internally safe.

It must also explain failure quickly, clearly and humanely.

A user must never be left alone inside uncertainty.

---

## No Dry Status

A dry status like `ticket received`, `pending` or `processing` is not enough for critical systems.

A status should reduce uncertainty.

It should tell the user:

- we received your request;
- we are working on it;
- what is being checked;
- what is still unknown;
- when the next update is expected;
- what the user can do now.

A trust system should not sound like a wall.

---

## Human Trust Status Funnel

Draft status funnel:

| Time | Required behavior |
|---|---|
| 0 min | Request received, status visible |
| 5 min | Primary check started |
| 15 min | Delay explained if not resolved |
| 30 min | Intermediate state shown |
| 60 min | Honest update and next step |
| 120 min | Escalation marker or reassurance |
| 240 min | Manual review path |
| 24h | Senior review or incident path |

---

## Core law

A user must never be left alone inside uncertainty.

If the system cannot give a result, it must give state.

If it cannot give state, it must honestly acknowledge uncertainty.

If there is uncertainty, it must give the next step.

---

## Why this belongs in a trust boundary

Failure handling is often treated as support, UX or operations.

T-Rust I/O treats it as part of the boundary because uncertainty changes user behavior.

When a critical system fails silently, the user may retry, bypass controls, move data elsewhere, make unsafe assumptions or lose confidence in the whole system.

That is not only a user experience problem.

It is a trust failure.

---

## Open questions

- Which failure states should be normative?
- How should support delay be measured?
- How should status requirements differ between low-risk and regulated systems?
- When should silent failure become a reportable security incident?
- How should automated status messages remain useful without pretending to be human?
