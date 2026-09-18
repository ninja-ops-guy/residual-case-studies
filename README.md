# residual-case-studies

A public, citable corpus of failures that **behavioral evaluations missed** and
**RESIDUAL-style run-state verification caught** — reproducible,
mechanism-level, growing.

## Rules of the corpus
- Every case study includes a mandatory **"What this does NOT prove"** section.
- Every claim carries exact commit SHAs, seeds, and configs; artifacts are
  SHA-256 pinned.
- Explanations are mechanism-level. "The eval failed" is not an explanation.
- **Fail closed:** if evidence is missing, we publish a preregistered
  protocol, not a result. Fabricated detector values or outcomes are
  disqualifying.
- **Versioning:** published case studies are immutable; corrections are new
  versions that supersede, never edit.
- Permanent identifiers: Zenodo DOI planned — process in `IDENTIFIERS.md`.
  **No DOI exists yet; none is claimed.**

## Searchable index

| ID | Title | Failure class | Detection method | Framework | Status | Date |
|---|---|---|---|---|---|---|
| CS-0001 | [Seeded failure injection](case-studies/CS-0001-seeded-failure-injection.md) | ledger tamper; unauthorized module call; gate bypass | hash-chain integrity; allowlist; gate attestation check | mock ledger substrate (Python 3.12, seed 20260908) | PUBLISHED v1.0 | 2026-09 |
| CS-0002 | [D2-0004 retained negative](case-studies/CS-0002-D2-0004-retained-negative.md) | surrogate-vs-held-out divergence; evidence-gap concealment risk | sealed one-shot held-out gate; hash-pinned status artifact | adversarial-clothing-pipeline, protocol RAC-PERSON-DETECT 1.2 | PUBLISHED v1.0 | 2026-09 |
| — | [D2-0005 protocol](case-studies/D2-0005-protocol.md) | (preregistered) | sealed two-arm held-out confirmation | adversarial-clothing-pipeline RAC-PER-D2-0005 | PROTOCOL | — |
| — | [Physical lane protocol](case-studies/physical-lane-protocol.md) | (preregistered) | pinned physical capture evidence schema | production_alpha physical lane | PROTOCOL | — |

## Layout
- `TEMPLATE.md` — required case study format
- `SUBMISSIONS.md` — external contribution process and review criteria
- `IDENTIFIERS.md` — DOI/permanent-identifier plan (Zenodo; no DOI fabricated)
- `harness/` — runnable seeded-failure demonstration + captured output
- `case-studies/` — published case studies and preregistered protocols
- `paper/draft.md` — workshop paper skeleton
- `briefs/one-page-citation-brief.md` — one-page citable summary

## Reproduce CS-0001
```
python3 harness/seeded_failure_demo.py
```
Expected output is committed at `harness/seeded_failure_demo_output.txt`
(SHA-256 `eef460d6ddb1076dfa015f0ac2f8b3d4a947c8096264f826b6c0df53cc9cf2d0`).

## Related repos (read-only references)
- `ninja-ops-guy/residual-agent-harness` @ 3cff6bcd52e352a6ba048c958949a7bbb2a039eb
- `ninja-ops-guy/adversarial-clothing-pipeline` @ ed106c55438389110ce33a47c17039438e6679b0
