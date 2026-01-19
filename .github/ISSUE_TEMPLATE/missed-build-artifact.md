## devclean missed an obvious build artifact

**Use this template when** you are confident a directory is safe to delete, but devclean did not flag it.

### 1. Directory details

* Directory name / path:
* Language / framework:
* How this directory is generated (if known):

### 2. Why are you confident it is regenerable?

* [ ] Official documentation states it can be regenerated
* [ ] It is created by a known build command
* [ ] It appears on every build
* [ ] Other:

### 3. Can you suggest a detection signal?

(e.g. marker files, commands, directory patterns)

---

## 📌 Maintainer note (please keep)

* This project intentionally avoids feature creep at this stage.
* We prioritize issues that reveal:

  1. Real hesitation and fear of deletion
  2. Incorrect or missing rule detection
  3. Explanations that fail to build trust

> A single real-world “I wasn’t sure if I could delete this” story is more valuable than ten feature requests.
