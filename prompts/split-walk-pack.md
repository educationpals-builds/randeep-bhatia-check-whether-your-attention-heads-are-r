# Split-Walk Prompt Pack

Five standalone prompts for auditing attention heads. Each walks one split and ends with the per-head measurement it demands. Use in any chat model.

---

## Prompt 1: Room

```
I'm auditing an attention setup. The tool under audit:

Lease tool that splits contract lines into separate duties

Real inputs look like: Old scanned leases with nested "provided that" lines

Here are three real messages where it fails:

Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.

Walk me through the ROOM split:
- Is there capacity for this task in the current head allocation?
- Which subtasks need dedicated heads?
- Where might heads be overloaded?

End with the per-head measurement that would confirm your finding:
→ Count of heads with non-trivial activation on the target pattern
```

---

## Prompt 2: Copies

```
I'm auditing an attention setup. The tool under audit:

Lease tool that splits contract lines into separate duties

Real inputs look like: Old scanned leases with nested "provided that" lines

Here are three real messages where it fails:

Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.

Walk me through the COPIES split:
- Are multiple heads doing the same work redundantly?
- Which heads might be duplicating effort?
- Is the redundancy protective or wasteful?

End with the per-head measurement that would confirm your finding:
→ Cosine similarity between head outputs on the same input
```

---

## Prompt 3: Unowned

```
I'm auditing an attention setup. The tool under audit:

Lease tool that splits contract lines into separate duties

Real inputs look like: Old scanned leases with nested "provided that" lines

Here are three real messages where it fails:

Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.

Walk me through the UNOWNED split:
- Is any part of the task falling through the cracks?
- Which subtasks have no head that owns them?
- What patterns get ignored?

End with the per-head measurement that would confirm your finding:
→ Attention mass on the unhandled subtask across all heads
```

---

## Prompt 4: Stitch

```
I'm auditing an attention setup. The tool under audit:

Lease tool that splits contract lines into separate duties

Real inputs look like: Old scanned leases with nested "provided that" lines

Here are three real messages where it fails:

Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.

Walk me through the STITCH split:
- Do heads that should hand off to each other actually connect?
- Where does information get lost between heads?
- Which sequential subtasks break at the seam?

End with the per-head measurement that would confirm your finding:
→ Correlation between upstream head output and downstream head input on sequential subtasks
```

---

## Prompt 5: Ablation

```
I'm auditing an attention setup. The tool under audit:

Lease tool that splits contract lines into separate duties

Real inputs look like: Old scanned leases with nested "provided that" lines

Here are three real messages where it fails:

Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.

Walk me through the ABLATION split:
- What happens when you remove each head one at a time?
- Which heads are load-bearing for this task?
- Which heads could be zeroed out with no effect?

End with the per-head measurement that would confirm your finding:
→ Delta in task accuracy when each head is zeroed out
```

---

## How to Use This Pack

1. Pick the split you want to investigate
2. Paste the prompt into any chat model
3. Replace the specimen, inputs, and failure examples with your own
4. The model walks the split and proposes findings
5. Confirm findings with the per-head measurement at the end

---

## Builder's Audit Summary

**Deciding split:** ablation (rated 4)  
**Pass bar:** Each duty lands on its own line with the right party named  
**Source:** Harbor Lease sample contracts

**Call:** ship-with-conditions  
**Tripwire:** Watch the metric that ablation can move — not overall accuracy alone. When ablation fails, this number should move before customers do.