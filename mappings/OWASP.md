# Mapping: OWASP GenAI / LLM Security

This document maps T-Rust I/O to OWASP GenAI and LLM application security work.

This is not an official OWASP mapping.

It is an implementation-oriented bridge showing how OWASP-style AI application risks can be expressed as trust states, evidence packets and boundary decisions inside T-Rust I/O.

---

## What OWASP provides

OWASP helps the industry name, understand and mitigate important security risks in LLM and GenAI applications.

OWASP is especially useful for:

- identifying common AI application vulnerabilities;
- naming attack classes;
- explaining security risks to builders;
- guiding secure design and testing;
- helping teams prioritize mitigations.

T-Rust I/O does not replace OWASP.

It uses OWASP-style risk language as one possible input into boundary decisions.

---

## Where T-Rust I/O fits

OWASP names important risks.

T-Rust I/O asks:

> What should the system do at the boundary when this risk appears?

The T-Rust I/O layer turns a risk signal into:

- a trust state;
- an evidence packet;
- a decision;
- an optional constraint;
- an optional escalation path;
- an optional human review state.

---

## Core relationship

    OWASP risk signal
      -> T-Rust inspection
      -> trust state
      -> evidence packet
      -> boundary decision
      -> OUT / block / constrain / escalate

---

## Example mapping

| OWASP-style risk area | T-Rust I/O boundary concern | Possible trust state | Possible decision |
|---|---|---|---|
| Prompt injection | Input or retrieved content attempts to override instructions | `constrained`, `quarantined`, `blocked` | `constrain`, `quarantine`, `block` |
| Sensitive information disclosure | Output may expose protected or private information | `constrained`, `blocked` | `constrain`, `block`, `request_human_review` |
| Supply chain risk | Tool, plugin, model, dependency or external component is not trusted | `quarantined`, `pending_human_review` | `quarantine`, `request_human_review` |
| Data or model poisoning | Input data or RAG source may manipulate model behavior | `constrained`, `quarantined` | `constrain`, `quarantine` |
| Insecure output handling | Model output is treated as executable or trusted downstream input | `constrained`, `blocked` | `constrain`, `block` |
| Excessive agency | AI action exceeds intended permission or authority | `pending_human_review`, `blocked` | `request_human_review`, `block` |
| System prompt leakage | Output may reveal hidden instructions or protected configuration | `blocked`, `constrained` | `block`, `constrain` |
| Vector and embedding weakness | Retrieved chunks may be poisoned, misleading or adversarial | `constrained`, `quarantined` | `constrain`, `quarantine` |
| Misinformation | Output may be unsupported, misleading or low-evidence | `constrained` | `allow_with_warning`, `constrain` |
| Unbounded consumption | Request may create uncontrolled cost, latency or resource usage | `constrained`, `blocked` | `constrain`, `block` |

---

## What T-Rust I/O adds

T-Rust I/O adds an operational layer around OWASP-style risks:

1. Trust States  
   Risks are not only listed. They become visible system states.

2. Evidence Packets  
   Decisions are backed by structured evidence.

3. IN / OUT Boundary  
   The same trust model applies to what enters AI and what leaves AI.

4. Agent and Tool Actions  
   Risk signals can constrain or block actions, not only text responses.

5. Failure Visibility  
   If the system cannot decide safely, it must not fail silently.

---

## Non-replacement statement

T-Rust I/O does not replace OWASP.

OWASP is a major source of AI application security language and risk categories.

T-Rust I/O is a draft boundary model that can help systems operationalize such risks as states, evidence and decisions.

---

## Open questions

- Which OWASP risk categories should become default T-Rust rule families?
- Should T-Rust I/O maintain versioned mappings for specific OWASP releases?
- Which OWASP risks should require mandatory evidence packets?
- Which OWASP risks should require human review in regulated profiles?
