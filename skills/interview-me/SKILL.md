---
name: interview-me
description: "Interview the user to uncover the real underlying goal of a project or body of work. Maintain a strong bias toward small, compartmentalized specifications from the very beginning. Explicitly require the user to verify and confirm every key decision, assumption, and decomposition before moving forward. Use when user says 'interview me', 'find the real goal of this project', 'help me scope this', 'what are we actually trying to achieve', or similar."
version: 1.0.0
license: MIT
---

# Interview Me

A focused interviewing skill for surfacing the real goal of a project and breaking it into small, verifiable, compartmentalized pieces.

## When to Use

- User explicitly says "interview me" or similar phrasing.
- Starting a new project or major initiative where the stated goal feels fuzzy or incomplete.
- Before heavy design or implementation work.
- When the user wants to distinguish the surface goal from the deeper intent, success criteria, and constraints.

## Core Loop (One Question at a Time)

1. **Start strong**: Confirm the project or idea. Ask for the currently stated goal and any existing description or brief.

2. **Uncover the real goal**: Probe to distinguish the stated goal from the underlying intent, why now, success criteria, constraints, and what done actually looks like. Do not accept the first framing.

3. **Bias toward small and compartmentalized specs**: When exploring scope or solutions, consistently push to break things into the smallest independent, verifiable pieces. Challenge large or coupled proposals immediately.

4. **Explicit verification**: For every significant decision, assumption, goal statement, or decomposition, clearly restate it and require the user to explicitly confirm or correct it ("Does this accurately capture the real goal? Do you verify this breakdown?").

5. **One question at a time**: High-signal questions only. Always state the current phase at the start of your response (one of: "Real Goal Discovery", "Small and Compartmentalized Specs", "Explicit Verification", or "Convergence to MVP"). Frame questions so the user can reply in 1-3 words, yes/no, a number, or one short sentence. Explicitly invite brevity. Prefer binary choices, scales (1-5), or quick confirmations. Offer a recommended framing or small option set when it will accelerate clarity. After their reply, acknowledge in one sentence max and move forward.

6. **Drive to endstate and converge**: Once the real goal is clearly articulated, an initial set of small specs has been proposed, and key decisions have been explicitly verified, stop asking new questions. Deliver the Output summary focused on the smallest viable product and ask if the interview can conclude with this as the endstate. If the user offers more tangential information, redirect: "We've covered the real goal, the small specs for the MVP, and the verified decisions. Shall we lock this MVP endstate?"

## Principles

- The real goal is rarely the first one stated.
- Small and compartmentalized is almost always preferable to large or monolithic.
- The user must own and verbally verify every key decision — do not assume silent agreement.
- Surface hidden assumptions, success criteria, and constraints aggressively.

## Research Phase (when specs require external knowledge)

When the gap between current knowledge and needed specs is large (for example "find the best algorithm for X"), look things up instead of relying on training data alone. If the agent can run parallel lookups, do that:

| Lens | Job |
|------|-----|
| A | Inspect reference project 1 (code, README, algorithms) |
| B | Inspect reference project 2 (code, README, algorithms) |
| C | Current public sources — state of the art and comparison tables |

**Rules:**

- Give each lookup URLs or project paths and specific questions.
- Report in a structured format with tables when comparing options.
- Treat live sources as authoritative for recent packages and versions.
- After the lookups return, compile one consolidated table.
- Present findings: "Here's what the research found. Does this match your thinking?"

If a browser or network is unavailable, read cloned source or fetched READMEs, or label training-data claims as such.

## Output

At the end of the session, deliver a clean summary containing:

- The distilled real goal (in the user's words where possible)
- Proposed initial breakdown into small, compartmentalized specs or components
- Research findings (if applicable): consolidated tables
- Explicitly verified key decisions and assumptions (with the user's confirmation)
- Remaining open questions, risks, or areas that still need clarification
- Recommended next steps for implementation planning or scoping
