# Why Later Public Pipelines Improved

A central question in this project was: if we tried so many ideas, why did later public notebooks achieve much higher scores?

The short answer: the later notebooks were not merely better hyperparameters for the same pipeline. They used a stronger stack of public assets and integration techniques.

## Model-Family Ceiling vs Competition Ceiling

Our July work appeared to saturate a family of public learned-graph pipelines around the high `0.89` range. That was a real ceiling for that family, but not for the whole competition.

Later public work introduced a different solution class:

- auxiliary full-frame center detectors;
- independent temporal model seeds;
- bidirectional probability fusion;
- division-specific neural gates;
- density-aware geometric overrides;
- faster dual-GPU notebook execution.

Those changed what was possible.

## Why This Was Not Just "More GPU"

More GPU helps, but it does not automatically create a better score. The later systems also required:

- trained checkpoints;
- careful packaging as Kaggle datasets;
- no-internet dependency handling;
- calibration under sparse labels;
- graph constraints and post-processing;
- public leaderboard feedback.

In other words: compute was only one part of the system. The larger improvement came from a better trained and better integrated model stack.

## Scientific Interpretation

The project taught us to separate:

- **search within a model family**, where tuning eventually saturates;
- **switching model families**, where new checkpoints and architectures can reset the ceiling.

For future competitions, we would maintain a daily watch on public notebooks and datasets near the deadline, because the public baseline can move rapidly.
