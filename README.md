# CSG-E2E-STPA Public Result Dataset

This repository provides the public JSON result release for **CSG-E2E-STPA**: a control-structure-guided end-to-end STPA workflow for SOTIF-oriented safety analysis of autonomous driving.

## Paper Context

Chinese title: 控制结构引导的自动驾驶SOTIF端到端危害识别：大模型STPA方法

English title: Control-Structure-Guided End-to-End Hazard Identification for Autonomous Driving SOTIF: An LLM-STPA Method

The study uses Automated Valet Parking (AVP) as the experimental system and evaluates four representative control actions: forward drive, parking-slot search, emergency braking, and lateral control.

## Directory Layout

- `data/manifest.json`: structured release manifest and file counts.
- `data/00_summary/summary_metrics.json`: compact experiment-level UC/KC/FDC metrics and expert agreement results.
- `data/01_candidate_generation/uca/`: 16 initial UCA candidate-generation JSON files, split by action and method.
- `data/01_candidate_generation/causal_scenario/`: 16 initial causal-scenario candidate-generation JSON files, split by action and method.
- `data/02_expert_quality_scoring/uca/`: 16 manual expert UCA scoring JSON files, split by action and method.
- `data/02_expert_quality_scoring/causal_scenario/`: 16 manual expert causal-scenario scoring JSON files, split by action and method.
- `data/03_expert_delivery_audit/`: final manual expert extraction, semantic merge, final delivery audit, and expert agreement summaries.

## File Naming

Each split result file is named with task, action, and method:

```text
uca_candidates__{action_key}__{method}.json
causal_scenario_candidates__{action_key}__{method}.json
uca_expert_scoring__{action_key}__{method}.json
causal_scenario_expert_scoring__{action_key}__{method}.json
```

Methods use:

- `zero_shot`: ZS
- `few_1_shot`: FS-1
- `few_3_shot`: FS-3
- `lora`: SFT

Actions use:

- `forward_drive`: 前进驱动
- `search_slot`: 搜索车位
- `emergency_brake`: 紧急制动
- `lateral_control`: 横向控制

## Release Scope

This public release intentionally contains JSON result files only. Implementation scripts, local environment metadata, service identifiers, request identifiers, model debug payloads, raw response payloads, and source-code files are excluded.

The review records are presented as **manual expert review results**. Each scoring file keeps externally readable evidence for auditing the published results: reviewed item text, explicit links, expert scores, expert rationales, expert issue notes, suggested revisions, and expert semantic-merge decisions.

## Metrics

- **UC**: usable count after expert quality review.
- **KC**: kept count after system-level semantic merge.
- **RR**: semantic-merge retention rate, calculated as KC / UC.
- **FDC**: final deliverable count after final expert delivery audit.

The paper reports 282 semantic-merge-kept STPA products, including 83 UCA records and 199 causal-scenario records. After final expert delivery audit, the overall final retention rate is 96.8%; causal-scenario retention is 100.0%. Expert agreement review on 60 sampled records reports 96.7% agreement and Cohen's kappa of 0.78.
