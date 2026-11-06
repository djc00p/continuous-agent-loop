## Description:

Provides canonical patterns for continuous autonomous agent loops with quality gates, evaluations, and recovery controls.

This skill is ready for commercial/non-commercial use.

## Publisher:

[djc00p](https://clawhub.ai/user/djc00p)

### License/Terms of Use:

MIT-0

## Use Case:

Developers and engineers use this skill to structure continuous autonomous agent loops, choose loop patterns, define quality gates, recover from failures, and run deterministic harness audits on a selected repository.

### Deployment Geography for Use:

Global

## Known Risks and Mitigations:

Risk: Autonomous loop guidance includes PR creation, git pushes, merges, and persistent execution patterns that may proceed without clear human approval boundaries.

Mitigation: Require explicit confirmation before PR creation, git pushes, merges, and any long-running or persistent loop.

Risk: Repository audits may target an unintended path if AUDIT_ROOT or --root points outside the intended project.

Mitigation: Set AUDIT_ROOT or --root only to the repository that should be audited before running the harness audit.

Risk: Continuous loops can churn, repeat the same failure, or drift in cost when acceptance criteria and budgets are loose.

Mitigation: Define pass/fail quality gates, cap iteration or token budgets, freeze failing loops, reduce scope to the failing unit, and replay with explicit criteria.

## Reference(s):

- [Continuous Agent Loop on ClawHub](https://clawhub.ai/djc00p/skills/continuous-agent-loop)
- [Harness Audit Command](references/harness-audit.md)
- [Harness Audit Script](scripts/harness-audit.js)

## Skill Output:

**Output Type(s):** [text, markdown, code, shell commands, configuration, guidance]

**Output Format:** [Markdown guidance with inline shell commands; the harness audit can return text or JSON scorecards.]

**Output Parameters:** [1D]

**Other Properties Related to Output:** [Requires AUDIT_ROOT or --root to point at the intended audit target.]

## Skill Version(s):

1.0.3 (source: server release evidence)

## Ethical Considerations:

Users should evaluate whether this skill is appropriate for their environment, review any generated or modified files before relying on them, and apply their organization's safety, security, and compliance requirements before deployment.
