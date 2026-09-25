# What Was Missing?

The question is not "why did we fail to turn one knob?" The question is "what capabilities separated the July model family from the later `0.94+` public pipelines?"

## Short Answer

We had strong iteration within the older public model family, but the later score jump required a different stack:

- a stronger full-frame center prior;
- an independent temporal model seed;
- robust model fusion;
- division-specific neural gating;
- density-aware geometric overrides;
- a fast dual-GPU/ILP implementation;
- enough training/runtime iteration to package those assets cleanly.

## What We Had

By the July `0.896` ceiling, the project had:

- valid notebook submission mechanics;
- baseline DoG/rule-based tracking;
- temporal graph public notebook adaptation;
- threshold and short-track tuning;
- safe-division and topology repair;
- local metric reconstruction;
- attempts at local detector training, appearance linking, distillation, self-supervision, and relinking.

This was enough to saturate that public family, but not enough to create a new model family.

## What Later Public Pipelines Added

| Missing capability | Why it mattered |
| --- | --- |
| DeepCenter-style full-frame center prior | Helped rescue plausible nodes near gaps, endpoints, and short components without blindly adding all peaks. |
| Independent temporal seed | Allowed dual-seed fusion, reducing single-checkpoint blind spots. |
| Harmonic bidirectional fusion | Favored mutually consistent associations instead of one-direction edge confidence alone. |
| Edge-feature / detection TTA | Stabilized predictions under spatial transforms and edge feature variation. |
| DivNet-style division classifier | Added a specialized signal for mitosis/division decisions rather than relying only on generic graph heuristics. |
| Density-adaptive geometry | Adjusted motion/gap rules for sparse vs dense frames, reducing hijacks in crowded scenes. |
| Production-grade Kaggle packaging | Made the system runnable under no-internet, T4, and notebook-version constraints. |

## Could We Have Built It?

In principle, yes. In practice, it required:

1. **Earlier recognition that detection priors were still under-exploited.**  
   We had concluded detection was not the main bottleneck for the older family. The later DeepCenter asset changed this because it was not used as a replacement detector; it was used as a gated rescue prior.

2. **A successful multi-seed training pipeline.**  
   Our from-scratch T4 training attempt underperformed. The later public stack had an independent trained seed with a stronger package and provenance.

3. **Specialized division modeling.**  
   We treated divisions as lower leverage than edges, which was often true, but a dedicated division gate can still improve topology and reduce bad branches.

4. **More late-stage public asset surveillance.**  
   The public baseline moved after our July work. Monitoring public notebooks and datasets near deadline is part of the competition system.

5. **More production integration time.**  
   The final stack was not one model; it was a calibrated ensemble plus graph optimizer plus diagnostics. That integration is its own engineering project.

## Scientific Lesson

Our July conclusion should be phrased precisely:

```text
The July public model family appeared saturated near 0.896.
```

It should not be phrased as:

```text
The competition was saturated near 0.896.
```

The later score jump was a solution-class shift. It required new assets, not merely more tuning of the old ones.
