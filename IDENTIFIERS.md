# Permanent identifiers plan

This corpus is designed to be citable. Process (to be executed by a
maintainer with Zenodo access; **no DOI exists yet — none is claimed**):

1. Tag a release (`v1.0.0-corpus`) once the first three case studies are
   merged to `main`.
2. Enable the Zenodo-GitHub integration for this repository and publish the
   release; Zenodo mints a version DOI and a concept DOI.
3. Record the minted DOIs here and in `README.md` **after minting**. The
   recorded DOI must resolve; unresolved DOIs must never be committed.
4. Each case study additionally cites: (a) the corpus release DOI, (b) the
   exact commit SHA of the case study file, (c) the SHA-256 blob manifest in
   the merge PR.

Until step 3 completes, cite this corpus by repository URL + commit SHA.
