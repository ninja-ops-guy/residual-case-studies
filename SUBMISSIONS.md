# External Submissions

We accept external case studies of failures that behavioral evaluations missed
and run-state / execution-substrate verification caught.

## Process
1. Open an issue titled `SUBMISSION: <short title>` with the completed
   `TEMPLATE.md` content.
2. Maintainers review (criteria below). Review is public.
3. Accepted submissions land as `case-studies/CS-XXXX-<slug>.md` via PR with
   an exact base/head SHA attestation and a SHA-256 manifest of all artifacts.
4. Rejected submissions get a written reason referencing the criteria.

## Review criteria
- **Mechanism level.** The explanation of the eval miss must be at the
  observation/scoring-channel level. Narrative explanations are rejected.
- **Reproducibility.** Exact commit SHAs, seeds, configs, environment, and
  runnable artifacts. Reviewers must be able to re-run.
- **Fail-closed evidence rule.** If any claim cannot be backed by an included
  artifact, the claim must be removed or the submission converted to a
  PROTOCOL. Fabricated detector values, outputs, or experiment outcomes are
  disqualifying and are recorded publicly.
- **"Not proven" section present and honest.**

## Versioning
Published case studies are immutable. Corrections or extensions are submitted
as new versions (`Version: X.Y`) that supersede, never modify, the original.
