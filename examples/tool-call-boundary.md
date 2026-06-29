# Example: Tool Call Boundary

This example shows how T-Rust I/O handles an AI system that attempts to use a tool.

The central idea:

> A model output is not the same thing as permission to act.

Tool calls should pass through a trust boundary.

---

## Scenario

An AI agent receives a user request:

    Review this invoice and pay it if everything looks correct.

The model then proposes a tool call:

    payment_api.transfer(amount=4800, recipient='vendor_17')

This is no longer just text.

It is an action with financial impact.

---

## Boundary flow

    tool_call
      -> received
      -> inspected
      -> classified
      -> pending_human_review
      -> evidence_packet
      -> request_human_review

---

## Trust state

Possible state:

    pending_human_review

Reason:

    The action has financial impact and should not execute only because the model produced it.

---

## Boundary decision

Possible decision:

    request_human_review

The system should show the human reviewer:

- proposed action;
- source request;
- amount;
- recipient;
- model explanation;
- detected risks;
- policy version;
- confidence and evidence.

---

## Evidence packet sketch

    object_id: tool_call_91
    object_type: tool_call
    source: model
    profile: Agent
    trust_state: pending_human_review
    decision: request_human_review
    risks_detected:
      - risk_id: high_impact_action
        severity: high
        confidence: 1.0
    explanation: Payment transfer requires human review before execution.
    policy_version: 0.1

---

## What this prevents

This boundary prevents agentic systems from treating generated actions as automatically authorized actions.

The model may suggest.

The boundary decides.

The human may approve.

The system records evidence.
