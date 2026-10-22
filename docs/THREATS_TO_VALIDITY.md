# Threats to Validity

## Sparse Annotation Bias

Ground truth annotations are sparse relative to all visible cells. This can make local validation counterintuitive: predictions involving unannotated cells may not be penalized the way a dense annotation benchmark would penalize them.

## Public Leaderboard Feedback

Public leaderboard score is not the same as hidden-test generalization. Public notebooks can become tuned to the public split. This repo reports public score but avoids claiming final biological superiority.

## External Asset Dependence

The late score jump depended on public Kaggle assets created by the community: checkpoints, datasets, and notebooks. Our contribution is partly adaptation, validation, and documentation rather than sole model invention.

## Timing Effects

The available public baseline changed over time. A conclusion that was valid in July was no longer sufficient in September after new public assets appeared.

## Publication Constraints

This research log is a narrative summary. The [technical closeout archive](https://github.com/EVERYTHINGAICO/biohub-cell-tracking-closeout) is now public and contains local experiment scripts. The two repositories describe the same work. The final notebook is linked on Kaggle; neither repository includes competition data, model weights, or a dependency-pinned end-to-end reproduction. Source and artifact access therefore limit reproducibility even after publication.
