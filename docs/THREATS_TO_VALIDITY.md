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

Because the competition was active, active code and detailed artifacts remain private. That limits the public repo's reproducibility until closeout review.
