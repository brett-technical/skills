---
name: distill
description: "First-principles distillation of dense material (long text, books, research papers, images, diagrams). Use when user says 'distill this', 'distill brief', 'distill for the wiki', 'distill wiki', 'distill the question', 'distill unified', 'first principles this', 'deep analysis of this paper', 'quick brief this book', 'challenge assumptions in this', or similar. Produces structured first-principles analysis via one of four paths: unified, wiki, brief, or question."
version: 1.0.0
license: MIT
---

# Distill

Process dense material (text, books, papers, images, diagrams) using first-principles thinking and produce output according to one of four strictly separate paths.

**Path Selection (do this first, before any analysis or reading):**

Examine the user's request for a path:

- Explicit argument: `path=unified|wiki|brief|question` (highest priority).
- Natural language indicators (case-insensitive):
  - "brief", "quick brief", "executive", "takeaways", "summary" → brief
  - "wiki", "for the wiki", "second brain", "second-brain", "wiki notes" → wiki
  - "question", "challenge assumptions", "assumptions", "what if" → question
  - "unified", "fixed template", "the template", "raw first principles" → unified

If a clear path is detected from the above, use it immediately.

If no path is indicated or it is ambiguous, immediately prompt the user with the four options ("unified, wiki, brief, or question") and wait for a clear selection before doing any analysis. Do not guess.

Once a path is determined, run **only** that path's instructions. The four paths are completely independent — never blend rules, formats, or thinking styles from other paths.

## Common Rules (apply inside whichever path is active)

- Use genuine first-principles thinking: surface fundamental assumptions, extract core truths from evidence, derive implications, and flag risks/contradictions.
- Handle all input the user provides: pasted text, references to books/papers, attached images, and diagrams. Read long documents when paths are given.
- Ground every claim directly in the source material. Cite specific sections, pages, or visual elements when relevant.
- For images and diagrams: analyze structure, relationships, data, and implications with the same rigor as text.
- Keep the final output clean, precise, and in the exact format required by the chosen path.

## Path: unified

Always produce the **exact same fixed first-principles template**, regardless of how the user might later use the result:

- Fundamental assumptions in the source
- Core truths / principles extracted
- Key implications & derivations
- Open questions / risks / contradictions

Deliver the template in clean, structured Markdown. Do not adapt, specialize, or reformat it for any particular end use. The raw template is the complete output.

## Path: wiki

Produce atomic, first-principles distilled notes in clean Markdown. Include:

- Atomic, linkable notes (focus on single concepts or entities where natural)
- Explicit provenance to the original source material (file, page, image, date added, etc.)
- First-principles elements surfaced (assumptions, core truths, implications, open questions/risks)

Do not produce executive summaries or pure assumption lists — stay in the atomic-note style.

## Path: brief

Run a fully separate analysis that produces:

- A tight executive summary of the material
- 3–5 actionable takeaways

Use first-principles thinking to ensure the summary and takeaways go beyond surface observations. Keep the output concise and practical.

## Path: question

Run a fully separate analysis focused exclusively on critical examination. Output **only**:

- A list of challenged assumptions, each supported by counter-evidence from the source
- "What if" probes and alternative framings suggested by the material

Do not add summaries, full templates, or other content. Stay narrow and rigorous.

## Principles

- Paths are mutually exclusive and self-contained. Once a path is chosen, stay inside its rules for the entire turn.
- Prioritize depth and evidence-based first-principles thinking over breadth or speed.
- For very long sources, process logically but always synthesize back into the single required output shape for the chosen path.
- When images or diagrams are central to the input, give them equal analytical weight.
