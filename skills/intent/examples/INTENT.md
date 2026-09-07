---
subject: this skills repository
set: 2026-09-07
---

# Intent — this repository

> **Immutable.** Agents read this file. They do not edit it.
> Only the operator changes it, by re-running the intent skill and confirming a replace.
> If work has drifted: report the gap and stop. Do not rewrite this file to match the work.

Purpose: publish a small set of original agent skills that force a sharp
intent before work starts, without leaking anything that is not meant to
be public.

## Key tasks

- Ship `intent` as a self-contained skill visitors can install in one command.
- Keep the catalog small enough to finish reading on the first screen.
- Show a sample `INTENT.md` so visitors see the output, not adjectives.

## End state

- A visitor can install with `npx skills add` or Claude Code `/plugin`.
- The README names the work, lists the skills, and links a sample.
- No machine paths, no hidden-library talk, no extra harness folders.

## Limits

- Not a dump of every skill the author has ever written.
- Not a methodology that owns the whole SDLC.
- Not Anthropic’s official plugin list.
