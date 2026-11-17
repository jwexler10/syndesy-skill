# Syndesy

**Choose a defensible approach. Make a hybrid earn its complexity.**

An agent skill for recommendations that compare alternatives fairly, challenge the favored option, and commit to a choice supported by evidence.

## What it does

- Defines success and distinguishes causal facts from assumptions.
- Uses the same decision criteria for each credible alternative.
- Checks whether option order or the user's enthusiasm is steering the answer.
- Names a recommendation, its strongest competitor, its tradeoff, and reversal conditions.

For decisions rather than unrestricted brainstorming. A genuinely necessary combination can win; automatic compromise and automatic contrarianism cannot.

## Install

This repository contains a portable, instruction-only agent skill. No API key,
MCP server, executable script, or companion skill is required. Tools are useful
when your task needs current information or inspection of an existing project.

1. Download this repository with **Code → Download ZIP**, or clone it:

   ```bash
   git clone https://github.com/jwexler10/syndesy-skill.git
   ```

2. For a Codex project, copy the entire `skills/syndesy` folder into the target
   project's `.agents/skills/` directory. The result should be:

   ```text
   your-project/
     .agents/
       skills/
         syndesy/
           SKILL.md
   ```

   Keep any supporting files inside that folder when copying. For user-wide local
   Codex discovery, use `~/.agents/skills/syndesy/` instead. Choose one scope to avoid
   installing duplicate copies.

3. In Codex, invoke the skill with `$syndesy` followed by your task, or let the
   agent select it when your task matches the description. If it does not appear,
   restart Codex. See the [official skills guide](https://learn.chatgpt.com/docs/build-skills).

For another agent that supports `SKILL.md`, use that agent's documented skills
directory. You can also explicitly ask an agent to read and apply
[`skills/syndesy/SKILL.md`](skills/syndesy/SKILL.md). Discovery and invocation syntax
depend on the host.

## Try it

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

## Repository contents

- [`skills/syndesy/SKILL.md`](skills/syndesy/SKILL.md): the complete skill.
- [`LICENSE`](LICENSE): MIT license for these instructions and documentation.

Copyright © 2026 Jason Wexler.
