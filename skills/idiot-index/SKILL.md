---
name: idiot-index
description: Cost audit by the idiot index. Use when a part, a service, a plan, or a quote costs more than it should, when someone says "that is what it costs", or when a bot must find the three worst parts of a budget. Ratio of total cost to raw-material cost, an owner name per line, and an 80 percent target. Worksheet and worked example.
version: 1.0.0
license: MIT
---

# Idiot index

A number that says whether a cost is physics or laziness.

## The rule

Idiot index = total cost of a component ÷ cost of its raw materials. "If the ratio is high, you're an idiot." A rocket that costs fifty times its materials is not expensive because of physics. It is expensive because of the design and the process around the materials.

Every line in the audit carries the name of the one person responsible for getting that cost down. No department names. A line with no name is a line nobody owns.

## Procedure

1. **List the parts.** Every component, step, license, or service in the thing. No rollups.
2. **Raw cost per part.** What the materials cost at spot price, or for software and services the cheapest thing that does the same job at the same scale (a VM, a library, an hour of a person).
3. **Paid cost per part.** What you pay now, all in.
4. **Ratio.** Paid ÷ raw. Sort descending.
5. **Name the owner** for each of the worst three. One person.
6. **Ask the owner, from memory, not from a screen:** what are the three worst parts, why is the ratio high, and what would bring it down 80 percent. A high ratio means one of three things: the design is too complex, the process is dumb, or a supplier is charging for a brand. Each has a different fix.
7. **Set the target:** 80 percent down on each of the worst three, with a date. If the owner cannot see a path, a different owner gets the part.
8. **Make versus buy.** If the part "is not more complicated than a garage door opener", make it. A $120,000 actuator became a $5,000 one that way.

## Worksheet

```
| Part | Raw cost | Paid cost | Ratio | Owner | Why high (design / process / brand) | Target (-80%) | Date |
|---|---|---|---|---|---|---|---|
```

Output: the worst three rows, then the one sentence that says which of the three causes dominates.

## Worked example

Actuator for an early SpaceX rocket. A supplier quoted $120,000. The part "was not more complicated than a garage door opener", so the target was $5,000 and the part was built in house. The ratio that justified the order: the quote against the materials and the labor of a garage-door opener, a factor above 20. Cause: brand and process, not design.

Software version. A managed search service at $2,400 a month for an index of 50,000 documents. Raw: the same index on one small VM with an open-source engine, about $40 a month plus a day of setup. Ratio 60. Cause: brand. Fix: run it yourself, or negotiate against the raw number.

## Where it fails

- Raw cost computed at the wrong scale. Ten units and ten million units have different floors.
- A ratio used on a person. The index audits parts and processes. It does not say a person is an idiot; it says the design or the process made one of them.
- Deleting the qualification that physics demanded. Flight hardware that fails costs more than the paperwork did. Use the ratio to ask the question, then test.
