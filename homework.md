# Audit your team app

DSO 576 • Module 9 • Individual homework

Individually audit at least one feature and one number in your team’s app. Record your evidence and conclusions in `my-audit.md`.

### Work individually on the shared project

Use your team’s build or the professor-provided build of your team’s one-shot prompt. If using the professor’s read-only repository, clone it and copy its files into your team repository. Pull before starting and run the app in its own uv environment, not the course environment.

If change-requests.md is missing, copy the template from the module repository into the top folder of your team repository. Under Claims, add your name, the feature, and the number you will audit. Choose something different from your teammates, or explain the specific new evidence you contribute to an existing audit.

### 1 Audit one feature as its user

Identify the intended user and task. Compare the feature with your team’s prompt, recording reproducible examples of what works, is missing, or is misleading.

### 2 Audit one number

State what the number should mean and check that it makes sense. Consider its range, units, denominator, and a small case whose expected result you can calculate yourself. Then do at least one of the following:

Compute the number another way: for example, by hand, with a simple loop, an appropriate reference, or a simulation.

Go deeper into the calculation: identify and check the assumption or code line behind the result. Explain how it affects the answer.

Include a check the reader can reproduce; the displayed number or an agent’s explanation alone is not evidence.

### Optional support with talk it through

Optionally use `talk-it-through` to resolve an ambiguous requirement or metric. Record the agreed definition; no conversation transcript is required.

### 3 Record findings and requested changes

Add findings, evidence, and requested changes to the team’s `change-requests.md`. Do not undo a teammate’s work to demonstrate a finding.

<!-- pagebreak -->

## Submission and team follow through

### What to include in my audit

Your name, the feature and number audited, and the app version or commit checked.

The intended user and the relevant requirement or metric definition.

What you checked, including inputs or reproducible steps.

Expected and actual results, with your explanation of any difference.

Your conclusion, remaining uncertainty, and any change-request IDs.

What you personally contributed and how AI helped, if used.

Include code or a link to the committed check when needed to reproduce your evidence. State what your checks establish and what remains untested.

### Example change request

AUDIT-01 — Average tip per visit. Two visits have tips $10 and $0; the first has two services. Actual: $6.67. Expected: $5. Cause: the service merge duplicates the first tip. Request: average at the visit level. Check: adding a service must leave the mean at $5.

### How the team uses the findings

Every few days, ask Codex to implement the open requests one at a time. For each request, rerun its evidence, commit with its ID in the message, and mark it built. Keep these shared implementation steps separate from your individual audit submission.

### Submit and practice

Submit your own my-audit.md on Brightspace by the deadline listed on /hw.

Complete Practice Quiz 9: ten samples in the course app, by the deadline listed on /hw.

Grading is based on effort, reasoning, and concrete checks. You do not need to find a bug.

AI may help you write code; the judgments and explanations are yours. Do not claim a teammate’s audit as your own.

