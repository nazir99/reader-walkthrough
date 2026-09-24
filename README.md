# reader-walkthrough

A Claude Code skill that reviews AI-built work the way its real reader will
read it, before a human has to.

## Why it exists

An agent can build a dashboard that passes every design guideline and still
leave its reader stuck on the first card: a `$0.00` that really means "not
computed", an internal ID where a name belongs, a button that might change live
data. Someone then has to review the work line by line, which cancels out the
time the agent saved.

This skill moves that review ahead of the human. The agent takes on a named
reader, walks the work top to bottom in the order it renders, and reports only
the points where that reader would stop.

## The one rule

**Only report what you found by walking the work as the persona.** Findings
drawn from general principle are the ones a human has to re-review. Findings
reached in character are the ones the reader would actually hit.

## Three readers, three different stalls

The bundled personas come from finance and accounting work, because that is
where this was built. The split behind them applies to any domain:

| Persona | Their question | Where they stall |
|---|---|---|
| `owner` | Can I defend this? | A number they cannot source, a button that might change something live |
| `reviewer` | Was this prepared correctly? | Two figures for the same thing, "not tested" that reads as "passed" |
| `evidence-assembler` | Can I hand this over without narrating it? | A summary they cannot open, your team's jargon |

If you pick the wrong reader, the walk comes back clean and the report is
useless.

## Install

This is a plain skill folder in the open Agent Skills format (a `SKILL.md`
plus supporting files), so it is not tied to one tool.

**Claude Code**

```
git clone https://github.com/nazir99/reader-walkthrough ~/.claude/skills/reader-walkthrough
```

**Claude.ai / Claude Desktop:** zip this folder and upload it under
Settings, Capabilities, Skills.

**Any other agent:** point it at `SKILL.md`, or paste its contents into the
system prompt along with the persona you want it to use.

## Use your real readers

The bundled personas are archetypes. The skill works best with the actual
people who will read the work. Copy `personas/TEMPLATE.md`, fill it in from
things the person has actually said and done, and save it to:

- `.claude/personas/<name>.md` in a project, or
- `~/.claude/personas/<name>.md` for every project.

Then ask: *"walk this as <name>"*. Your persona files stay local and are never
part of this repo.

## In a pipeline

Every report ends with a line a pipeline can gate on:

```
VERDICT: PASS | STALLS <count> | worst: <Where>
```

When it runs unattended, the skill does not stop to ask questions. It uses the
persona it is given, or `owner` if none is named, and says so when it had to
assume one.

## License

MIT
