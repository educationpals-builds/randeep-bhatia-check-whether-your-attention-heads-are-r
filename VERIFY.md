# Stranger Verification

This file describes how a stranger can verify the Head-Map Interrogator works as intended.

---

## Verification Steps

### 1. Run the Seeded Specimen Through /play

Open the interrogator and provide the seeded specimen:

> Lease tool that splits contract lines into separate duties

With the sample sentences:

1. Tenant shall repair the roof provided that Landlord funds materials within 10 days.
2. Fees accrue daily; provided, however, that the cap in §4.2 still applies.
3. Notice is deemed given when posted, unless the parties agree otherwise in writing.

### 2. Confirm the Unowned-Relationship Finding Surfaces

The interrogator must surface the ablation finding — that nobody ever checked the parts on their own. This is the deciding check from the builder's audit.

Look for:
- The tool identifies ablation as a concern
- The tool walks through what happens when component heads are tested in isolation
- The severity story connects to the real input about tenant/landlord repair duties

### 3. Confirm Per-Head Number Demand

The interrogator must demand a per-head measurement for the finding. Generic statements like "check the attention maps" are not sufficient.

The tool should ask for or propose:
- A specific metric that can be computed per head
- A threshold that distinguishes acceptable from problematic
- An owner who monitors the metric

### 4. Check the Output Structure

The final audit output must include:
- [ ] A severity story on a pasted input
- [ ] A call (ship / ship-with-conditions / hold)
- [ ] A tripwire with a numeric threshold

---

## What Success Looks Like

A stranger with their own attention setup can:
1. Describe their tool and paste their own sentences
2. Get walked through all five splits conversationally
3. Receive candidate per-head findings with proposed measurements
4. End with a scored audit, severity story, call, and tripwire

The builder's audit (lease duty splitter, ablation finding, ship-with-conditions call) serves as the worked example throughout.
