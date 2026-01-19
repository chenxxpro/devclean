# Changelog

All notable changes to this project will be documented in this file.

This project follows a principle of **explicit scope and conservative behavior**.
New features are added only when backed by real-world feedback.

---

## [0.1.0] – Initial exploration release

> This is a validation-focused release.
> devclean is intentionally limited and scan-only.

### Added
- `scan` command to analyze a development directory
- Detection of common project ecosystems (Rust, Node.js, Python, Java)
- Identification of well-known build and dependency directories
- Explainable output with:
  - Detected directory
  - Reasoning / evidence
  - Confidence level (high / medium / low)

### Design decisions
- devclean **does not delete files or directories**
- All analysis runs in **dry-run mode**
- Rules are explicit and conservative
- Uncertain cases are clearly marked as such

### Non-goals (for this release)
- Automatic cleanup or deletion
- System-wide cache cleaning
- Heuristic or ML-based detection
- Broad ecosystem coverage

### Known limitations
- Detection is rule-based and incomplete
- Confidence levels are qualitative
- Output format may change based on feedback

### Feedback focus
We are especially interested in:
- Directories you were unsure about deleting
- Cases where the explanation was insufficient
- Build artifacts that were missed
- Situations where devclean helped reduce hesitation

---

## Future releases

Future versions will be guided by:
- Real hesitation scenarios reported by users
- Repeated false positives or false negatives
- Evidence quality, not feature count

Features that increase automation or risk will only be considered
after strong trust has been established.
