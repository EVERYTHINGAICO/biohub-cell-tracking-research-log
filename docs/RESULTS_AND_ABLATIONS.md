# Results and Ablations

This table reports public scores from our competition trajectory at a publication-safe level.

| Stage | Public score | Interpretation |
| --- | ---: | --- |
| Early valid notebook baseline | `0.113` | Valid structure but weak prediction quality. |
| Public rule-based DoG baseline | `0.826` | Stronger detection/linking baseline. |
| Two-pass linker / rule-based V3 | `0.842` | Motion-aware association improved edge Jaccard. |
| Public learned-graph adaptation | `0.856` | Learned temporal graph model improved over heuristics. |
| Short-track / threshold tuning | `0.867-0.873` | Reduced over-prediction in the July public family. |
| Advanced post-processing | `0.889-0.893` | Safer division and topology repair improved graph quality. |
| LB897 public family adaptation | `0.896` | July family appeared near saturation. |
| DeepCenter / ILP public adaptation | `0.944` | Later public model assets changed the achievable ceiling. |

## Interpretation

The score trajectory suggests three phases:

1. **Validity phase:** learning the correct notebook-submission mechanics.
2. **Model-family tuning phase:** improving within a known public pipeline family.
3. **Solution-class shift:** adopting later public assets that improved the base model stack.

## Why Not Claim `0.951`?

Some public notebooks claimed or titled themselves around `0.951`. Our confirmed score for the adapted submission was `0.944`. This repo reports our confirmed score, not title claims from public notebooks.
