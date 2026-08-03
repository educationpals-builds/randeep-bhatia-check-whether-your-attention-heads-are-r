# Audit Charter: Lease Duty Splitter

## Specimen

**Tool under audit:** Lease tool that splits contract lines into separate duties

**d_model ÷ h arithmetic:** The attention mechanism divides the embedding dimension across heads. Each head operates on a slice of the representation space, learning to attend to different relationship types in the input.

## Standard

Each duty lands on its own line with the right party named

## Pasted Sentence Set

**Source:** Harbor Lease sample contracts

1. Tenant shall repair the roof provided that Landlord funds materials within 10 days.
2. Fees accrue daily; provided, however, that the cap in §4.2 still applies.
3. Notice is deemed given when posted, unless the parties agree otherwise in writing.

## Five Split Findings

| Check | Rating | Notes |
|-------|--------|-------|
| room | 0 | — |
| copies | 2 | — |
| unowned | 1 | — |
| stitch | 2 | — |
| ablation | 4 | Deciding check |

**Top crack:** ablation

## Severity Story

Example input: Tenant shall repair the roof provided that Landlord funds materials within 10 days. Deciding check: Nobody ever checked the parts on their own What goes wrong: [wrong output in one line — what the tool says back] Who gets hurt: A partner signs a summary that puts repair duty on the wrong side How long until someone notices:

## Call

Call: ship-with-conditions
Why: Nobody ever checked the parts on their own still breaks Lease tool that splits contract lines into separate duties on the real messages above.
Pass bar: Each duty lands on its own line with the right party named
Condition (owner: [name]): [one checkable action before ship]
If we hold instead: reopen when [a per-helper measurement] clears.

## Tripwire

Metric: [a number Nobody ever checked the parts on their own can move — not overall accuracy alone]
Trouble threshold: [the number that means stop]
Owner: [who gets the alert]
Why this catches it: when Nobody ever checked the parts on their own fails, this number should move before customers do.

---

This charter documents the builder's complete audit run and serves as the worked example for the Head-Map Interrogator.
