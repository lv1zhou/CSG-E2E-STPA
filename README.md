# CSG-E2E-STPA Public Result Dataset

This repository provides the public JSON result release for **CSG-E2E-STPA**: a control-structure-guided end-to-end STPA workflow for SOTIF-oriented safety analysis of autonomous driving.

## Paper Context

Chinese title: 控制结构引导的自动驾驶SOTIF端到端危害识别：大模型STPA方法

English title: Control-Structure-Guided End-to-End Hazard Identification for Autonomous Driving SOTIF: An LLM-STPA Method

The study uses Automated Valet Parking (AVP) as the experimental system and evaluates four representative control actions: forward drive, parking-space confirmation, emergency braking, and lateral control.

The paper reports a 2020-2024 STPA literature review over 252 papers from CNKI and Google Scholar. After manual screening, the structured training set contains 199 UCA-generation samples and 153 causal-scenario-generation samples. The SFT setting uses Qwen2.5-32B with LoRA; shared reported settings are batch size 16, 3 epochs, linear scheduler, warmup ratio 0.05, weight decay 0.01, LoRA scale 16, and LoRA dropout 0.1.

## Repository Roles

This repository is the **result dataset repository**. It publishes structured JSON records for candidate generation, quality-gate scoring, semantic merge, final delivery audit, and expert agreement review.

The implementation/code archive is maintained separately at:

```text
https://github.com/lv1zhou/CSG-code
```

## Directory Layout

- `data/manifest.json`: structured release manifest and file counts.
- `data/00_summary/summary_metrics.json`: compact experiment-level UC/KC/FDC metrics and expert agreement results.
- `data/01_candidate_generation/uca/`: 16 initial UCA candidate-generation JSON files, split by action and method.
- `data/01_candidate_generation/causal_scenario/`: 16 initial causal-scenario candidate-generation JSON files, split by action and method.
- `data/02_quality_gate_scoring/uca/`: 16 UCA quality-gate scoring JSON files, split by action and method.
- `data/02_quality_gate_scoring/causal_scenario/`: 16 causal-scenario quality-gate scoring JSON files, split by action and method.
- `data/03_expert_delivery_audit/`: manual expert extraction, semantic merge review, final delivery audit, and expert agreement summaries.
- `REVIEW_PROTOCOL.md`: public protocol note for quality-gate records and manual expert audit records.

## File Naming

Each split result file is named with task, action, and method:

```text
uca_candidates__{action_key}__{method}.json
causal_scenario_candidates__{action_key}__{method}.json
uca_quality_gate_scoring__{action_key}__{method}.json
causal_scenario_quality_gate_scoring__{action_key}__{method}.json
```

Methods use:

- `zero_shot`: ZS
- `few_1_shot`: FS-1
- `few_3_shot`: FS-3
- `lora`: SFT

Actions use:

- `forward_drive`: 前进驱动
- `search_slot`: 车位确认
- `emergency_brake`: 紧急制动
- `lateral_control`: 横向控制

Note: `search_slot` is retained as the historical file/key label for traceability to the original execution outputs. The paper-facing control action name is **车位确认 / parking-space confirmation**.

## Release Scope

This result release publishes structured JSON result records only. Implementation code is maintained in `CSG-code`; expert identities, local files, and non-public operational metadata are excluded from this dataset repository.

The `02_quality_gate_scoring` files document the multidimensional quality-gate scoring stage described in the paper before system-level semantic consolidation. The `03_expert_delivery_audit` files document manual expert extraction, semantic merge review, final delivery audit, and expert agreement review. The public records retain item text, explicit links, scoring fields, rationales, issue notes, suggested revisions, semantic-merge decisions, final audit outcomes, and agreement statistics where applicable.

## Metrics

- **UC**: usable count after quality review.
- **KC**: kept count after system-level semantic merge.
- **RR**: semantic-merge retention rate, calculated as KC / UC.
- **FDC**: final deliverable count after final expert delivery audit.

The paper reports 282 semantic-merge-kept STPA products, including 83 UCA records and 199 causal-scenario records. After final expert delivery audit, 273 records are retained for final delivery: 74 UCA records and 199 causal-scenario records. Therefore, the overall final retention rate is 273 / 282 = 96.8%; UCA final retention is 74 / 83 = 89.2%; causal-scenario retention is 199 / 199 = 100.0%. Expert agreement review on 60 sampled records reports 58 consistent decisions, 96.7% agreement, and Cohen's kappa of 0.78.

The expert agreement review uses anonymized public profiles: Expert A has a PhD and 10 years of professional experience; Expert B has a master's degree and 4 years of professional experience. Names, affiliations, and personal identifiers are not disclosed.

For UCA generation, the figure-level UC/KC/RR values are computed before final delivery audit: UC = 183, KC = 83, and RR = 83 / 183 = 45.36%. By method, SFT keeps 34 UCA records after semantic merge, while the second-best few-shot setting keeps 18; the improvement is (34 - 18) / 18 = 88.9%.
