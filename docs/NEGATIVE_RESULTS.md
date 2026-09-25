# Negative Results

Negative results are part of the scientific contribution. They identify which plausible directions did not produce robust improvements.

| Hypothesis | Experiment family | Result | Interpretation |
| --- | --- | --- | --- |
| A local 3D UNet detector can beat the public detection stack. | Train/evaluate local 3D UNet detection. | Did not outperform established detection/linking stack. | Detection alone was not the easiest route; localization and graph integration both mattered. |
| Appearance patches can identify correct temporal links. | Pairwise appearance classifier / embedding experiments. | Weak or non-transferable signal. | Cells were visually similar; geometry and learned graph context mattered more. |
| Self-supervised patch features will recover hidden association structure. | Contrastive/self-supervised patch representations. | Did not produce reliable edge recovery. | Local visual similarity was insufficient for robust lineage association. |
| Pseudo-label distillation can exceed the teacher. | Distill from public model outputs. | Mostly learned teacher behavior. | Without independent signal, distillation inherited teacher blind spots. |
| Small local-proxy relink gains will transfer to hidden test. | Relink/gap variants. | Some local gains did not reliably transfer. | Sparse labels and public/hidden mismatch made small proxy deltas unreliable. |
| More training from scratch on limited runtime will beat public checkpoints. | Kaggle T4 training attempt. | Undertrained relative to public checkpoints. | Starting from a strong checkpoint and using robust resume/fine-tune workflows would be preferable. |

## Lesson

The most valuable improvements came from stronger public model assets and integrated graph post-processing, not from a single local heuristic.
