---
name: intent
description: "Elicit a clear statement of intent for a project, career, life area, or anything else being pursued — the purpose, key tasks, end state, and limits. Modeled on the Army's commander's intent. Use when the user says 'intent', 'set the intent', 'what's the intent here', 'write a mission statement', 'define what winning looks like', 'what are we actually going for', or is starting a new project without a stated purpose. Produces an INTENT.md that other skills read to judge whether work is worth doing."
version: 1.0.0
license: MIT
---

# Intent

Interview the user until a sharp statement of intent falls out. Modeled on the Army's
**commander's intent** — the artifact that lets someone make the right call when the plan breaks
and nobody is available to ask.

This is not a mission statement. A mission statement is the task — who, what, when, where. Intent
is the **purpose, the end state, and the bounds**. Never produce corporate mission-statement
language: no "strive to," no "world-class," no "leverage synergies." If a draft could hang on an
office wall unchanged, it is too vague to steer anything.

**Never describe how something works.** Intent is the why and the result, never the mechanism.

## What it produces

One `INTENT.md` per subject, at the head of that subject.

A subject is anything being pursued: a project, an app, a career, a life area. One intent per
subject.

## Immutability — hard rule

**Agents never edit an existing `INTENT.md`.** Not to refine it, not to adapt it to what turned out
to be achievable, not to reconcile it with reality. An intent that bends when work gets hard is
worthless — resisting exactly that is what it is for.

Only the **operator** changes it, by explicitly re-running this skill and confirming a replace.
If work has drifted from the file, **report the gap and stop**. Surfacing the gap is useful.
Rewriting the file to close the gap is the failure.

This rule must live **in the file**, not only in this skill. Agents that never loaded the skill
still read `INTENT.md`. If the file is silent, they will treat it as ordinary notes.

---

## Step 1 — Identify the subject

Confirm what the intent is *for*, in one question. Do not proceed against a vague subject.

If an `INTENT.md` already exists for it, say so, show it, and ask whether the user is replacing it.
Never overwrite silently.

## Step 2 — Read the subject

Before asking anything, read what is already there: the README, the actual files, open TODOs.

This is what makes the drafts useful. A draft assembled only from what the user said in the session
just reflects them back and surfaces nothing. Reading the subject is where real blind spots come
from — *"you say the purpose is X, but most of the code serves Y."*

**Outside research:** ask first. Never run it unprompted. When the user says yes, scope it tightly —
real commander's intent examples, and how comparable efforts define *done*. Never search generic
"mission statement" advice; it returns vague corporate language that will pollute the drafts.
**Research informs the drafts. It never becomes the intent.** The words stay the user's.

## Step 3 — Interview

One question at a time. Acknowledge in one sentence, then move on.

**Always offer options. Never cold-call the user for an answer.** The user has the information
locked in and cannot always retrieve it on demand — pulling it out is the job. A bare open question
("what is the purpose?") puts the work back on them and returns adjectives. The question itself may
be open-ended, but it must arrive with concrete candidate answers attached that the user can accept,
reject, or correct.

Build the options from two places: what the user has already said in their own words, and what the
subject's own files prove. Say which is which. Offer 3–4, make them materially different, and put
enough in each option that the user knows what they are choosing without reading anything else —
a bare label is not a choice.

When the user answers in adjectives ("bold", "rigorous", "innovative"), do not record them.
Translate each into something observable and name the evidence behind it, then offer those back.

Get enough to draft from — the why, what would count as done, what is explicitly not being chased.
A handful of questions, not an interrogation.

## Step 4 — Draft, three ways

For each section, offer **three materially different drafts**. Not three rewordings of one idea —
three genuinely different readings of what the user might mean. Divergence is the mechanism: a
single draft becomes an anchor and the user edits it instead of choosing.

| Section | Contains |
|---------|----------|
| **Purpose** | The why. What this is ultimately in service of. 1–2 sentences |
| **Key tasks** | What must happen regardless of approach. 3–5 bullets. Not a plan — the things any plan has to deliver |
| **End state** | The conditions that mean it is done. 2–4 bullets. Observable, not aspirational |
| **Limits** | What is explicitly not being chased. 2–4 bullets. The left and right bounds |

The user cuts and corrects. Iterate until they say it is right.

**Limits is the section people skip and regret.** It is what stops downstream work from ranking
something highly that the user would never actually want. Push for it.

## Step 5 — Run both tests

Doctrine attaches two rules to commander's intent. Both are testable. Run them before writing anything.

**Two echelons down.** Intent must be understood two levels below whoever wrote it. Here that means:
a reader with **zero context** — no session history, no memory of this conversation — must be able
to make a real decision from it.

Test it. Dispatch a subagent with only the draft and a concrete question: *"Given this intent, is
task X worth doing? Yes or no, and why."* If no subagent is available, re-read the draft with all
session context deliberately set aside and answer the same question honestly.

- **Fails:** *"Build the best personal AI system."* Nothing can be decided from it.
- **Passes:** *"...so I stop losing hours to work that turned out not to matter."* Now a task can be rejected.

If it fails, say which section was too vague and go back to step 4.

**Less is better.** Doctrine is explicit: long intents are not read or recalled; short ones change
behavior. The whole artifact must be readable in about 30 seconds. If it runs past a short page, cut
it — vagueness is mostly what happens when there is no word limit.

## Step 6 — Write it

Write `INTENT.md` at the head of the subject. Frontmatter carries the subject and the date it was
set. No expiry, no review date — an intent does not go stale on a clock, and a nag would only invite
the drift this skill exists to prevent.

Every `INTENT.md` must open with this block, verbatim, after the title:

```
> **Immutable.** Agents read this file. They do not edit it.
> Only the operator changes it, by re-running the intent skill and confirming a replace.
> If work has drifted: report the gap and stop. Do not rewrite this file to match the work.
```

Show the operator the final file and confirm before writing. After that write, refuse further
edits to that file. Point at the block. Do not "just fix a typo."

---

## Downstream

Any skill that starts a new project should run this first. A project without a stated intent has
nothing to judge its own work against.
