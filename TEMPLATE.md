# Case Study Template (v1)

Copy this file for every new case study. Sections marked MANDATORY may not be
removed. A case study that cannot fill a section with real, referenced
material must be submitted as a PREREGISTERED PROTOCOL instead (set
`Status: PROTOCOL`).

---
**Case Study ID:** CS-XXXX
**Title:**
**Status:** PUBLISHED | PROTOCOL | SUPERSEDED
**Version:** 1.0
**Date:**
**Framework under test:** (agent framework / harness / model, with versions)

## 1. Failure description
What failed, in mechanical terms. What the agent was supposed to do, what the
run actually did. No narrative gloss.

## 2. Behavioral evaluation result (MANDATORY)
The behavioral eval applied, its exact configuration, and its verdict.
Show the eval output. State precisely what the eval observed and scored.

## 3. Run-state verification result (MANDATORY)
The run-state / substrate checks applied (ledger integrity, authorization,
gate attestations, state invariants), their exact configuration, and their
verdicts. Show the check output.

## 4. Mechanism-level explanation (MANDATORY)
Why the behavioral eval missed the failure, stated at the level of the eval's
observation and scoring mechanism: what information channel the eval reads,
why the failure does not alter that channel, and what channel the run-state
check reads instead. "The eval failed" or "objective A beat objective B" are
not acceptable explanations.

## 5. Reproducibility artifacts (MANDATORY)
- Exact commit SHA(s) of every repository involved
- Seeds, configuration files (with SHA-256), environment (OS, runtime version)
- Exact commands and their captured outputs
- SHA-256 of every artifact referenced

## 6. What this case study does NOT prove (MANDATORY)
Explicit list of claims this evidence cannot support (e.g., generality across
frameworks, prevalence, novel-attack coverage, statistical significance).

## 7. Version history
Immutable once PUBLISHED. Corrections ship as a new version of the case study
with the prior version marked SUPERSEDED, never edited in place.
