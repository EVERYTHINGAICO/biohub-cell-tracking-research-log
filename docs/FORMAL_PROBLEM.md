# Formal Problem

## Temporal Graph Reconstruction

For each microscopy movie, the input is a sequence of 3D volumes:

```text
X = {X_t}, t = 0 ... T-1
X_t in R^(Z x Y x X)
```

The desired output is a directed temporal graph:

```text
G = (V, E)
```

Each node `v in V` represents a cell candidate:

```text
v = (id, dataset, t, z, y, x)
```

Each directed edge `(u, v) in E` represents a lineage relation from a parent or predecessor cell to a successor cell.

## Biological and Topological Constraints

A plausible lineage graph should satisfy:

- **Temporal direction:** edges point forward in time.
- **Single parent:** most non-root nodes should have indegree <= 1.
- **Continuation:** non-dividing cells usually have outdegree <= 1.
- **Division:** dividing cells may have outdegree = 2.
- **Physical motion:** displacement should be plausible in micron space.

Because voxel spacing is anisotropic, distance should be computed using:

```text
d_um(i, j) = sqrt((1.625 dz)^2 + (0.40625 dy)^2 + (0.40625 dx)^2)
```

## Decomposition

The practical solution can be decomposed into:

1. **Detection:** estimate candidate nodes `V`.
2. **Association:** estimate candidate edge probabilities `p(e | X)`.
3. **Optimization:** select a valid graph under topological constraints.
4. **Post-processing:** repair gaps, divisions, and implausible topology.
5. **Formatting:** emit the Kaggle node/edge table.

## Why This Is Hard

The difficulty is not only visual detection. Several cells can be visually similar, dense regions create association ambiguity, and sparse labels complicate local validation. A method can improve detection recall but hurt graph precision if it adds many ambiguous candidates. Conversely, excessive pruning can raise precision while destroying true lineage continuity.
