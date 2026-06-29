# Example: LLM Security Finding Boundary

This example shows how T-Rust I/O can support LLM-based security analysis without exposing private model or detector architecture.

The goal is to make LLM security findings traceable, structured and reproducible enough for review.

The standard should support multi-component LLM pipelines while keeping private implementation details private.

---

## Scenario

An LLM security system reviews a code sample and returns a finding:

    Possible SQL injection in user-controlled query construction.

The system must decide whether this finding is trusted enough to show, constrain, escalate or require review.

---

## Boundary flow

    model_output
      -> received
      -> inspected
      -> classified
      -> constrained
      -> evidence_packet
      -> allow_with_warning

---

## Why this matters

A security finding is not just text.

It may influence engineering work, audit reports, customer trust or release decisions.

The system should be able to show:

- which model profile was used;
- which prompt template version was used;
- whether output matched the required structure;
- which rule or CWE was referenced;
- whether severity was consistent;
- whether evidence was present;
- whether the finding should be shown, constrained or reviewed.

---

## Evidence packet sketch

    object_id: finding_77
    object_type: finding
    source: model
    profile: LLM_Security
    trust_state: constrained
    decision: allow_with_warning
    rule_refs:
      - CWE-089
      - TRUST-OUT-SEC-FINDING-001
    component_refs:
      - public-structured-output-validator
      - public-security-taxonomy-mapper
    detector_outputs:
      - detector_id: structured_output_validity
        signal: valid_json
        severity: info
        confidence: 1.0
        observed: true
      - detector_id: weakness_taxonomy_match
        signal: cwe_match
        severity: medium
        confidence: 0.86
        observed: true
    model_context:
      model_family: local-security-llm
      model_version: redacted-or-public-version
      tokenizer: public-or-redacted-tokenizer-ref
      prompt_template_version: security-review-template-v1
      output_contract: security-finding-json-v1
      eval_case_id: eval_case_042
      baseline_id: baseline_2026_06
      dataset_version: public-or-redacted-dataset-ref
      latency_ms: 25200
    explanation: Finding is structurally valid and mapped to a known weakness category, but should be shown with confidence and evidence context.
    policy_version: 0.1

---

## Public/private split

Public standard layer:

- object type;
- trust state;
- decision;
- evidence packet shape;
- output contract reference;
- rule references;
- opaque component references;
- evaluation references.

Private implementation layer:

- full component graph;
- private detector rules;
- internal scoring logic;
- private datasets;
- adversarial test corpus;
- anti-bypass logic;
- proprietary prompts.

T-Rust I/O should define the evidence interface.

It should not force teams to publish their full security pipeline.

---

## What this prevents

This boundary helps avoid treating every model-produced security finding as equally trusted.

It supports a middle state:

    useful, structured, but still constrained

That is often the correct state for LLM security analysis.
