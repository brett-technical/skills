---
name: decision-matrix
description: "Rank competing tasks, projects, or options using an impact/feasibility matrix hardened against estimation bias. Use when the user says 'prioritize these', 'what should I do first', 'what should I work on', 'triage this', 'rank these', 'decision matrix', 'impact feasibility', or presents 3+ competing options with no stated order. Produces a ranked table, a quadrant placement, a do-next with reasoning, and a note on what would change the answer."
version: 1.0.0
license: MIT
---

# Decision Matrix

Rank a set of competing items on an **impact/feasibility matrix**. The 2×2 is how the answer is
read; **the anti-bias protocol is the actual product**. Do not skip steps to save time — the
framework fails precisely where the protocol is skipped.

## Scope — detect and state it

Infer from the working directory and the prompt:

- **Project scope** — inside a project folder, or the prompt names one. Impact is judged against
  that project's `INTENT.md` if one exists.
- **Global scope** — comparing work across projects. Impact is judged against a top-level
  `INTENT.md` if one exists.

**State the inferred scope in one line before scoring**, so the user can correct it. Root working
directory does not reliably mean global.

**Impact is scored against an `INTENT.md`.** Look for it project-first, then at the workspace
root. It supplies the yardstick — without one, impact has no meaning, and at global scope a hobby
build and an income-generating build have no shared unit at all.

If no `INTENT.md` is found:

1. Say it is missing and that scores will be weaker without it.
2. Ask what they are optimizing for right now, in one question. Use that as the yardstick for this
   run only.
3. Recommend writing a durable intent (purpose, end state, bounds) if they want later runs to
   share a yardstick.

Never score against nothing.

**Never edit an `INTENT.md`.** If the items on the table all point away from the stated intent, say
so and stop. Reporting that gap is useful. Closing it by rewriting the intent is the exact drift the
intent exists to prevent — only the user changes it.

## Modes

| Mode | Machinery | Use |
|------|-----------|-----|
| **full** *(default)* | 5 impact lenses · double-scored feasibility · adversarial pass | Everything |
| **quick** | 2 passes, same rubric | Long lists, or the user asks for quick |

`quick` uses the identical rubric — it only cuts redundancy. Label its output as lower confidence.
Never drop the rubric itself.

---

## Step 1 — Frame

Take the goal from the applicable `INTENT.md`. If there is none, confirm it in **one** question.
No goal means impact is undefined. Do not proceed without one.

## Step 2 — Collect

One line per item. Merge duplicates. Split anything that is really two items. Note where one item
is a dependency of another — that changes sequencing later.

## Step 3 — Feasibility

Score every item on this axis **before** touching impact. The order is load-bearing: it stops the
desired answer from steering the effort estimate.

Four sub-scores, **1–5 where 5 = easiest**:

| Sub-score | Question |
|-----------|----------|
| Effort | Raw time to done |
| Clarity | Do we know *how*, or is the path itself unknown? |
| Dependencies | Blocked on other work, other people, an external service? |
| Risk | Odds of failure, rework, or breaking something live |

`feasibility = mean(the four)` · `effort = 6 − feasibility`

**Blind double-score.** Score all items, then score them again without consulting the first pass.
Reconcile only where the two diverge. This is the strongest available defense against anchoring.

**Apply the ×2 effort rule.** Effort estimates are wrong low, universally. Correct for it, then tune
the multiplier from the run log once there is history.

No lenses here. Effort and dependencies are estimable facts, not perspectives.

## Step 4 — Impact — five lenses

Score each item **five separate times**, once per lens. Each lens is an independent read, not a
reworded version of the last one. Do not let them collapse into each other.

| Lens | Position | Asks |
|------|----------|------|
| **Immediate payoff** | present · upside | What does this unlock today? |
| **Leverage** | future · upside | What does this make cheaper later? How often does the payoff repeat? |
| **Fragility** | present · downside | What is load-bearing here? **Look both ways:** what breaks if this is *not* done, and what breaks if it *is*? |
| **Cost of inaction** | future · downside | What decays on its own if this is ignored? |
| **Momentum** | the person, not the task | Will this realistically get finished, or sit at 80%? |

The first four are mutually exclusive by construction — each occupies a different cell of
upside/downside × now/future. Momentum sits on a separate axis: it judges the person, not the work.

**Reconcile to one impact score, and report the spread.** The spread is signal, not noise:

- High on every lens → rare, unambiguous, act on it
- High on one lens only → real but narrow; name which lens carried it
- Wide spread → the item means different things depending on what is being optimized for; surface that

**Evidence gate.** Any lens scoring ≥4 must state a reason. No reason, cap it at 3.

## Step 5 — Confidence

Per item, name the basis of belief:

| Basis | Value |
|-------|-------|
| measured | 0.9 |
| reasoned | 0.6 |
| guessed | 0.3 |

**Uncertainty must be resolved, not laundered.** Any item tagged `guessed` that lands in the top
ranks: go find the fact, or ask the user, before the score stands. Apply this rule whether or not
the estimate feels uncertain — a wrong score does not feel wrong from the inside.

## Step 6 — Compute

```
score = (impact ÷ effort) × confidence
quadrant: impact ≥ 3 and feasibility ≥ 3
```

**Robustness check.** Recompute under ICE (`impact × confidence × ease`) and RICE. If the top pick
holds across all three, the formula choice did not drive the answer. If it flips, say so — that is
a weaker result than a single number implies.

Quadrants — always name the axis, never say "top-left". Impact/**effort** and impact/**feasibility**
charts mirror each other, so position names are ambiguous:

| Quadrant | Impact | Feasibility | Action |
|----------|--------|-------------|--------|
| Quick win | high | high | Do now |
| Big bet | high | low | Plan it, or run a cheap experiment to raise confidence |
| Fill-in | low | high | Batch it. **Warn:** these feel productive and quietly eat weeks |
| Money pit | low | low | Kill, or park with a date |

**Exclude sunk cost.** Score in-flight items on remaining effort and future return only.

**Steelman before killing.** One line on why a money-pit item might deserve to live, before dropping it.

## Step 7 — Constraints and time

The score stays clean. These promote items into a **separate lane**, never silently:

- **Deadline** — time-bound items, with the date stated.
- **Money** — does anything here have to produce income by a date, or does this plan threaten
  runway? A money constraint can stop a run.

List promotions apart from the ranking, with the reason. The user must be able to see which items
are being done because they matter and which because the clock says so.

## Step 8 — Adversarial pass

Argue against the top-ranked item. Try to defeat it. A wrong #1 is the expensive error — everything
below it is cheaper to get wrong.

## Step 9 — Present

- Ranked table: item · impact · feasibility · effort · confidence · score · quadrant
- ASCII quadrant plot
- **DO NEXT** — and why it beat #2
- **FLIPS IF** — what would have to be true to change the order
- Promoted lane, if any
- Fill-in warning, if any

Offer an HTML view on request ("show me", "visualize") as a single self-contained page.

## Step 10 — Persist and calibrate

Append the run to a log next to the work:

- **Project scope** → `decision-matrix-runs.md` in that project
- **Global scope** → `decision-matrix-runs.md` at the workspace root, or a folder the user names

**On every run, open the previous log first** and ask how the last top picks actually landed. Effort
estimates only improve if predictions get checked. This step is what makes the skill a system rather
than a ritual.

**Watch item for later:** frequency-of-payoff currently rides inside the Leverage lens. If the log
shows high-frequency, low-magnitude items losing to things later regretted, promote it to its own
multiplier (`reach × impact`).

## Self-invocation

When 3+ competing options appear mid-work, offer: *"There are N ways to go here — want me to run
the decision matrix?"* Announce and ask. Never run a scoring pass the user did not request.
