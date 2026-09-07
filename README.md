<p>
  <img src="assets/banner.svg" alt="Intent first — purpose, end state, bounds" width="738">
</p>

# Intent first

Skills that make an agent write down the purpose, the end state, and the bounds before it builds.

No mission-statement language. No “world-class.” If a draft could hang on an office wall unchanged, it is too vague to steer anything.

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
