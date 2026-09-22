![Lauren Poteto's skill for your Grok Bot](assets/cover.png)

# Lauren Poteto Rules

A portable engineering skill inspired by [Lauren Tan's](https://x.com/poteto) talks about working with coding agents.

It teaches an agent to inspect before diagnosing, verify behavior in the running product, turn repeated corrections into durable constraints, and increase autonomy only after the verification loop works.

## What it changes

- **Evidence before confidence.** A diagnosis must come from relevant code and observed behavior.
- **Run the product.** Builds and type checks do not prove a user flow works.
- **Make verification reusable.** Record how to reach and exercise important features.
- **Treat the codebase as memory.** Agents copy existing patterns, including bad ones.
- **Improve the environment.** Prefer architecture, types, lint rules, and CI over repeated review comments.
- **Evaluate agent instructions.** Change skills in response to observed failures and test the resulting behavior.
- **Scale trust gradually.** Delegate more work only when results remain reviewable and reproducible.

Read the complete instructions in [SKILL.md](SKILL.md). See [EXAMPLES.md](EXAMPLES.md) for concrete failure modes and expected behavior.

## Install

### Grok Bot

Download [SKILL.md](SKILL.md), attach it to a Grok Bot conversation, and send:

```text
Create a private skill named "Lauren Poteto Rules" from the attached SKILL.md.
Preserve its scope and instructions. Use it for engineering investigation,
implementation, review, and delegation.
```

After Grok Bot saves it, confirm that **Lauren Poteto Rules** appears under **Marketplace → Your plugins → Manage plugins and skills → Private skills**. Invoke it from the `/` menu when needed.

For a one-off task, attach `SKILL.md` and ask the Bot to follow it without saving a skill.

### Grok CLI

Clone the repository into Grok's personal skills directory:

```bash
mkdir -p ~/.grok/skills
git clone https://github.com/unicodef1wn/lauren-poteto-rules.git \
  ~/.grok/skills/lauren-poteto-rules
```

Start a new session and invoke `/lauren-poteto-rules`. To share it only inside one project, place the folder at `.grok/skills/lauren-poteto-rules` in that repository.

### Codex

Clone it into the user skills directory:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/unicodef1wn/lauren-poteto-rules.git \
  ~/.agents/skills/lauren-poteto-rules
```

Start a new Codex session and invoke `$lauren-poteto-rules`. For one repository, use `.agents/skills/lauren-poteto-rules` instead.

### Claude Code

Clone it into Claude Code's personal skills directory:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/unicodef1wn/lauren-poteto-rules.git \
  ~/.claude/skills/lauren-poteto-rules
```

Invoke it with `/lauren-poteto-rules`. For a project installation, use `.claude/skills/lauren-poteto-rules`.

### Cursor CLI

Install [Cursor CLI](https://cursor.com/docs/cli/overview) and run `cursor-agent login`
if you are not already authenticated. Clone the skill into Cursor's personal skills
directory:

```bash
mkdir -p ~/.cursor/skills
git clone https://github.com/unicodef1wn/lauren-poteto-rules.git \
  ~/.cursor/skills/lauren-poteto-rules
```

Start a fresh CLI session from the project you want to work on:

```bash
cursor-agent
```

Ask it to use the installed skill explicitly:

```text
Use the lauren-poteto-rules skill for this task.
```

To check discovery without changing project files, run this from a project you trust
(`--trust` accepts workspace trust for this invocation):

```bash
cursor-agent --print --mode ask --trust \
  'Use the lauren-poteto-rules skill. Read its SKILL.md and report the file path and the rule about matching verification to the task. Do not edit files or run application tests.'
```

Check that the reported path is `~/.cursor/skills/lauren-poteto-rules/SKILL.md`
(expanded to your home directory) and the response cites the installed instructions.
This checks skill loading, not whether the agent will follow every rule in future tasks.

### Cursor editor

Create a project rule with **New Cursor Rule** or **Cursor Settings → Rules**. Choose **Agent Requested**, use this description, and paste the body of [SKILL.md](SKILL.md):

```text
Engineering workflow for evidence-based diagnosis, runtime verification,
durable constraints, and safe delegation.
```

Project rules live in `.cursor/rules` and can be committed with the codebase. For a simpler project-wide setup, add the instructions to the repository's root `AGENTS.md`.

## Use it

Give the agent a bounded engineering task and the real project context:

```text
Use Lauren Poteto Rules for this task.

Repository: <repository or working directory>
Task: <the behavior to investigate or change>
Expected result: <observable outcome>
Constraints: <scope or actions requiring approval>
```

A useful completion report states the result, the checks actually performed, the evidence, and anything still unverified.

## Evaluate it

Run the same tasks in fresh sessions with and without the skill. Compare actions and artifacts:

- Did the agent inspect the relevant code before naming a cause?
- Did it reproduce the bug or clearly explain the blocker?
- Did it exercise the affected user flow?
- Can another engineer repeat the verification?
- Did the change stay within scope?
- Did a small task remain small?

Use several runs. Judge tool calls, diffs, and evidence rather than the agent's confidence.

## Credits

The engineering principles are adapted from talks by [Lauren Tan (@poteto)](https://x.com/poteto). The wording, structure, installation guide, and examples are an independent community adaptation by [unicodef1wn](https://x.com/unicodef1wn).

Inspired by the compact packaging of [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills). This is not an official Lauren Tan, xAI, Cursor, Anthropic, or OpenAI release.

## License

[MIT](LICENSE)
