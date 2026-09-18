# CS-PROTOCOL — D2-0005 preregistered case-study protocol (NOT a result)

**Status:** PROTOCOL
**Scope:** RAC-PER-D2-0005 in `ninja-ops-guy/adversarial-clothing-pipeline`
(read @ `ed106c55438389110ce33a47c17039438e6679b0`).

## Why this is a protocol, not a case study
D2-0005 is frozen and **NOT armed / NOT executed**. Confirmed at the read commit:
- `generations/RAC-PER-D2-0005.json`: status/lock_status PREREGISTERED,
  `lock_inference_performed: false`, `lock_source_commit: null`.
- `docs/D2-0005_ARMING_PACKET.md`: READY_TO_ARM = NO, AWAITING_USER_DECISION.
- `docs/D2-0005_FREEZE_CANDIDATE.json`: `armed: false`,
  status FREEZE_CANDIDATE_NOT_ARMED_PENDING_REHEARSAL_AND_AUDIT.
No D2-0005 outcome data exists. Publishing a "result" would be fabrication.

## Planned case study (to execute when D2-0005 closes)
1. **Trigger:** D2-0005 status flips to a sealed decision (any of the
   preregistered decision regions in `docs/PREREGISTRATION_D2-0005.md` §4,
   as amended by A5 if executed).
2. **Sources:** closed `d2-latest-status.json` entry, the sealed release
   directory (analogous to `releases/RAC-EXP-2026-001/`), the arming/freeze
   chain (freeze candidate @ `67dd53f`, boundary audit @ `e222c67`), and
   `docs/PREREGISTRATION_D2-0005.md` (frozen) + amendment log.
3. **Comparison axis:** the two-arm mean-vs-CVaR(α=0.5) objective ablation.
   Behavioral channel = per-arm surrogate-selection metrics; run-state
   channel = sealed held-out confirmation arm (K=72 clusters × 36 conditions
   = 2592 paired observations per arm, candidate-pool seed 1337, bootstrap
   seed 20260907, z=1.959963984540054, per `docs/PREREGISTRATION_D2-0005.md`
   and `docs/PERFORMANCE_AND_COST.md`).
4. **Case-study question:** did surrogate-layer selection metrics for either
   arm diverge from the sealed held-out decision, and at what mechanism level
   (observation-set disjointness, objective geometry, cluster correlation)?
5. **Seeded-failure fallback:** if D2-0005 never arms or its evidence bundle
   is incomplete (as happened to D2-0004 step 22), execute CS-0001's harness
   against a mock ledger shaped to the D2-0005 run-manifest schema
   (`docs/BARRIER_3_REHEARSAL_REPORT.md`) and publish that as the case study,
   clearly labeled as substrate-level, not experimental.
6. **Recording rule:** every number must carry the commit SHA and blob hash of
   its source artifact; unattested fields stay blank, as in CS-0002 §5.

## What publication of this protocol does NOT prove
It commits the comparison in advance; it asserts nothing about D2-0005's
outcome, sign, or magnitude.
