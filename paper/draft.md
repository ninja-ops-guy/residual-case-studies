# When Behavior Looks Fine: Failures Behavioral Evals Miss and Run-State Verification Catches

**Draft skeleton — target: systems/security workshop (4–6 pp). Status: DRAFT,
all empirical content already published as case studies CS-0001 / CS-0002 in
this repo; nothing here claims more than those case studies.**

## Abstract
Behavioral evaluations score what an agent produces; they cannot score what the
run did. We present a growing, citable corpus of failures invisible to
behavioral evaluation but caught by verification of the execution substrate —
hash-chained run ledgers, module authorization, gate attestations, sealed
one-shot measurement boundaries. Three seeded failure classes (runnable mock,
3/3 missed by behavioral eval, 3/3 caught by run-state checks) and one grounded
real-program case (D2-0004, a retained negative in a sealed adversarial-apparel
pipeline) instantiate the taxonomy.

## 1. Introduction
- Evaluating agents by outputs vs verifying run state; the two observation
  channels are disjoint by construction.
- Contribution: a corpus with mechanism-level explanations, exact SHAs/seeds,
  and mandatory "not proven" sections. (Paper cites corpus DOI when minted —
  see IDENTIFIERS.md.)

## 2. Threat/failure model
Failure classes in scope: ledger tampering, unauthorized capability use,
gate/boundary bypass, evidence-gap concealment. Out of scope: failures that
alter task outputs (behavioral evals can see those).

## 3. Method
- Substrate model: append-only hash-chained ledger; allowlists; required gates;
  sealed one-shot decision boundaries (RESIDUAL-style).
- Corpus methodology: template, protocol-vs-published fail-closed rule,
  immutable versioning, SHA attestation.

## 4. Case study I: seeded injection (CS-0001)
- Table: 4 scenarios × 2 verdicts; the three findings; full captured output
  referenced by SHA-256. Mechanism: eval reads answer string; failures act on
  run state only.

## 5. Case study II: D2-0004 retained negative (CS-0002)
- Surrogate selection channel vs sealed held-out channel; detection rate
  1.0→1.0 with mean_delta -0.0987; one-shot boundary and step-22 evidence gap
  handled by governance, not by rebuilding outputs.

## 6. Preregistered protocols (D2-0005, physical lane)
- Why publishing protocols instead of results is the correct failure mode for
  a corpus; fallback seeded-failure plan.

## 7. Discussion
- Limits: mocks are not deployed frameworks; single-program grounding;
  adversarial control of the substrate itself is out of scope.
- What a claim would require: N independent frameworks, pre-registered
  detectors, blinded review.

## 8. Related work
- Agent evals, provenance/audit logging, preregistration in security experiments.

## 9. Conclusion
Cite the corpus. Contribute via SUBMISSIONS.md.

## References
- This corpus (URL + commit SHA; DOI pending — see IDENTIFIERS.md).
- ninja-ops-guy/adversarial-clothing-pipeline @ ed106c55438389110ce33a47c17039438e6679b0.
- ninja-ops-guy/residual-agent-harness @ 3cff6bcd52e352a6ba048c958949a7bbb2a039eb.
