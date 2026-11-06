# 🔄 Continuous Agent Loop

[![ClawHub Skill](https://img.shields.io/badge/ClawHub-Skill-blue)](https://clawhub.ai/djc00p/continuous-agent-loop) [![Agent Skill](https://img.shields.io/badge/Agent-Skill-blue)](#) [![Quality Gates](https://img.shields.io/badge/Quality-Gates-brightgreen.svg)](https://en.wikipedia.org/wiki/Quality_control) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Continuous Agent Loop** provides canonical patterns for autonomous agent loops with **quality gates** and **recovery controls**.

A loop without gates is just a script that runs until it burns through your budget. A loop without recovery is a script that stops at the first error and waits for a human. This skill covers both — the patterns themselves, and the controls that keep them from misbehaving.

---

## 🔁 Loop Selection

```text
Need strict CI/PR control?
  → continuous-pr

Need RFC decomposition?
  → rfc-dag

Need exploratory parallel generation?
  → infinite

Default → sequential
```

| Loop | Shape | Best For | Recovery |
|------|-------|----------|----------|
| **Sequential** | Task → execute → verify → repeat | Stable, incremental work | Freeze, audit, reduce scope |
| **RFC-DAG** | Decompose → parallel branches → merge | Complex multi-part features | Replay the failing unit |
| **CI/PR** | Generate → test → push PR → merge on pass | Code-heavy deliverables | Fail fast, surface root cause |
| **Infinite/Exploratory** | Generate variants in parallel, filter winners | Creative or search-heavy work | Stop on quality threshold |

---

## 🛡️ Human Approval Boundaries

These loop patterns automate repository work. Some of that work reaches **shared and remote systems**, so it needs an explicit human gate.

**Always require explicit human confirmation before:**

* creating a pull request
* pushing to a remote
* merging a branch
* starting any long-running or persistent loop
* publishing a release or tag

---

## 🎯 Scope Every Run to One Project

Set `AUDIT_ROOT` (or the loop's `--root` flag) to the specific repository you intend to work on, and **confirm it before the loop starts**.

> ⚠️ Do not point it at a home directory or a parent folder containing unrelated code. A loop with an ambiguous root will happily modify the wrong thing, repeatedly.

**Prefer dry runs.** Where a loop supports one, run it in dry-run mode first and read the proposed actions before approving execution.

---

## 🏗️ Production Stack (Recommended)

1. **RFC decomposition** — break large requests into a DAG of sub-tasks before looping
2. **Quality gates** — define explicit pass/fail criteria *before* starting each iteration
3. **Eval loop** — run automated checks after each iteration to verify progress
4. **Session persistence** — checkpoint state between iterations so you can resume on failure

---

## 🧠 Key Patterns

### Sequential Loop

* Single task → execute → verify → repeat
* Best for: stable, incremental work
* Recovery: freeze, audit, reduce scope

### RFC-DAG Loop

* Decompose request → parallel branches → merge results
* Best for: complex multi-part features
* Recovery: replay failing unit

### CI/PR Loop

* Generate → test → push PR → merge on pass
* Best for: code-heavy deliverables
* Recovery: fail fast, surface root cause

### Infinite / Exploratory Loop

* Generate variants in parallel, filter winners
* Best for: creative or search-heavy work

---

## 📚 References

* `references/loop-patterns.md` — detailed pattern implementations
* `references/quality-gates.md` — defining pass/fail criteria and eval loops
* `references/recovery.md` — failure handling, checkpointing, and resume strategies

---

**Adapted from [everything-claude-code](https://github.com/affanm/everything-claude-code) by [@affaan-m](https://github.com/affaan-m) (MIT).**

**Published by [@djc00p](https://github.com/djc00p)**
