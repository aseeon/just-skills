# skills

Just Skills is a lean collection of focused agent skills, built to stay small. The aim is to make quality work easier. Every skill has to earn its place. Only what brings a clear benefit stays.

Agent skills by [@aseeon](https://github.com/aseeon), installable with the [`skills`](https://github.com/vercel-labs/skills) CLI.

## Install

To install every skill in this repo (recommended, as this repo is intentionally kept as small as possible):

```bash
npx skills add https://github.com/aseeon/skills
```

To install a chosen skill from the repo:

```bash
npx skills add https://github.com/aseeon/skills --skill chosen_skill
```

The CLI writes the skill into your agent's skills directory (`.claude/skills/` for Claude Code, and the equivalent path for other supported agents).

## Intended workflow


Manually invokable skills:
1. /just-scope - gather requirements through questioning and brainstorming
2. /just-design - agree UI/UX decisions after scope; optional when there is no interface or interaction change
3. /just-spec - turn scope and any agreed design into technical specification
4. /just-slice - break specification into tickets *(To be added)*
5. /just-implement - implement the tickets *(To be added)*
6. /just-verify - verify implementation *(To be added)*

Automatically applied helper skill: /plainspeak - make all the talking and output documents more pleasant

## Skills Inventory

| Skill | Description |
| --- | --- |
| [plainspeak](skills/plainspeak/SKILL.md) | Use plain language and cut AI tells from any writing. Applies to all output. |
| [just-scope](skills/just-scope/SKILL.md) | Invoke explicitly to gather requirements through questioning and brainstorming, then write scope document |
| [just-design](skills/just-design/SKILL.md) | Invoke explicitly after scope to agree UI/UX decisions and write a design document, with mockups when useful |
| [just-spec](skills/just-spec/SKILL.md) | Invoke explicitly to turn a scope file into a technical specification |


## Acknowledgments

The plainspeak skill is an opinionated synthesis of poteto's unslop and astra's model guidance

The just-scope skill would not exist without the prior work from obra (brainstorming), mattpocock (domain-modeling and grilling) and poteto (figure-it-out).

The just-spec skill is inspired by work from mattpocock (to-spec) and poteto (technical-writing).

The just-design skill draws inspiration from Dammyjay93's interface-design skill and Anthropic's frontend-design.

## License

MIT. See [LICENSE](LICENSE).
