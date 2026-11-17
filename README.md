# Syndesy

**Choose a defensible approach. Make a hybrid earn its complexity.**

An agent skill for recommendations that compare alternatives fairly, challenge the favored option, and commit to a choice supported by evidence.

## Install in one command

```bash
npx skills add jwexler10/syndesy-skill
```

Choose Claude Code, Cursor, Codex, or another supported agent in the installer.
Requires [Node.js](https://nodejs.org/) 22.20 or later. Installs to the current project
by default; add `--global` for a user-wide installation. See the
[skills CLI](https://github.com/vercel-labs/skills) for supported agents and options.

For a noninteractive installation to Claude Code, Cursor, and Codex together:

```bash
npx skills add jwexler10/syndesy-skill --skill syndesy --agent claude-code cursor codex --yes
```

Prefer a graphical install? Use the Claude marketplace option below.

## What it does

- Defines success and distinguishes causal facts from assumptions.
- Uses the same decision criteria for each credible alternative.
- Checks whether option order or the user's enthusiasm is steering the answer.
- Names a recommendation, its strongest competitor, its tradeoff, and reversal conditions.

For decisions rather than unrestricted brainstorming. A genuinely necessary combination can win; automatic compromise and automatic contrarianism cannot.

## Before vs. after

**Example request:** “Our only logging-stack maintainer is leaving. A managed service meets our requirements at similar cost. Should we keep both permanently?”

| Aspect | Without the skill: illustrative pitfall | With Syndesy: intended behavior |
|---|---|---|
| Evaluation | Treats keeping both as automatically safer. | Tests which requirement a second, unmaintained stack would actually meet. |
| Recommendation | Says both options have merits and leaves the choice open. | Names one target approach, its strongest competitor, and the tradeoff that decides the choice. |
| Uncertainty | Adds a backup without an end condition. | States what would reverse the choice and gives temporary coexistence an explicit removal condition. |

These are illustrative comparisons, not recorded model outputs or benchmark results.
Actual results depend on the model, the prompt, and the evidence you provide.

## Install as a Claude plugin

This repository is both a standalone skill and a single-plugin marketplace. The
plugin and the skills CLI install the same `SKILL.md`; choose one route per host
to avoid duplicate installations.

### Claude and Cowork: no terminal

1. Open **Plugins** (or **Customize → Plugins**, depending on your version).
2. Choose **Add → Add marketplace → Add from a repository**.
3. Enter `jwexler10/syndesy-skill` or `https://github.com/jwexler10/syndesy-skill`.
4. Select **Syndesy** and add the plugin. Find its skill through `/` or the
   skill picker; when namespaced commands are shown, use `/syndesy:syndesy`.

Availability and organization controls depend on your Claude plan and account.
See [Anthropic's plugin installation guide](https://support.claude.com/en/articles/13837440-use-plugins-in-claude).

### Claude Code: marketplace commands

Run these inside Claude Code:

```text
/plugin marketplace add jwexler10/syndesy-skill
/plugin install syndesy@jwexler10-syndesy
```

Then invoke `/syndesy:syndesy` followed by your task. The marketplace is defined in
[`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json), and the plugin
in [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json).

### Manual installation

Download the repository using **Code → Download ZIP**, or clone it:

```bash
git clone https://github.com/jwexler10/syndesy-skill.git
```

Copy the entire `skills/syndesy` folder, including any supporting files, into the
appropriate directory in your target project:

| Agent | Project skill directory | Invocation |
|---|---|---|
| Claude Code, direct skill | `.claude/skills/syndesy/` | `/syndesy` |
| Codex | `.agents/skills/syndesy/` | `$syndesy` |
| Cursor | `.cursor/skills/syndesy/` | Ask the agent to use Syndesy. |

Each destination must contain `SKILL.md` directly. Other hosts may use different
discovery or invocation rules; follow their documentation. See the
[Codex skills guide](https://learn.chatgpt.com/docs/build-skills).

This is an instruction-only skill: no API key, MCP server, companion skill, or
executable script is required. Tools are useful when your actual task needs live
information or inspection of an existing project.

## Try it

The prompts below use Codex's `$syndesy` syntax. In Claude Code, use `/syndesy` for a
direct skills installation or `/syndesy:syndesy` for a marketplace plugin. In Cursor,
ask the agent to use Syndesy and give it the same task.


```text
$syndesy Should we maintain our self-hosted logging stack or move to a managed service? Compare both against the same criteria and recommend one.
```

```text
$syndesy Our team proposes keeping both implementations permanently as backups. Does that combination meet a requirement one approach cannot?
```

```text
$syndesy We can fund either onboarding improvements or reporting exports this quarter. Pick one using the evidence below; do not split the budget.
```

Expect one target approach, decisive evidence, the strongest rejected alternative, the cost of the choice, and what would reverse it.

## Adapt it

Supply your actual objective, constraints, evidence, and priorities. Edit the skill
to fit your workflow. It assumes no particular product, repository structure,
technology stack, or internal decision log. Applying a thinking skill does not
itself authorize changes, purchases, deployments, or other external actions.

Optional research context: [background](skills/syndesy/references/background.md). It is not required to use the decision procedure.

## Related skills

Each skill works independently. Choose the workflow that matches your question:

| Skill | Use it to |
|---|---|
| [Aristotle](https://github.com/jwexler10/aristotle-skill) | Challenge assumptions and reason from first principles. |
| [Apple](https://github.com/jwexler10/apple-skill) | Work backward from the user experience to the technology. |
| [Bushnell](https://github.com/jwexler10/bushnell-skill) | Design immediate value and meaningful depth across repeated use. |
| [Evgenii](https://github.com/jwexler10/evgenii-skill) | Evaluate economic outcomes, incentives, and uncertainty. |

Read the practical guide: [Five reusable workflows for better product and engineering decisions](https://github.com/jwexler10/aristotle-skill/blob/main/docs/five-decision-workflows.md).
It includes a worked decision, installation steps, and the limits of the current validation.

## Repository contents

- [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json): Claude plugin metadata.
- [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json): installable marketplace catalog.
- [`skills/syndesy/SKILL.md`](skills/syndesy/SKILL.md): the complete skill.
- [`LICENSE`](LICENSE): MIT license for these instructions and documentation.

Copyright © 2026 Jason Wexler.
