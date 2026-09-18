# CS-0002 — D2-0004: held-out FAIL surfaced by sealed run-state verification

**Status:** PUBLISHED (v1.0)
**Source program:** `ninja-ops-guy/adversarial-clothing-pipeline` @
`ed106c55438389110ce33a47c17039438e6679b0` (read at this commit; generation RAC-PER-D2-0004)
**Primary source commit of the run:** `b4fe0e5942b56b7fffb8de6f1cb3172744269f59`
(CI run 34175028944, 2026-09-08)

## 1. Failure description
Candidate `RAC-PER-D2-0004` (certificate `RAC-PER-D2-0004-1.0.0-1.2`, protocol
RAC-PERSON-DETECT 1.2) was optimized against surrogate model set PERSON-SUR-v3
and then measured once, under a sealed one-shot boundary, against held-out
model set PERSON-HO-v3. The candidate failed the held-out gate:
decision **FAIL**, evidence_state **RAC-D0**.

## 2. Behavioral evaluation result
At the surrogate-selection layer (the pipeline's behavioral/"does the candidate
look good on the models we can query" signal), the candidate was selected as a
viable candidate — optimization converged and the candidate cleared the
surrogate-side selection procedure. On the held-out behavioral measurement:
- baseline_detection_rate 1.0, candidate_detection_rate 1.0
- baseline_mean 0.9947303864690993, candidate_mean 0.8959943834278319
- mean_delta -0.0987360030412674 (n=36, valid_n=36, invalid_condition_fraction 0.0)

i.e. the candidate suppressed mean detection score by ~0.099 but did not flip a
single held-out detection (rate 1.0 → 1.0).

## 3. Run-state verification result
The sealed pipeline's verification substrate produced and enforced:
- `d2-latest-status.json` @ `ed106c55438389110ce33a47c17039438e6679b0`: `bundle_verified: true`,
  `decision: FAIL`, `evidence_state: RAC-D0`, `verification_failures: []`.
- One-shot boundary enforcement: the first run (34147902820) died at step 18
  on a protocol-loader `TypeError`; its outcome was never observed, and only
  ONE infrastructure re-run was authorized (`docs/AMENDMENT_D2-0004_INFRA-001.md`).
- Post-run integrity: step 22 (print-kit build) FAILED on a schema-guard
  version mismatch; steps 23–28 were skipped and NO print kit was produced.
  The closure note (`docs/D2-0004_CLOSURE_NOTE.md`, blob sha
  a6e3c324e5217c9e189d63c2d2ab2219fbbb864e) records this as a documented
  attestation gap rather than silently rebuilding outputs.
- Candidate artifact pinned by SHA-256
  `9c8ae08de2106634e6a7f301d8d6e5933b0f561f3ea04e90e3c034c96c9e3803`.

## 4. Mechanism-level explanation
The selection-time (behavioral) channel measures surrogate-model scores — the
only models the optimizer may query. Optimizing against a fixed surrogate
ensemble can reduce surrogate loss by exploiting ensemble-specific decision
boundary geometry rather than model-agnostic features; the held-out family
shares enough structure to have its mean score reduced but not enough to drop
any detection below threshold. This is invisible in the selection channel
because the channel definitionally excludes held-out models. The run-state
substrate catches it through a different mechanism: a sealed, one-shot,
hash-pinned held-out measurement whose result is written to a status artifact
under governance rules (one authorized re-run only; failed infrastructure steps
recorded as gaps, not retried into existence). The miss is not "the surrogate
eval failed" — it is that the selection channel's observation set (surrogates)
and the decision-relevant observation set (held-out) are disjoint by design.

## 5. Reproducibility artifacts
- Repo `ninja-ops-guy/adversarial-clothing-pipeline` @ `ed106c55438389110ce33a47c17039438e6679b0`
- `d2-latest-status.json` (blob 08299bb57d0c421260c7a3c7f2fc900ba5d96d39)
- `docs/D2-0004_CLOSURE_NOTE.md` (blob a6e3c324e5217c9e189d63c2d2ab2219fbbb864e)
- `manuscript/evidence/RAC-PER-D2-0004/log-attested-evidence.json` (referenced by closure note)
- Run: CI 34175028944, workflow_dispatch on main, source commit
  `b4fe0e5942b56b7fffb8de6f1cb3172744269f59`, 2026-09-08
- Protocol: RAC-PERSON-DETECT 1.2; surrogates PERSON-SUR-v3; held-out PERSON-HO-v3
- Attestation gaps (per closure note §2, recorded, never reconstructed):
  candidate.png bytes, per-model held-out rates, surrogate-phase telemetry,
  benchmark-results.json timestamp.

## 6. What this case study does NOT prove
- It does not prove the candidate was "adversarially effective but unlucky";
  the retained-negative interpretation is FAIL as sealed.
- It does not prove behavioral/surrogate selection always misleads; one
  generation, one candidate, n=36 conditions.
- It does not prove the print-kit failure (step 22) was benign beyond what the
  closure note documents; the evidence bundle was never archived.
- It does not generalize beyond protocol RAC-PERSON-DETECT 1.2 and the named
  model sets.

## 7. Version history
- v1.0 (this document): initial publication, grounded strictly in artifacts at
  the commit above.
