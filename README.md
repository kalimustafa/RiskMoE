# RiskMoE

**Graph-Guided Sparse Experts for Financial Risk Classification**

[中文说明](README_zh-CN.md) | [Model Card](MODEL_CARD.md) | [Model Download](models/README.md)

RiskMoE is a sentence-level financial risk classification framework for corporate disclosures. It integrates a Transformer encoder, graph-conditioned sparse mixture-of-experts routing, temporally aligned structural context, graph-to-text cross-attention, and gated fusion.

## Overview

Financial risk expressions often share similar vocabulary while their meanings depend on company identity, industry, reporting period, and filing section. RiskMoE introduces structured context without replacing textual evidence.

The model contains:

- Transformer text encoder;
- Top-2 routing over four routed experts;
- one always-active shared expert;
- temporally aligned structural sidecar;
- graph-to-text cross-attention;
- gated late fusion for six-class prediction.

The reported implementation does not use RotatE/HyTE embeddings, graph neural message passing, or pretrained graph embeddings. Graph-guided means that temporally available structural attributes condition routing and fusion.

## Benchmark

| Setting | Value |
|---|---:|
| Training | 125,118 instances |
| Validation | 347 instances |
| Test | 600 instances |
| Routed experts | 4 |
| Top-k routing | 2 |
| Sequence length | 512 tokens |

## Results

| Model | Micro-F1 | Macro-F1 | ECE |
|---|---:|---:|---:|
| Text-only MoE | 0.6633 | 0.6626 | 0.2273 |
| RiskMoE | 0.7150 | 0.7150 | 0.0761 |

RiskMoE improves Micro-F1 by 5.17 percentage points and Macro-F1 by 5.24 percentage points over Text-only MoE while improving confidence calibration.

## Model Download

The official checkpoint release location is:

https://github.com/kalimustafa/RiskMoE/releases

Model weights are not included in the current repository snapshot. Release assets will be uploaded after checkpoint verification. The repository intentionally avoids publishing nonexistent download links.

## Repository Structure

```text
RiskMoE/
├── README.md
├── README_zh-CN.md
├── MODEL_CARD.md
├── models/
│   └── README.md
├── configs/
├── docs/
└── CITATION.cff
```

## Data and Reproducibility

The processed splits, preprocessing rules, temporal cutoff logic, and structural sidecar construction procedures will be released with the verified reproduction package.

## Citation

```bibtex
@article{yi2026riskmoe,
 title={RiskMoE: Graph-Guided Sparse Experts for Financial Risk Classification},
 author={Yi, Xiang},
 year={2026}
}
```

## Contact

Xiang Yi  
Northwest Minzu University  
Email: 1130575372@qq.com
