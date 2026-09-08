# skills

Agent skills by [@aseeon](https://github.com/aseeon), installable with the [`skills`](https://github.com/vercel-labs/skills) CLI.

## Install

```bash
npx skills add https://github.com/aseeon/skills --skill plainspeak
```

To install every skill in this repo:

```bash
npx skills add https://github.com/aseeon/skills
```

The CLI writes the skill into your agent's skills directory (`.claude/skills/` for Claude Code, and the equivalent path for other supported agents).

## Skills

| Skill | Description |
| --- | --- |
| [plainspeak](skills/plainspeak/SKILL.md) | Use plain language and cut AI tells from any writing. Applies to all output. |

## Layout

```
skills/
  <skill-name>/
    SKILL.md
```

Each `SKILL.md` starts with YAML frontmatter carrying `name` and `description`, followed by the instructions.

## Adding a skill

1. Create `skills/<skill-name>/SKILL.md`.
2. Give it frontmatter with a `name` matching the folder and a `description` that says when the skill applies.
3. Add a row to the table above.

## Acknowledgments

The plainspeak skill is an opinionated synthesis of poteto's unslop and astra's model guidance

## License

MIT. See [LICENSE](LICENSE).
