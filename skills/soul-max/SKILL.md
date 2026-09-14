---
name: soul-max
description: "Use when the user says soul max a repo or article. Extract short operating rules for how an agent should think, decide, and act. Do not copy code, ingest a knowledge base, or study a whole field."
version: 1.0.0
license: MIT
---

# Soul max

Mine one source for how an agent should think, decide, and process information. Keep only rules that would make the agent better. Write each keep as a short standing instruction. Drop the rest.

The point is not code. The point is a tighter modus operandi: principles, working style, bounds.

Standing instructions say how the agent operates. Skills say when to do a task. This skill feeds standing instructions. It does not paste functions into a project.

## When to use

- User says `soul max` this repo, article, paper, talk, or other named source.
- Do not use for: install, clone-into-a-project, retrieval ingest, hunting GitHub for a named helper, documenting a tree, a field study, or writing a persona.

## Hard

- One source per run.
- No install. No new project. No silent edit of the user's standing instructions.
- A keep needs a cited location and a reason that names how the agent would think or act differently.
- Prefer a principle over a function.
- Never promote a line into a role whose job it fights.

## Keep test

Keep only if all of these hold:

1. It is about how an agent thinks, decides, or processes — not a widget, interface, helper, or product feature.
2. Applying it would make the agent more effective (faster judgment, fewer wasted tools, clearer verification, safer defaults).
3. It is not already in the standing instructions the user named. If it conflicts with them, mark conflict. Do not call it universal unless every named instruction file is missing it.
4. It fits as a short operating line. A 12-step recipe is a skill candidate, noted in the source file, not a standing-instruction paragraph.
5. It is true of an agent (files, model, tools). Drop body, employees, "I own no computer," and bans that belong to whoever assigns work.

If it fails any test, skip it.

## Where it lives

Staging (not live instructions):

A folder the user names, or `soul-max/` next to the work.

| File | Role |
|---|---|
| `index.md` | Catalog of sources |
| `sources/<date>-<slug>.md` | One file per source |

Live: only lines the user approved, patched into the instruction files they named (`AGENTS.md` or the agent's standing instruction file).

Copy `templates/source.md` for a new source file.

## Procedure

1. Read the standing instruction files the user named (or the default agent instruction file in the workspace). Done when you can mark already vs conflict.
2. Walk the source. Use whatever fetch and read tools this agent has. Done when you can defend each keep against the keep test.
3. For each keep, mark `apply` / `already` / `conflict` against those files. Done when no keep says `all` unless every named file is `missing`.
4. Write or update `sources/<YYYY-MM-DD>-<slug>.md`. Update the index row. Done when the file matches the template and the index row is current.
5. Show the keep table in chat, including apply/already/conflict. Wait. Done when the user has the table.
6. On explicit yes only: patch those lines into the instruction files the user named. Mark them `promoted` in the source file. Done when those files contain the line and the source file says so.

Unapproved lines never load in a later session. Chat may use them in this run only.

## Output in chat

```
Source: <url or path>
Keeps: <n>  Skips: <n>

KEEP  — <instruction-ready sentence>
        why: <one sentence: how the agent would think or act differently>
        apply: <file names, or none>
        already: <file names>
        conflict: <file (one-line reason)>
        cite: <path or URL>

SKIP  — <what> — <one-line reason>
```

## Pitfalls

- A clever script is not an operating line. If the agent cannot think differently after the keep, skip it.
- Do not grow this into a field study or a persona dossier.
- Do not ingest staging into a wiki or knowledge base.
- Do not copy a persona's method into an ops seat, or an ops "act now" line into a tester, debugger, or gatherer.

## Verification

- [ ] Staging file exists and index has the row
- [ ] Every keep is a short instruction with a citation and apply/already/conflict
- [ ] Nothing installed, copied into a project, or written to standing instructions unless the user said yes
- [ ] Target was agent operating quality, not general software reuse
