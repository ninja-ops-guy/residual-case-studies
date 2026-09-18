# One-page citation brief: residual-case-studies corpus

**What it is.** A public, versioned corpus of failures that behavioral
evaluations of agents *missed* and run-state verification (hash-chained run
ledgers, module allowlists, gate attestations, sealed measurement boundaries)
*caught*. Repo: `ninja-ops-guy/residual-case-studies`. Cite by URL + commit
SHA; DOI via Zenodo is planned, not yet minted (see IDENTIFIERS.md).

**Why infrastructure teams can cite it.**
- **Mechanism-level, not anecdotal.** Every case study explains the miss at
  the observation-channel level: what the eval reads, why the failure never
  enters that channel, what the run-state check reads instead.
- **Reproducible.** CS-0001 ships runnable code + captured output
  (3 injected failure classes; behavioral eval PASS, run-state FAIL on all 3;
  fixed seed, stdlib Python, exact SHA-256 of code and output).
- **Real grounding.** CS-0002 documents D2-0004, a sealed FAIL / retained
  negative in a production research pipeline, with exact commit SHAs, CI run
  ID, and pinned artifact hashes — including an honestly recorded evidence gap.
- **Fails closed.** Where experiments haven't run (D2-0005, physical lane),
  the corpus publishes preregistered protocols, not results. Fabricated
  numbers are disqualifying.

**Suggested citation (until DOI):**
> RESIDUAL Case Studies Corpus, ninja-ops-guy/residual-case-studies,
> commit <SHA of cited version>, case study CS-XXXX vX.Y.

**What it does not claim:** prevalence estimates, cross-framework generality,
or that behavioral evals are unnecessary — only that output-only evaluation is
structurally blind to run-state failures.
