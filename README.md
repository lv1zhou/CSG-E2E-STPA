# CSG-E2E-STPA Public Result Dataset

This repository provides the public JSON result release for **CSG-E2E-STPA**: a control-structure-guided end-to-end STPA workflow for SOTIF-oriented safety analysis of autonomous driving.

## Paper Context

Chinese title: ???????????SOTIF???????????STPA??

English title: Control-Structure-Guided End-to-End Hazard Identification for Autonomous Driving SOTIF: An LLM-STPA Method

The study uses Automated Valet Parking (AVP) as the experimental system and evaluates four representative control actions: forward drive, parking-slot confirmation, emergency braking, and lateral control. The published results cover UCA identification and causal-scenario reasoning after quality gating, semantic merge, and final expert delivery review.

## Public Files

- `data/summary_metrics.json`: compact experiment-level UC/KC/FDC metrics and expert agreement results.
- `data/uca_expert_review_results.json`: sanitized UCA expert review records.
- `data/causal_scenario_expert_review_results.json`: sanitized causal-scenario expert review records.

## Release Scope

This public release intentionally contains JSON result files only. Implementation scripts, local environment metadata, service identifiers, and source-code files are excluded.

The review records are presented as **manual expert review results**. Each item keeps only the externally readable evidence needed to audit the published result: reviewed item text, explicit links, expert scores, expert rationales, expert issue notes, suggested revisions, and expert semantic-merge decisions.

## Metrics

- **UC**: usable count after expert quality review.
- **KC**: kept count after system-level semantic merge.
- **RR**: semantic-merge retention rate, calculated as KC / UC.
- **FDC**: final deliverable count after final expert delivery audit.

The paper reports 282 semantic-merge-kept STPA products, including 83 UCA records and 199 causal-scenario records. After final expert delivery audit, the overall final retention rate is 96.8%; causal-scenario retention is 100.0%. Expert agreement review on 60 sampled records reports 96.7% agreement and Cohen's kappa of 0.78.
