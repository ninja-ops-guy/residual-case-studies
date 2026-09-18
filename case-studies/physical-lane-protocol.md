# CS-PROTOCOL — physical lane (production_alpha / print-test) case-study protocol

**Status:** PROTOCOL
**Scope:** physical lane of `ninja-ops-guy/adversarial-clothing-pipeline`
(read @ `ed106c55438389110ce33a47c17039438e6679b0`).

## Why this is a protocol, not a case study
No measured physical evidence exists at the read commit. `production_alpha/`
contains ordering/QA scaffolding only (ORDER_CHECKLIST.md, ORDER_WORKSHEET.md,
PRINTFUL_PRODUCT_RESOLUTION.md, RECEIPT_QA_FORM.md, SKU_MANIFEST.json);
`docs/BARRIER3_REHEARSAL.md` records `physical_test_executed = false` and
`physical_efficacy_claimed = false`. The operative sealed physical kit remains
the RAC-PER-D2-0003 kit referenced by `production_alpha/SKU_MANIFEST.json`;
D2-0004 produced no print kit (its step 22 failed; see CS-0002).

## Planned case study (to execute when a physical print test closes)
1. **Fabrication parameters (fixed in advance):** vendor/SKU resolution per
   `production_alpha/PRINTFUL_PRODUCT_RESOLUTION.md`; garment SKUs per
   `production_alpha/SKU_MANIFEST.json`; print file pinned by SHA-256 before
   ordering; no post-hoc print substitution.
2. **Test conditions:** capture conditions logged per
   `production_alpha/RECEIPT_QA_FORM.md` (lighting, camera, distance, angles);
   detector = a frozen held-out person-detector set with model-lock hashes
   recorded before any physical capture.
3. **Evidence schema:** for each capture — capture_id, garment SKU, print-file
   SHA-256, camera model, lux estimate, distance, detector model-lock hash,
   per-frame detection score, detection decision. Raw frames retained; the
   evidence bundle hash-pinned at close.
4. **Case-study question:** does digital-layer surrogate behavior (the
   behavioral channel) predict physical held-out detection (the run-state
   sealed measurement), and where the two channels diverge, at what mechanism
   level (print/capture transform, threshold geometry, ensemble specificity)?
5. **Seeded-failure fallback:** if the physical test is never executed,
   CS-0001's harness is re-run with an injected "physical evidence gap" class
   (missing attestation for a required capture), published as a substrate-level
   case study and explicitly not a physical-efficacy claim.

## What publication of this protocol does NOT prove
It fixes fabrication parameters, test conditions, and the evidence schema in
advance. It asserts nothing about physical adversarial efficacy.
