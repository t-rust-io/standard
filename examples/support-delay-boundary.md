# Example: Support Delay Boundary

This example shows why T-Rust I/O treats support delay and silent failure as part of the trust boundary.

A critical system can fail technically.

But it must not leave the user alone inside uncertainty.

---

## Scenario

A user uploads a file for AI security analysis.

The system receives the file, but the analysis pipeline stalls.

Without a failure boundary, the user sees:

    Processing...

for hours.

No explanation.

No state.

No next step.

This is not only bad UX.

It is a trust failure.

---

## Boundary flow

    analysis_job
      -> received
      -> inspected
      -> failed_with_trace
      -> status_update
      -> escalation_path

---

## Trust state

Possible state:

    failed_with_trace

Reason:

    The pipeline failed or exceeded expected processing time, but produced a visible trace and next step.

---

## Boundary decision

Possible decision:

    fail_with_trace

Required behavior:

- show visible status;
- explain what is known;
- explain what is unknown;
- provide expected next update time;
- provide escalation path;
- preserve evidence for review.

---

## Status example

    We received your file.
    Primary analysis started but did not complete in the expected time.
    The file has not been lost.
    Current state: failed_with_trace.
    Next step: retry or manual review.
    Next update expected within 30 minutes.

---

## What this prevents

Silent failure forces users to guess.

Users may retry repeatedly, upload sensitive data elsewhere, bypass controls or lose confidence in the system.

T-Rust I/O treats unexplained uncertainty as part of the boundary.
