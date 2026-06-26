# Glossary

Words matter because unclear language creates unclear systems.

This glossary defines the early vocabulary of T-Rust I/O.

The goal is not to invent new terminology for its own sake.

The goal is to make AI trust boundaries easier to discuss, implement and critique.

---

## AI I/O Trust Boundary

The control layer that governs what may enter an AI system and what may leave it.

## T-Rust I/O

An open, implementation-oriented draft for the AI I/O Trust Boundary Standard.

## T-Rust IN

The input side of the trust boundary.

## T-Rust OUT

The output and action side of the trust boundary.

## Trust State

A machine-readable state assigned to an input, output, action, failure or escalation.

## Evidence Packet

A structured record explaining why a trust decision was made.

## Trust Level

A level that describes enforcement strength, from observation to regulated handling.

## Profile

A modular adoption area, such as IN, OUT, Agent, RAG or Failure Modes.

## Human Review State

A state in which a decision must be reviewed by a human before proceeding.

## No Silent Failure

The principle that a critical trust system must not fail without visible status, explanation and trace.

## No Silent Support Void

The principle that a critical system must not leave users alone inside uncertainty.

## No Dry Status

The principle that status messages should reduce uncertainty and provide useful next steps.

## Support Delay as Trust Boundary

The idea that time, delay and lack of explanation are part of the trust experience and therefore part of the boundary.

## Evidence over claims

The principle that trust decisions should be backed by structured evidence, not only policy statements or marketing language.

## Trust In. Trust Out.

The short form of the T-Rust I/O principle: what enters AI and what leaves AI must pass through a trust boundary.

## Boundary decision

The decision made at the AI I/O trust boundary: allow, constrain, block, quarantine, escalate, request human review or fail with trace.

## Invisible state

A condition where an object, action or failure has no visible trust state.

T-Rust I/O treats invisible critical states as trust risks.
