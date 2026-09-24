---
name: reader-walkthrough
description: Use before showing a person any screen, dashboard, report, export or written deliverable, and whenever someone says a screen is confusing, unclear, or that they do not know what they are supposed to do. Walks the work as a named reader persona and reports only where that reader gets stuck.
---

# Reader Walkthrough

The review has to happen before a person sees the work, not after. If the
person is the one finding the double badge, the internal ID where a name
belongs, or the `$0.00` that means "not computed", the review step was skipped.

**This is a rigid skill.** Do not summarise it, do not skip the walk, do not
report findings you did not reach by walking.

## When to run it

Run it **before** presenting:

- any screen, tab, card or dashboard
- any report, export or CSV a non-developer will read
- any document written for someone other than the person who asked for it

Run it **again** when the user says any of: *"I don't know how to use it"*,
*"I'm not sure what I'm supposed to be doing"*, *"this is confusing"*, *"make
this simpler"*, *"I have to spend a lot of time reviewing what you built"*.

Skip it for: backend logic, queries, deploy scripts, anything with no reader
but a developer.

## The rule that makes it work

**You may only report what you found by walking the thing as the persona.**

Not what you know is wrong. Not what the design guidelines say. If you did not
reach it by reading the screen in order, in character, it does not go in the
report. Findings invented from general principle are the ones a human has to
re-review, which is the problem this skill exists to fix.

## Procedure

### 1 · Load the persona

Look for the persona in this order and use the first match:

1. `.claude/personas/<name>.md` in the current project
2. `~/.claude/personas/<name>.md`
3. `personas/<name>.md` in this skill directory

Real readers belong in 1 or 2. The bundled personas in 3 are archetypes, used
when no real reader has been written up yet:

| Persona | Use it for | The thing that makes them different |
|---|---|---|
| `owner` | The person accountable for the number | Has to defend it. Asks "can I defend this?" |
| `reviewer` | Anything read as a work paper | Checks someone else's preparation. Asks "was this prepared correctly?" |
| `evidence-assembler` | Reconciliations, audit support, board packs | Hands the work to a third party. Asks "can I hand this over without narrating it?" |

If no persona is named, use `owner`.

**Owning a number, reviewing one, and handing one over are different jobs.**
They stall in different places, so picking the wrong persona produces a clean
walk and a useless report.

If the named persona does not exist, write it first from
`personas/TEMPLATE.md`: what they know, what they do not know, and what they
came to the screen to find out. Save it to the project's
`.claude/personas/`. Ground it in things the reader has actually said or done,
and mark the rest as assumed, because a persona built on invention produces
findings someone has to re-review.

### 2 · Name the visit

Before reading anything, write down in one line:

- **why they opened it today:** the actual job, not "to use the tool"
- **which visit this is:** first ever, or the routine monthly one. They behave
  completely differently and only the first is ever designed for.

Default to the **routine** visit. First-run polish is easy and it is not where
the pain is.

### 3 · Walk it in order

Read the thing top to bottom, in the order it renders, in character. At each
element ask only these:

1. **Do I know what this number is?** Not what it is called: what it *is*, and
   whether it is the one I came for.
2. **Do I believe it?** What would make me doubt it, and can I check from here?
3. **What am I supposed to do now?** If the answer is "read on", say so and
   move on.
4. **What happens if I press this?** Specifically: can it change something live,
   and does the screen tell me before I find out?

Stop at the **first** point where the honest answer is "I don't know" and write
it down. That is a finding. Then carry on. Do not fix it in your head and keep
walking, because everything after it is now being read by someone confused.

### 4 · Report

Report **only stalls**, ranked by how early they occur. Earliest first: a stall
on the first card invalidates everything below it, so it is worth more than
three later ones.

For each:

| Field | Content |
|---|---|
| **Where** | The element, by the label the persona sees, not the function name |
| **Stall** | What they thought or asked, in their words |
| **Why** | What the screen assumed they knew |
| **Fix** | The smallest change that removes the stall |

Then one line: **the single worst one**, and whether you are fixing it now.

If you found nothing, say so plainly and name the riskiest element you checked.
"No stalls" with nothing behind it is not a review.

End every report with a verdict line, so a pipeline can gate on it:

```
VERDICT: PASS | STALLS <count> | worst: <Where>
```

`PASS` only when the walk found no stalls. Anything else blocks.

### 5 · Fix, then re-walk

Fix the findings. Then **walk it again from step 3**, because fixes move things
and a fix that pushes the number they came for below the fold is a new stall.

Two rounds maximum. If stalls remain after two, present anyway and say which
ones you knowingly left.

## Running unattended

When this skill runs inside an automated pipeline with no human to ask:

- Do not stop to ask which persona. Use the one the pipeline names, or `owner`.
- If the persona file is missing, write it from the template, mark every line
  as assumed, and say so in the report.
- Still walk, still report, still end with the verdict line.

## The specific failures this catches

Check each one explicitly on every walk.

| Failure | The test |
|---|---|
| **Zero for "not computed"** | Every number that could be blank: does it read as a fact, when it is actually an absence? `$0.00` is a finding; "Not calculated yet" is a state. |
| **Internal IDs on screen** | Anything rendering as a bare number that is really a record. The reader has never seen an internal ID and will read `142` as a quantity. |
| **A code with no remedy** | Every error, exception or warning: does it say what to do, or only what happened? |
| **Contradictory state** | Two indicators that can both be true and must not be. Derive them from one value, never from independent booleans. |
| **Unmarked destructive action** | Every button: does the screen say, before the press, whether it touches live data? |
| **The wall of text that hides the decision** | Any long block: is there a question inside it that needs an answer, and is it visible without reading the block? |
| **Dark mode** | Every colour that carries meaning: was it defined once for light only? |

## Interaction with other skills

If a design or UI skill is available, run this **after** it has produced the
design, not instead of it. Guidelines say how to build; this says whether the
person who has to use it can.
