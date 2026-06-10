# opencode instructions

Personal opencode instructions that bias agents toward explanation-first planning, surgical changes, and autonomous implementation of understood slices.

These are not official opencode defaults. They are personal preferences intended to be copied, modified, or ignored.

These are not affiliated with, endorsed by, or authored by opencode or Effect.

## Usage

Add the instruction file to your opencode config:

```json
{
  "instructions": [
    "/path/to/instructions/opencode-working-style.md"
  ]
}
```

Instructions are loaded into every session. Keep them short and broadly applicable.

Install a skill globally by copying its directory under `~/.config/opencode/skills/`, or register this repository's `skills/` directory with `skills.paths` in `opencode.json`.

## Files

- `instructions/opencode-working-style.md`: explanation-first planning, scoped implementation checkpoints, surgical change rules, verification guidance, and concise Effect preferences.
- `instructions/rich-hickey-preferences.md`: concrete Hickey-inspired preferences for values, functions, managed state, declarative data, and rules.
- `skills/grill-with-docs/SKILL.md`: plan interview that sharpens domain language and records durable decisions; adapted from Matt Pocock's skill.
- `skills/teach/SKILL.md`: stateful, mission-driven teaching workflow; adapted from Matt Pocock's skill.

The adapted skills are based on [`mattpocock/skills`](https://github.com/mattpocock/skills), which is also MIT licensed.

## License

MIT
