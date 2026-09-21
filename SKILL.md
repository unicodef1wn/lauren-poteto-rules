---
name: lauren-poteto-rules
description: Use when an engineering task requires diagnosis, runtime verification, correction of recurring agent failures, or coordination of delegated coding work.
---

# Lauren Poteto Rules

Engineering instructions for Grok Bot, adapted from Lauren Tan's ideas on verification, agent environments, and durable engineering judgment.

## Agent instructions

Use these rules for engineering investigation, implementation, review, and delegation. Follow the repository's instructions and the user's scope. Apply only the relevant parts: an explanation needs code evidence; a behavior change needs a running check; a typo needs a document check. Creating tooling or evaluating skills is conditional work, not a prerequisite for every task.

### 1. Pair with the human

Make the work understandable enough to review and maintain.

- For a non-trivial task, state the problem, material assumptions, and what would demonstrate success. Continue with routine choices already covered by the request.
- Explain consequential decisions using relevant code and observed behavior. Give the reviewer enough context to judge the result without reconstructing your session.
- Keep independent changes separable. When writing commits or pull requests, explain why behavior changed so history remains useful for investigation and reversal.
- Optimize for reviewed, working outcomes rather than code volume or pull-request count.

### 2. Earn trust with evidence

Close the loop between a claim and the running system.

- Before diagnosing a cause, inspect the affected implementation and trace the relevant calls or data flow. Cite the code and observations supporting your explanation. Mark an untested explanation as a hypothesis.
- For a bug, reproduce the reported behavior before fixing it, then repeat the same steps after the change. If reproduction is blocked, report the missing access, input, or environment and what remains uncertain.
- Exercise the interface users depend on: the UI, API, CLI, or device flow. A passing build alone does not prove runtime behavior.
- Match evidence to the claim. A screenshot can show appearance; interaction claims need an exercised sequence. Performance claims need comparable measurements, traces, or profiles.
- Check correctness and engineering quality separately. A passing flow does not establish that the implementation is maintainable or efficient.

### 3. Make verification repeatable

Give the next agent both a way to operate the app and a way to find the feature.

- Discover and reuse the repository's actual setup, run, test, and diagnostic tools. Never invent a verification command.
- Consult the feature map when available. It should connect a user-visible feature to its entry point, prerequisites, navigation steps, relevant code, and expected result. Confirm the affected entry against the running app.
- If agents repeatedly get lost, capture the verified route for that feature in existing project documentation. Avoid mapping the whole application for one small fix.
- When developing verification tooling, start locally or in another observable environment. Inspect its actions and failures before using it unattended.
- Turn recurring manual checks into reusable procedures when this fits the task. Record setup, inputs, expected outcomes, evidence locations, and cleanup needed. Keep affected procedures current when the product changes.

### 4. Treat the codebase and history as memory

Agents learn from the examples they find. Today's shortcut can become tomorrow's convention.

- Inspect nearby code and documented conventions before implementing. Use relevant history when the reason for a pattern is unclear.
- Validate a pattern before copying it. Frequency does not make an obsolete workaround correct.
- Fix the underlying cause within scope. If a workaround is necessary, explain its limitation and removal condition.
- Remove temporary scaffolding introduced by your work. Preserve useful explanations of non-obvious constraints; do not turn a one-off review remark into a permanent comment or universal rule.

### 5. Turn corrections into durable constraints

When the same mistake can recur, improve the environment that permits it.

Choose the smallest effective mechanism:

| Failure | Useful response |
|---|---|
| An invalid state or dependency can be designed out | Constrain the architecture, API, or data model. |
| A bad pattern can be detected mechanically | Add or reuse a type, lint, compiler, or CI check. |
| A decision requires context and judgment | Write a concise project rule or review criterion. |
| The agent lacks a repeatable procedure | Capture the workflow in a skill and evaluate its behavior. |

- Prefer enforceable constraints where feasible. Written rules and automated review remain fallible guidance.
- Verify that a new check rejects the bad case and permits a valid case.
- Record the general principle and when it applies. Omit the incident's names and history. Extend existing instructions rather than accumulating duplicates.
- Follow the target project's constraints. Lauren's project-specific bans on comments or `useEffect` do not establish universal bans.
- Keep broader architectural changes as a scoped follow-up when they exceed the task.

### 6. Keep the supported path healthy

Make the shortest route to an implementation follow the intended design.

- Use the canonical helper or module when it meets the need. If it lacks a capability, consider a scoped improvement before adding a competing implementation.
- If several patterns conflict, inspect their usage and constraints before selecting one.
- During maintenance, update obsolete examples and callers together. If existing debt cannot be removed yet, consider preventing new instances while tracking existing exceptions.
- In a new project, establish a minimal working example and enforce important boundaries before agents replicate the first implementation across features.

### 7. Evaluate rules and skills

Apply this when creating or changing agent instructions or verification workflows.

- Start with an observed failure and define the behavior that should improve. Skills should grow from evidence about how agents work.
- Use representative tasks and observable criteria: did the agent inspect relevant code, exercise the flow, and provide valid evidence? Include a routine task to detect unnecessary process. A dedicated evaluation framework is optional.
- Compare behavior before and after the change when practical. Inspect tool calls, edits, and artifacts, not the agent's confidence or a score alone.
- Keep expected answers out of the evaluated agent's task. Use fresh sessions and the intended model and environment where available.
- Inspect failures and refine the smallest relevant instruction or tool. Re-run affected cases after changes. If execution is unavailable, label the revision untested rather than claiming improvement.

### 8. Scale only what you can verify

Increase autonomy after the verification loop works reliably.

- Before expanding unattended work, demonstrate that one representative task can be investigated, implemented, exercised, and reviewed using available tools.
- When delegating, pass the repository and revision, scope, relevant instructions, verification procedure, and expected evidence. Make ownership explicit for parallel work.
- Inspect returned changes and evidence. Verify the integrated result when independent changes can interact; a worker's completion message alone is insufficient.
- Preserve the user's existing action boundaries. Successful verification does not grant additional permission.

### Completion report

Finish with the result, checks actually performed, accessible evidence, and any material limits. Keep it proportional to the task. Distinguish observed results from hypotheses and worker-reported results from checks you performed yourself.
