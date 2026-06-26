# Roadmap

This roadmap is not only about adding documents.

It is about turning a phrase into a working public standard.

T-Rust I/O starts with a simple claim:

> AI systems need a visible input/output trust boundary.

The roadmap describes how that claim becomes language, structure, schemas, examples, mappings and implementation profiles.

---

## Phase 0 — Public draft foundation

Status: started.

- README positioning
- Memorandum
- Standard v0.1
- Trust States
- Evidence Packet
- Failure Modes
- Profiles
- Glossary

---

## Phase 1 — Prior art and mapping layer

- Publish prior-art gap analysis
- OWASP mapping
- NIST AI RMF mapping
- Google SAIF mapping
- MITRE ATLAS mapping
- Product and competitor map
- Academic research map

Purpose:

Show that T-Rust I/O does not ignore existing work.

It should build on OWASP, NIST, SAIF, MITRE ATLAS and academic research while defining its own narrower implementation layer.

---

## Phase 2 — Schemas

- Evidence packet JSON schema
- Trust event JSON schema
- Trust state transition examples
- Profile-specific schemas

Purpose:

Turn trust language into machine-readable artifacts.

---

## Phase 3 — Examples

- RAG poisoning boundary
- Tool call boundary
- Document ingestion boundary
- Support delay boundary
- Agent action boundary
- Multi-agent trust composition

Purpose:

Make the standard understandable to builders.

A standard without examples becomes theory.

---

## Phase 4 — RFC process

- RFC-0001: AI Input/Output Trust Boundary
- GitHub Discussions
- Contributor guidance
- External critique request

Purpose:

Invite criticism before claiming maturity.

T-Rust I/O should be hardened by challenge, not protected from it.

---

## Phase 5 — Reference implementation direction

- Define implementation requirements
- Define language-agnostic boundary behavior
- Define Rust-backed implementation profile
- Keep implementation details separate from public standard claims

Purpose:

Show a path from draft to implementation without overclaiming.

Rust is the foundation.

Evidence is the trust.

---

## Phase 6 — Community and adoption

- Invite critique from AI security researchers
- Invite critique from Rust security engineers
- Invite critique from agent framework builders
- Invite critique from RAG system builders
- Prepare implementation notes
- Prepare public examples

Purpose:

Make the idea visible outside the repository.

GitHub alone is not enough.

The standard needs discussion, critique and practical pressure.
