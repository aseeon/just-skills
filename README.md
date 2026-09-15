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
| [scope](skills/scope/SKILL.md) | Invoke explicitly to gather requirements through questioning and brainstorming, then write docs/scope.md. |
| [spec](skills/spec/SKILL.md) | Invoke explicitly to turn a scope file into a technical specification in docs/spec-<feature-name>.md. |

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

The scope skill draws on four approaches:

- [obra/superpowers brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md) contributes context gathering, exploring alternatives, and refining requirements through dialogue. Scope records the entire agreed work in a document for user review.
- [mattpocock domain-modeling](https://github.com/mattpocock/skills/blob/main/skills/engineering/domain-modeling/SKILL.md) contributes precise terms and concrete boundary cases. Scope keeps definitions with the work unless the repo requires separate records.
- [mattpocock grilling](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) contributes relentless questioning in dependency order and agent-led fact finding. Scope limits rounds to seven relevant questions and supports stopping early with a draft and open questions.
- [cursor/pstack figure-it-out](https://github.com/cursor/plugins/blob/main/pstack/skills/figure-it-out/SKILL.md) contributes measurable success and early investigation of risky unknowns. Scope captures verification requirements without taking on execution or its plugin dependencies.

The spec skill draws on two approaches:

- [mattpocock to-spec](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-spec/SKILL.md) contributes repo context, design decisions, and tests of observable behavior. Spec uses the scope file as its input and maps its requirement and acceptance IDs to design and verification.
- [cursor/pstack technical-writing](https://github.com/cursor/plugins/blob/main/pstack/skills/technical-writing/SKILL.md) contributes consistent terminology, exact identifiers, and clear sentences. Spec delegates general writing rules to plainspeak and keeps one document focused on the technical design.

## License

MIT. See [LICENSE](LICENSE).
