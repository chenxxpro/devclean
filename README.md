# devclean

> A safe, explainable development directory analyzer.
>
> **devclean does not delete anything.**

---

## What is devclean?

`devclean` scans a development directory and **explains which folders are likely safe to delete — and why**.

It is designed for developers who:

* Work with **multiple languages or frameworks**
* Maintain **monorepos or long-lived projects**
* Have directories they *suspect* are build artifacts, but **don’t dare to delete**

Unlike traditional cleanup tools, devclean focuses on **analysis and trust**, not automation.

---

## What problem does it solve?

Most developers eventually face directories like these:

```text
./target/
./node_modules/
./build/
./dist/
./.cache/
```

You *think* they are safe to remove — but you are not 100% sure.

**If devclean made you hesitate more or less, please open an issue.**

Current options are unsatisfying:

* `rm -rf` — fast but dangerous
* `git clean -xfd` — even more dangerous
* Language-specific tools — only work within one ecosystem

`devclean` exists to answer one question:

> **“Can I delete this directory?”**

And just as importantly:

> **“Why do you think so?”**

---

## What devclean does (and does not do)

### ✅ What it does

* Detects common project types (Rust, Node.js, Python, Java, …)
* Identifies **well-known build or dependency directories**
* Explains its reasoning using clear evidence
* Assigns a confidence level to each suggestion
* Runs in **dry-run mode only**

### ❌ What it does NOT do

* ❌ It does **not delete files or directories**
* ❌ It does **not promise 100% correctness**
* ❌ It does **not scan your entire system**
* ❌ It does **not try to be “smart” with ML or heuristics**

If you want an automatic cleanup tool, this is probably **not** for you.

---

## Example usage

```bash
$ devclean scan .
```

Example output:

```text
Found 4 directories worth reviewing:

✔ target/          Rust Cargo build directory
  Evidence: Cargo.toml found in project root
  Confidence: high

✔ node_modules/    Node.js dependencies
  Evidence: package.json found
  Confidence: high

⚠ .cache/          Mixed-use cache directory
  Evidence: name matches common cache pattern
  Confidence: low

✖ src/             Source code directory
  Reason: protected path
```

You decide what to delete — devclean only provides context.

---

## Supported ecosystems (initial)

* Rust (Cargo)
* Node.js (npm / yarn / pnpm)
* Python (venv / pyproject-based workflows)
* Java (Maven / Gradle)

Support is intentionally conservative and rule-based.

---

## Design philosophy

1. **Safety over convenience**
2. **Explainability over cleverness**
3. **Explicit uncertainty over false confidence**

A suggestion you understand is better than an action you regret.

---

## Project status

🚧 **Early exploration / validation stage**

* The current goal is to validate whether this tool solves a real pain point.
* APIs, rules, and output formats are **not stable**.
* Feedback is far more valuable than code contributions at this stage.

---

## Feedback wanted

If you find this idea useful, we would love to hear:

* What directories do you hesitate to delete?
* Which languages or frameworks should be supported first?
* What information would make you trust a suggestion?

You can open an issue or simply comment with examples.

---

## Non-goals

To keep the project focused, devclean explicitly avoids:

* One-click cleanup
* System-wide cache removal
* IDE- or editor-specific cleanup
* "Magic" detection without explanation

---

## License

TBD

---

> devclean is an attempt to reduce *fear-driven disk usage* in development environments.

---

## IMPORTANT

This tool analyzes only. It never deletes files.