# Examples

Use these scenarios to understand or evaluate the skill. They are illustrative, not quotations from Lauren or measured product claims.

## A green build, a broken flow

**Task:** Fix a search filter that disappears after opening an item and navigating back.

**Failure:** The agent changes state handling, runs the build, and reports success.

**Expected:** Reproduce the navigation sequence, make the scoped fix, repeat the same sequence, and provide evidence showing the filter and results after returning.

## A confident diagnosis without evidence

**Task:** Investigate why notifications arrive twice. Do not implement a fix.

**Failure:** The agent blames duplicate subscriptions without inspecting the notification path.

**Expected:** Trace the producer, delivery path, and consumers. Inspect relevant code and logs, reproduce the duplication if possible, and distinguish supported findings from hypotheses.

## Yesterday's workaround becomes today's convention

**Task:** Add a data view beside one that retries with a fixed delay.

**Failure:** The agent copies the delay because nearby code uses it.

**Expected:** Determine why the delay exists and whether the new view shares that constraint. Use the supported loading path when it covers the case. Flag unrelated debt without expanding the task.

## The same correction in every review

**Task:** Fix another module that imports an internal implementation instead of its public entry point.

**Failure:** The agent corrects the import and adds another reminder to the prompt.

**Expected:** Correct the import, then inspect whether exports, types, linting, or CI can prevent recurrence. Verify any new check against both forbidden and valid imports.

## The agent can launch the app but cannot find the feature

**Task:** Verify a report about a slow history panel.

**Failure:** The agent launches the app and clicks around without reaching the reported state.

**Expected:** Use the feature map or inspect the route and prerequisites. Reach the panel with representative data, reproduce the interaction, and collect an appropriate timing or trace. Correct stale navigation instructions using steps actually verified.

## A spelling fix grows into a framework

**Task:** Correct a typo in a documentation heading.

**Failure:** The agent launches the application, creates verification tooling, and rewrites adjacent documentation.

**Expected:** Correct the heading, check affected links or anchors, and inspect the diff.
