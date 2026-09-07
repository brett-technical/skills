<p>
  <img src="assets/banner.svg" alt="Intent first — purpose, end state, bounds" width="738">
</p>

# Intent first

Skills that make an agent write down the purpose, the end state, and the bounds before it builds.

## Why intent

This is the Army's **commander's intent**. When the plan breaks and nobody is there to ask, the unit still knows three things: why we are here, what done looks like, and what we will not chase.

Agents fail the same way. They rewrite the goal to match the work they already did. A mission statement on the wall does not stop that. A short file can.

That is why this skill exists. Write the intent first. Then the file is law.

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
