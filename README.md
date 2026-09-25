# Biohub Cell Tracking Research Log

**A publication-safe Everything AI Co research note on 3D cell lineage tracking, reproducible scientific ML, and Kaggle bioimage analysis.**

This repository summarizes our work on Kaggle's `biohub-cell-tracking-during-development` competition. It is written as a public research log rather than a code dump: the goal is to document the scientific reasoning, failure modes, validation problems, and release boundaries behind a high-performing cell-tracking workflow.

The private engineering archive remains closed until competition closeout review. This public repo does **not** redistribute competition data, active submission code, copied notebooks, generated outputs, model weights, credentials, or private logs.

## Abstract

Developmental cell tracking from 3D microscopy time series can be formalized as constrained temporal graph reconstruction: detect cell centers, associate them across time, recover divisions, and produce a valid lineage graph. During the Biohub Kaggle competition, we progressed from classical detection/linking baselines to learned graph pipelines and later public DeepCenter/ILP adaptations. The confirmed public score improved from early baselines around `0.826` to `0.944`. The main scientific lesson is that the July model family saturated around `0.896`, but later public checkpoints and ensemble assets changed the solution class. This repo records the methodological arc, negative results, and publication-safe lessons for reproducible AI research.

## Research Questions

1. **Representation:** Is the problem primarily detection-limited, association-limited, or topology-limited?
2. **Validation:** How should local validation behave when ground truth is sparse and many cells are unannotated?
3. **Optimization:** Which changes improve actual Kaggle score rather than only local proxy metrics?
4. **Operations:** How should active competition code, data, public notebooks, and private outputs be separated for safe publication?

## Main Result

| Stage | Public score / status | Interpretation |
| --- | ---: | --- |
| Early rule-based baseline | `0.826` | Valid notebook workflow and baseline graph generation. |
| Two-pass linker / rule-based improvements | `0.842` | Better motion association improved edge recovery. |
| Learned graph public adaptation | `0.856` | Learned temporal association outperformed pure heuristics. |
| Threshold and short-track tuning | `0.867-0.873` | Reduced over-prediction in the older model family. |
| Advanced public post-processing | `0.889-0.896` | Safe division and topology repair improved the July family. |
| Later DeepCenter/ILP public adaptation | `0.944` | New public assets changed the model-family ceiling. |

## Formal Problem Sketch

Let each movie be a time-indexed 3D volume sequence:

```text
X = {X_t in R^(Z x Y x X)} for t = 0 ... T-1
```

The output is a directed temporal graph:

```text
G = (V, E)
```

where each node `v in V` has `(t, z, y, x)` coordinates and each edge `(u, v) in E` links a parent cell at time `t` to a child/successor at a later time. A biologically plausible graph should satisfy constraints such as:

- one parent per non-root node;
- usually one child per continuing cell;
- up to two children for division events;
- physically plausible displacement in anisotropic micron space.

See [docs/FORMAL_PROBLEM.md](docs/FORMAL_PROBLEM.md).

## Scientific Contributions of This Archive

This public archive contributes:

- a clear distinction between **model-family ceiling** and **competition ceiling**;
- a publication-safe negative-result map;
- documentation of sparse-label metric risks;
- a reproducibility and release-boundary template for active Kaggle competitions;
- a case study in fast adaptation to late public-SOTA notebooks without redistributing sensitive artifacts.

It does not claim novelty for public Kaggle models created by other authors. See [docs/ATTRIBUTION_PUBLIC.md](docs/ATTRIBUTION_PUBLIC.md).

## Document Map

| Document | Purpose |
| --- | --- |
| [Formal Problem](docs/FORMAL_PROBLEM.md) | Mathematical framing of 3D cell lineage tracking as temporal graph reconstruction. |
| [Methods](docs/METHODS.md) | Method families, metric proxy, and operational constraints. |
| [Results and Ablations](docs/RESULTS_AND_ABLATIONS.md) | Score progression and interpretation. |
| [Negative Results](docs/NEGATIVE_RESULTS.md) | Hypothesis, experiment, result, and lesson for failed directions. |
| [Why Later Pipelines Improved](docs/WHY_LATER_PIPELINES_IMPROVED.md) | Scientific explanation for the late jump from `0.896` to `0.944`. |
| [Threats to Validity](docs/THREATS_TO_VALIDITY.md) | Risks from sparse labels, leaderboard feedback, external assets, and hidden tests. |
| [Publication Boundaries](docs/PUBLICATION_BOUNDARIES.md) | What is public now vs private until closeout review. |

## What Is Public Here

- High-level methodology.
- Score progression already visible through Kaggle.
- Negative-result summaries.
- Reproducibility principles.
- Publication boundaries.
- Public asset names and provenance at a non-redistributive level.

## What Remains Private

- Active submission code.
- Copied public notebooks.
- Generated submission CSVs and outputs.
- Competition data.
- Model weights and private datasets.
- Credentials and raw operational transcripts.

## Everything AI Co Positioning

Everything AI Co builds auditable AI workflows for complex technical domains: agent governance, reproducible research, quantitative systems, and scientific machine learning. This project demonstrates our approach to rigorous AI experimentation: document assumptions, preserve negative results, separate public claims from private artifacts, and move fast when the public baseline changes.

## Keywords

Kaggle, Biohub, cell tracking, 3D microscopy, bioimage analysis, cell lineage reconstruction, temporal graph reconstruction, scientific machine learning, reproducible ML, graph tracking, ILP tracking, DeepCenter, temporal UNet, Everything AI Co.
