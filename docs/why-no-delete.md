# Why devclean Does Not Delete Files (At Least for Now)

When people first encounter devclean, a very common and reasonable question comes up:

> **“If devclean already knows which directories are build artifacts, why doesn’t it just delete them for me?”**

This is a fair question.  
But devclean’s decision to **never delete files** is not a temporary limitation — it is a deliberate design choice.

---

## Deletion Has Never Been the Hard Part

For developers, deleting files is trivial:

- `rm -rf`
- `cargo clean`
- `npm install`
- `gradle clean`

These tools have existed for years and are widely understood.

The real difficulty is not *how* to delete something, but:

> **“Am I confident this is safe to delete?”**

---

## devclean Solves Uncertainty, Not Execution

devclean exists to answer a specific kind of question:

> **Is this directory a build artifact? Why? How risky is it to remove?**

This is a **decision problem**, not an execution problem.

The moment devclean starts deleting files, it stops being:
- a tool that provides judgment and context

and becomes:
- a tool that takes responsibility for the outcome

Those two roles carry very different risk profiles.

---

## Deletion Instantly Changes the Trust Model

Even with:
- multiple confirmations
- `--force` flags
- “I know what I’m doing” switches

file deletion changes how users perceive responsibility.

| Tool behavior | User mindset |
|--------------|-------------|
| Analysis only | “I’m reviewing suggestions” |
| File deletion | “The tool made this decision” |

devclean intentionally avoids becoming the party that “made the call”.

---

## Scan-only Is a Safety Boundary

One of devclean’s core principles is:

> **Analysis and execution must be separated**

- devclean is responsible for:
  - scanning
  - explaining
  - assigning confidence
- the user is responsible for:
  - deciding
  - executing
  - accepting the consequences

This boundary makes devclean:
- more predictable
- easier to trust
- suitable for large, unfamiliar, or inherited codebases

---

## Suggested Commands: Reducing Friction Without Crossing the Line

To reduce user effort, devclean may provide:

> **Explicit, copy-paste-ready cleanup commands**

For example:

```text
Suggested command:
  cargo clean
````

These commands:

* are never executed automatically
* remain entirely under user control
* usually rely on ecosystem-native tooling

This design delivers **nearly the same convenience as deletion**, without shifting responsibility.

---

## Not Deleting Is a Long-Term Trust Decision

devclean intentionally chooses to:

* do less
* move slower
* be conservative

Because in filesystem operations, **a single mistaken deletion can be irreversible**.

Trust, once lost, is very hard to recover.

---

## Will devclean Ever Support Deletion?

Possibly — but only under very strict conditions.

Any future deletion capability would require:

* being disabled by default
* explicit, interactive confirmation
* a rollback mechanism (e.g. moving files to a private trash)
* complete audit logging
* strict separation from analysis logic

Until then, **scan-only remains a core feature, not a missing one**.

---

## Summary

devclean is not about deleting files.

It is about this:

> **Helping you stop hesitating before you delete them yourself.**

Deletion is easy.
Making the *right* deletion decision is the hard part.

That is the problem devclean is designed to solve.
