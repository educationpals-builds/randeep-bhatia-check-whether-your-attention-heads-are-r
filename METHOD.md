# METHOD: The Five Splits

This file spells out the framework used to audit attention head behavior.

---

## The Five Principles

### P — Partition the Space

Each head receives a slice of the embedding dimension. Check whether the partitions are sized to capture the relationships the task requires. A head with too few dimensions cannot encode complex dependencies; too many dimensions may waste capacity on noise.

### R — Run in Parallel

Heads operate simultaneously, not sequentially. Verify that the parallel structure is exploited — heads should not be duplicating each other's work. Look for redundancy in attention patterns across heads.

### I — Individuate the Pattern

Each head should specialize. One head might track subject-verb agreement; another might follow coreference chains. Confirm that heads have differentiated roles. If all heads attend to the same tokens, the multi-head structure is wasted.

### S — Stitch the Spectra

After parallel computation, head outputs are concatenated and projected. Check that the stitching layer can combine the specialized signals into a coherent output. A failure here means good head-level work gets lost in aggregation.

### M — Map What Each Head Sees

Visualize or measure what each head attends to on real inputs. Without this map, you cannot diagnose which head is responsible for a failure. The map turns "the model is wrong" into "head 7 missed the conditional clause."

---

## The Anti-Pattern: Collapse to Monochrome

When all heads converge on the same attention pattern — attending to the same tokens with similar weights — the multi-head mechanism collapses. You get one head's worth of capacity from h heads. This is the collapse-to-monochrome failure: the spectrum of specialized attention flattens into a single gray signal.

Watch for it. Measure head diversity. If your attention maps look identical across heads, the architecture is not doing its job.
