<p>
  <img src="assets/banner.svg" alt="Intent first — purpose, end state, bounds" width="738">
</p>

# Intent first

Skills that make an agent write down the purpose, the end state, and the bounds before it builds.

## Why intent

You want the end state. Give an agent too many guardrails and it will force itself into engineering it that way.

In the United States Military, the Commander’s Intent does not tell you how. It names the desired outcome.

Intent is the purpose, the conditions that must remain true, and the end state. It is not a method. Too many specifics and people stop thinking. They follow the method even when the method is wrong.

Humans are not perfect. We do not engineer perfectly. A master engineer gets the tools and the end state — not a script for how they must use the tools.

You write the intent. The how stays theirs.

## Immutable

After `INTENT.md` is written, **agents read it. They do not edit it.**

Only the operator changes it, by running the intent skill again and confirming a replace. If the work has drifted: the agent reports the gap and stops. It does not rewrite the file to match the work.

## Installation (30-second setup)

Two ways in. Pick one per machine. Installing both leaves you with every skill twice.

<details>
<summary><strong>Claude Code</strong></summary>

```
/plugin marketplace add brett-technical/skills
/plugin install skills@skills
```

</details>

<details>
<summary><strong>Codex, Cursor, and other agents</strong></summary>

```bash
npx skills add brett-technical/skills
```

</details>

<details>
<summary><strong>Manual</strong></summary>

Copy the `skills/` directory into your agent’s skills path (for example `~/.codex/skills` or `~/.claude/skills`).

</details>

## Skills

| Skill | Use when |
| --- | --- |
| [intent](skills/intent) | Starting work with no stated purpose, end state, or bounds |

## Sample

[skills/intent/examples/INTENT.md](skills/intent/examples/INTENT.md) — what the skill writes.

## License

[MIT](LICENSE)
