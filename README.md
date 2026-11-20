# Follow the Source

A skill for coding agents. When you give an agent originals to work from (examples, a runbook, a primer, a spec, screenshots), this skill makes it keep going back to them instead of working from its memory of them.

The rule it enforces: a note can tell the agent where to look, but only inspecting the original counts as a check.

## What the agent does with it

It keeps a short map of each source: where it is, which part of the job it guides, and any version you pinned. Then it reopens the relevant part of the original at these moments:

| When | What it does |
| --- | --- |
| Starting a decision, section, or batch that depends on the material | Reads the relevant part again, with its qualifications and exceptions, and applies it. |
| Working through a long, repetitive stretch | Splits the work into batches. Without a cadence from you, at most five substantive items between reads. |
| After a correction, a revised source, or an unexpected result | Reopens the affected material and repairs the earlier work that depended on it. |
| Resuming after a handoff, an interruption, or context compaction | Recovers the source locations and reopens the originals before acting. Delegates get the same locators and the same loop. |
| Delivering the result | Checks the actual output against the originals again and fixes mismatches. |

Search hits, filenames, earlier quotes in notes, and another agent's assurance only help locate a source. They are not a check.

It also covers how to use an example: apply the move the example makes in a comparable situation, without copying its wording or treating an inferred pattern as a mandatory rule. If two originals conflict on a decision that matters, the agent names the exact passages and asks only about that choice.

The full instructions are in [SKILL.md](SKILL.md).

## Install

Clone once and link it into each agent's skill folder:

```sh
git clone https://github.com/ap7x42a/follow-the-source ~/follow-the-source
ln -s ~/follow-the-source ~/.claude/skills/follow-the-source   # Claude Code
ln -s ~/follow-the-source ~/.codex/skills/follow-the-source    # Codex
```

Or clone straight into the one you use:

```sh
git clone https://github.com/ap7x42a/follow-the-source ~/.claude/skills/follow-the-source
git clone https://github.com/ap7x42a/follow-the-source ~/.codex/skills/follow-the-source
```

Start a new session so the agent picks it up.

## Use

The agent loads it on its own when you supply originals to guide the work, ask it to keep referring back to them, or resume work governed by them.

To ask for it by name:

- Claude Code: `/follow-the-source`
- Codex: `Use $follow-the-source to apply the attached references throughout this task and check the finished work against them.`

Routine checks stay out of the deliverable. If you want an audit, ask for one. An entry looks like this:

> Runbook, Escalation criteria → recorded the failed local print test before escalation → ticket 17, diagnostics field.

## Files

- `SKILL.md` is the skill.
- `agents/openai.yaml` is its Codex interface entry.
- `assets/icon.svg` is its icon.

## License

MIT. See [LICENSE](LICENSE).
