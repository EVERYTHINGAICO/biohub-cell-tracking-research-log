# What We Tried

This document summarizes the work at a level that is safe to publish during competition closeout. It avoids active submission code, private outputs, and copied notebooks.

## Baseline Mechanics

We first focused on making valid submissions:

- learned that direct local CSV uploads were not valid for this code competition;
- established notebook-generated `submission.csv` as the correct route;
- packaged dependencies for no-internet Kaggle execution;
- validated output schema and node/edge counts.

## Rule-Based Tracking

Initial systems used classical detection and linking:

- blob-like cell detection;
- motion-aware nearest-neighbor or Hungarian linking;
- gap-closing experiments;
- division heuristics;
- graph formatting.

This gave a useful baseline but did not fully exploit the learned graph structure needed for higher scores.

## Learned Public Pipelines

We then adapted public learned graph pipelines based on temporal UNet and node-linking models. These improved score significantly and shifted focus from detection-only work to graph-level post-processing.

Useful levers included:

- detection threshold tuning;
- short-track filtering;
- safe division constraints;
- topology-preserving graph repair;
- learned edge probabilities plus geometric sanity checks.

## Experiments That Did Not Become The Final Route

Several plausible directions were tested and found less effective:

- from-scratch 3D UNet detection;
- appearance-only cell-pair classifiers;
- self-supervised patch embeddings;
- pseudo-label distillation beyond teacher behavior;
- aggressive relinking variants that did not reliably transfer.

These negative results were useful because they narrowed the problem: the best gains came from stronger public model assets and graph-level integration, not from a single simple heuristic.

## Late Public-SOTA Adaptation

Near closeout, newer public Kaggle notebooks and datasets appeared with stronger model stacks. Adapting one of these pipelines produced a confirmed public score of `0.944` for our account.

The broad idea was:

- stronger center-prior detection;
- dual-seed temporal graph inference;
- global graph optimization;
- division gating;
- topology-aware post-processing.

The exact active kernel archive remains private until competition closeout review.
