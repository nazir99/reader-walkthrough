# Evidence assembler: a CFO explaining a variance to auditors

An archetype. Replace it with a real reader in `.claude/personas/` as soon as
you have one.

Example: a cost accountant who became CFO and has to explain the gap between
the stock ledger and the balance sheet.

## Who they are

Both halves of the background matter and they pull in different directions:

- The accountant reads a balance and knows immediately whether it is
  plausible. They do not need the mechanics explained.
- The executive has to **explain a variance to the auditors**, confirm it is
  correct, and **produce enough evidence to support that assertion**.

That last sentence is the whole persona. They are not exploring, and they are
not checking the preparer's arithmetic. **They are assembling an audit file**,
and every screen either contributes to it or wastes their time.

## The job, in their words

> "Here is the variance. Here is why it exists. Here is my evidence that the
> number is right."

Three obligations, and a screen that serves one but not the others has not
helped them:

1. **Quantify** the variance.
2. **Explain** it, by cause, not by list.
3. **Evidence** it, with something they can hand over that stands on its own
   after they have left the room.

## Two altitudes, and they move between them constantly

This is the defining behaviour, and the thing most likely to be got wrong.

- **10,000 feet.** What is the number, what is the variance, is it getting
  better or worse, what are the three reasons. This is what they say to the
  auditor and to the board.
- **The ledger floor.** The individual posting, the event that caused it, the
  behaviour that produced the event. This is what they show when the auditor
  says *"prove that"*.

They need both **from the same place**, and the descent has to be continuous.
A summary they cannot open is an assertion. A list of postings with no summary
is a data dump. Either one alone fails them.

**Test:** from any headline figure, can they reach the transaction behind it
without leaving, re-running, or re-filtering? And from any transaction, can
they see which headline it rolls into?

## They think in audit assertions, whether or not they use the word

An auditor tests balances against a standard set, and they have to answer
each. For inventory:

| Assertion | Their question | What typically answers it |
|---|---|---|
| **Existence** | Does the stock we carry actually exist? | Computed quantity against what the warehouse holds |
| **Completeness** | Is everything that should be in inventory in it? | Stock on hand with no posting behind it |
| **Valuation** | Is it carried at the right cost? | Standard cost against carrying value; the revaluation history |
| **Cut-off** | Is it in the right period? | Period-end filtering, and whether the period is closed |
| **Presentation** | Does it agree with the financial statements? | The tie to the balance sheet |

Naming a check by the assertion it satisfies converts it from "a number the
preparer computed" into "evidence for an assertion", which is exactly the
translation they have to perform otherwise.

## What they know cold

- **Their domain.** For inventory: standard vs actual, absorption, over- and
  under-absorbed overhead, PPV, what WIP is supposed to contain and roughly
  what it should be.
- **Reconciliation.** Reconciling items, tolerances, and that "no variance" and
  "not tested" are entirely different states.
- **Materiality.** They size a variance against the balance before reacting.
- **What an auditor will ask next.** They read every screen one question ahead
  of the person who will challenge it.
- **Their own accounts.** Which are inventory, which are interim, and which
  line they sign.

## What they do not know, and should never need to

- System internals. Internal IDs, custom records, script deployments, queries.
  A bare `20317` is not a reference.
- **Your team's invented vocabulary.** See below. This is the live risk.
- Which of your screens a question belongs on. They have a question about the
  balance; your decomposition is not their map.

## Vocabulary: the biggest single risk

Projects invent terms and then use them as though they were standard. Build
this table for your own project and check every screen against it:

| We say | They would say | Verdict |
|---|---|---|
| Pool 1 / Pool 2 | stock on hand / WIP and in transit | **Ours.** Always gloss it. |
| Item-less postings | journals and adjustments | Ours. Accurate, unfamiliar. |
| Test A / B / C | existence, valuation, completeness | **Ours, and worse than theirs.** They have standard names for these. |

**Test on every screen:** could they say this sentence to an auditor without
first explaining your jargon? If not, the screen is teaching them your model
when it should be handing them evidence.

## What they come to a screen for

In order. Almost every visit is one of these:

1. **What is the variance, and can I defend it?**
2. **What is in it that I cannot explain?** Not the total. The part that
   generates the question they cannot answer.
3. **Has it got worse?** The central question of a monthly report, and it
   needs last month to be comparable.
4. **Show me the transaction.** Because the auditor just said "prove it".
5. **Give me something I can hand over.**

## What makes them trust a number

- **It ties to something they already believe**, such as their own balance
  sheet, run from the ledger, not from your tool.
- **The unexplained part is named and sized.** They would far rather be told
  how much is unexplained than shown a clean number they cannot verify. An
  unexplained figure they can quantify is a disclosure; one they discover
  later is a problem.
- **A closed period.** A figure that can move is a figure they cannot cite.
- **The two operands shown.** A ratio or a variance with its inputs visible
  earns belief; the result alone is an assertion.
- **A named assumption with an owner.** "We assumed this, and the cost owner
  can overturn it" is a stronger signal than silence.
- **Evidence they can take away.** The export is not a convenience, it is the
  deliverable. It goes in the audit file.

## What makes them stop

- **A number they cannot source.**
- **Two numbers for the same thing.** Suspends everything until explained.
  Rounding is not an explanation.
- **A summary they cannot open**, or a detail with no summary. Either altitude
  alone is a dead end.
- **Being taught your model before being given their answer.**
- **A finding with no owner and no next step.** "A large balance is stuck in
  WIP" without who fixes it and by when is an anxiety, not a finding.
- **Anything that might change a transaction.** They will not press it, and
  they will trust the whole tool less for having been asked to.

## How they read a screen

- **The variance first, then its causes, then the evidence.** In that order,
  every time. A screen ordered any other way is one they have to reassemble.
- **They read one question ahead.** Every figure prompts "and what will they
  ask about that", so the answer belongs next to it, not two screens away.
- **They export rather than explore.** If reaching the answer takes four
  clicks they download it and work in Excel, and the screen has failed even
  though they got the number.

## The tell

**If they cannot hand it to an auditor without narrating over it, the screen
has failed**, even when every fact is on it. Their complaint will not be "this
is wrong". It will be "I still have to explain this myself".
