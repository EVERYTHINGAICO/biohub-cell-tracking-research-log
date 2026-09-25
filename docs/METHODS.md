# Methods

This public methods note describes the approach family without redistributing active competition code.

## Submission Mechanics

The competition requires notebook-generated submissions. A local CSV upload is not equivalent to a valid competition submission. Therefore, the operational pipeline had to:

- run inside Kaggle;
- produce `/kaggle/working/submission.csv`;
- satisfy no-internet and GPU constraints for final notebook runs;
- preserve exact kernel version and submission reference.

## Metric-Aware Validation

Local validation must account for sparse labels. In sparse ground truth, many real cells are not annotated. A predicted edge touching an unannotated cell may be ignored by the official-like metric rather than counted as a false positive.

This implies that naive precision/recall estimates can be misleading. A useful proxy must:

- match nodes per frame in physical micron space;
- map predicted edges through matched nodes;
- score only comparable edges;
- account for over-prediction where the metric does so.

## Method Families

### Rule-Based Baselines

Rule-based systems used blob/cell candidate detection followed by geometric linking. These established baseline validity and helped identify the importance of edge recovery.

### Learned Graph Pipelines

Public learned graph pipelines used temporal models to generate detections and learned edge probabilities. Graph optimization and topology repair then selected a biologically plausible lineage graph.

### Post-Processing

Post-processing explored:

- short-track filtering;
- gap recovery;
- motion relinking;
- safe division recovery;
- line-fit smoothing;
- density-aware geometric gates.

### Late Public-SOTA Adaptation

Later public notebooks added stronger center priors, independent temporal seeds, division gates, bidirectional fusion, and optimized ILP execution. These methods changed the solution class and produced the final confirmed `0.944` public score for our account.

## Reproducibility Principle

For each serious result, record:

- kernel slug and version;
- submission ref;
- public score;
- public asset provenance;
- runtime constraints;
- whether the score is ours or a public notebook claim.
