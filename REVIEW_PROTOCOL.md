# Review Protocol and Public Evidence Boundary

This note clarifies how the public JSON files should be read alongside the paper.

## Scope

The public release contains three evidence layers:

1. `data/01_candidate_generation`: initial generated candidate UCA and causal-scenario records.
2. `data/02_quality_gate_scoring`: multidimensional quality-gate scoring records used before semantic consolidation.
3. `data/03_expert_delivery_audit`: manual expert extraction, semantic merge review, final delivery audit, expert agreement summary, and item-level agreement sample records.

The paper describes quality gating as a structured review stage before system-level semantic consolidation. Therefore, the `02_quality_gate_scoring` files are public scoring records for the quality-gate stage, while final manual expert audit evidence is reported separately in `data/03_expert_delivery_audit`.

## Manual Expert Audit

The manual expert audit evidence is reported in `data/03_expert_delivery_audit`. These files retain the public parts of the final review process:

- reviewed item text and explicit links;
- expert scoring or audit decisions where applicable;
- rationale fields, issue notes, and suggested revisions;
- semantic merge decisions and final delivery decisions;
- expert semantic agreement review summary, including agreement rate and Cohen's kappa.
- anonymized item-level semantic agreement sample records for the 60 sampled STPA products.

The item-level expert agreement categories are neutral semantic-boundary classification codes. They distinguish clear semantic alignment from boundary semantic alignment for agreement analysis, and should not be read as public acceptance/rejection labels or as a second final-delivery acceptance decision.

The public rationales are structured review summaries prepared from manual review records for auditability.

## Expert Reviewer Privacy

Reviewer identities and personal profile details are not disclosed in the public release.

## Public Sanitization

The result release excludes:

- expert personal identities;
- local working files and local environment metadata;
- non-public operational metadata;
- implementation scripts in this result dataset repository.

Implementation code is maintained separately in `CSG-code`.

## Recommended Citation Wording

Use a bounded statement such as:

```text
The public repository releases the original generated results, quality-gate scoring records, system-level semantic consolidation records, final expert delivery-audit records, expert semantic agreement summary, and item-level semantic agreement sample records in structured JSON format. Implementation code is maintained separately in the CSG-code repository. Expert identities, local files, and non-public operational metadata are not included in the public result release.
```

Avoid claims that go beyond the evidence boundary of the public files.
