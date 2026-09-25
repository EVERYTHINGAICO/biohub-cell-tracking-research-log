# Biohub Cell Tracking Research Log

**Everything AI Co public research note on 3D cell tracking, Kaggle bioimage analysis, and reproducible scientific ML.**

This repository is a public-facing summary of our work on Kaggle's `biohub-cell-tracking-during-development` competition. It explains what we investigated, what failed, what improved, and what we learned about building robust cell lineage tracking systems under notebook-only competition constraints.

It intentionally does **not** include competition data, copied notebooks, private outputs, model weights, active submission code, or credentials. The detailed engineering archive remains private until competition closeout and publication review.

## Why This Project Matters

Tracking cells during development is not only an image segmentation task. It is a graph reconstruction problem:

- detect candidate cell centers in anisotropic 3D microscopy volumes;
- connect cells across time into biologically plausible lineages;
- recover or reject division events;
- preserve graph topology constraints;
- generate a reproducible Kaggle notebook submission.

The project became a case study in scientific ML operations: metric reconstruction, sparse-label validation, public-notebook adaptation, leaderboard drift, negative results, and safe release boundaries.

## Public Status

| Item | Status |
| --- | --- |
| Competition | `biohub-cell-tracking-during-development` |
| Public score improved during project | from early baselines around `0.826` to a confirmed `0.944` closeout submission |
| Current public repo contents | narrative, scientific lessons, release policy |
| Excluded until closeout | active submission code, private kernel archive, outputs, copied notebooks, model weights |

## High-Level Method Families Explored

We investigated several families of approaches:

1. **Rule-based detection and linking**
   - Difference-of-Gaussian style cell candidate detection.
   - Hungarian and motion-aware linking.
   - Submission formatting and local validation.

2. **Learned graph pipelines**
   - Temporal UNet / node-transformer style public notebook adaptations.
   - ILP-constrained graph selection.
   - Edge and division-aware graph repair.

3. **Post-processing and topology repair**
   - short-track filtering;
   - safe division recovery;
   - gap recovery;
   - motion relinking;
   - density-aware geometry.

4. **Training and representation experiments**
   - local 3D UNet detector attempts;
   - appearance-based edge classifiers;
   - pseudo-label distillation;
   - self-supervised patch features;
   - T4 training experiments.

5. **Late public-SOTA adaptation**
   - newer public DeepCenter/temporal-UNet/DivNet/ILP pipelines appeared near closeout;
   - these changed the achievable score ceiling and improved our confirmed public score to `0.944`.

## Key Scientific Lessons

- **Sparse labels change validation.** Predictions touching unannotated cells may be ignored by the metric instead of counted as false positives. Local validation must model this carefully.
- **Detection quality and graph quality are coupled.** Better cell center priors can improve downstream lineage edges even when the tracker is unchanged.
- **Negative results are valuable.** Several plausible routes, including appearance-only linking and self-supervised patch representations, did not provide enough independent signal.
- **A model-family ceiling is not a competition ceiling.** Our July pipeline family saturated around `0.896`, but later public assets changed the solution class.
- **Public leaderboard ecosystems move fast.** Near the end of a Kaggle competition, new public datasets, checkpoints, and notebooks can redefine the practical baseline.
- **Release hygiene matters.** Data, credentials, copied notebooks, generated outputs, and active submission code require careful handling.

## Why Some Details Are Private For Now

The competition was still active when this public note was prepared. Kaggle competitions have rules around code sharing, data redistribution, and notebook submissions. To respect those constraints, this repo excludes:

- competition data;
- generated submission CSVs;
- model weights;
- private Kaggle datasets;
- copied public notebooks;
- private agent transcripts;
- active kernel code and operational submission details.

After the competition closes, we plan to review what can be safely published with proper attribution.

## Documents

- [What We Tried](docs/WHAT_WE_TRIED.md)
- [Why the Later Public Pipelines Improved](docs/WHY_LATER_PIPELINES_IMPROVED.md)
- [Publication Boundaries](docs/PUBLICATION_BOUNDARIES.md)

## About Everything AI Co

Everything AI Co builds auditable AI workflows for complex technical domains: agent governance, reproducible research, quantitative systems, and scientific machine learning. This project is part of our broader effort to make AI experimentation more rigorous, traceable, and publishable.

## Keywords

Kaggle, Biohub, cell tracking, 3D microscopy, bioimage analysis, cell lineage reconstruction, scientific machine learning, reproducible ML, graph tracking, ILP tracking, DeepCenter, temporal UNet, Everything AI Co.
