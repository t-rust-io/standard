# T-Rust I/O Profiles

Not every system needs the full T-Rust I/O stack on day one.

But every system can start by making one boundary visible.

Profiles exist so adoption can begin with a narrow surface and expand over time.

A team may start with document ingestion, then add RAG trust, then tool-call boundaries, then human review and failure-mode handling.

The goal is not to force everything at once.

The goal is to make trust visible where risk already exists.

---

## IN Profile

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

## OUT Profile

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

## Agent Profile

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

## RAG Profile

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

## Failure Modes Profile

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

---

## Adoption path

Suggested adoption sequence:

1. Start with visibility.
2. Add trust states.
3. Add evidence packets.
4. Add IN profile.
5. Add OUT profile.
6. Add Agent or RAG profile.
7. Add Failure Modes profile.
8. Add mappings and audit requirements.

---

## Profile principle

A profile should be useful alone.

A profile should also compose with other profiles.

For example:

- RAG Profile without OUT Profile can inspect sources but may not govern actions.
- OUT Profile without IN Profile can block actions but may not understand poisoned context.
- Agent Profile without Failure Modes Profile may control tools but still fail silently.
- Full T-Rust I/O combines IN, OUT, evidence, review and failure visibility.
