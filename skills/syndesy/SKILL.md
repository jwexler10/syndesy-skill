---
name: syndesy
description: Compare competing approaches and recommend a defensible choice using shared criteria, causal evidence, tradeoffs, and reversal conditions. Use for recommendations and decision deadlocks, including whether a hybrid is justified; leave open-ended brainstorming open.
license: MIT
---

# Syndesy — choose, don't blend

**Syndesy** (working term) is the habit of blending competing ideas, keeping every proposed approach, or landing on a middle ground without showing that the combination beats the alternatives. It reads as balanced and helpful, but it has three costs. The plan takes on the costs of both approaches. It loses whatever advantage each one had on its own. And the reader is left to make the decision they asked you to make.

The goal is the **most defensible path, and why**. That is not automatic compromise and not automatic contrarianism. Sometimes the user's idea wins, the existing system wins, or a combination wins. In every case it has to win on the evidence.

## Why agents drift this way (brief)

- **Established.** RLHF-trained assistants are sycophantic: humans and preference models prefer responses that match the user's stated view, sometimes over correct ones (Sharma et al., ICLR 2024). LLM judgments shift with presentation alone: the order of options and the length of answers both change verdicts (Wang et al. 2023; Zheng et al. 2023). Instruction-tuned models show human-like decoy effects more strongly than base models (Itzhak et al. 2023). In people, the middle option gains share, more so when the chooser expects to justify the choice (Simonson 1989), and the status quo is chosen disproportionately (Samuelson & Zeckhauser 1988).
- **Plausible, not established.** Training text overrepresents reconciliation ("both have merits"). A blended answer is hard to call wrong, so it feels like the low-risk reply.
- **Not the mechanism.** Token prediction does not average two ideas into a compromise, and models differ in their training objectives. RLHF is also linked to *over*confident wording (Leng et al. 2024), so stronger language is not the cure. Treat these as tendencies to check yourself for, not a diagnosis. Sources: `references/background.md`.

## Explore or decide?

When the user is brainstorming or asking what is possible, a range of options is the answer. Use this skill once the task needs a decision: the user asks what to do, a plan has to be executed, or one option has to be chosen. At that point, stop listing and commit.

## The procedure

Work through all eight steps. Show the conclusions compactly, not every step.

1. **Define success before looking at solutions.** Extract the objective, the hard constraints, the priorities in order, and the decision horizon (this week's fix or the five-year system). Separate what the user *requires* from what the user *assumes* or *hopes*. "We need sub-second sync" is a requirement. "Webhooks will fix it" is a hypothesis to test. Fix the criteria now. Changing them later so a favourite wins is the commonest way to cheat.
2. **Establish the causal facts.** Sort what you know into observations, interpretations, assumptions and unknowns. Name the mechanism that produces the problem. For each option, ask whether it changes that mechanism. An option that leaves the mechanism alone is not a fix, however well it is pitched.
3. **Build distinct alternatives.** Where relevant, include a repair, a replacement, and the other moves people forget: do nothing, delete something, buy it, defer it. Treat the current approach as one candidate. It gets no credit for existing. Its one real advantage is that the alternatives must pay a switching cost, so count that cost honestly. Present each option at its strongest. Do not invent a weak option to fill a slot, and do not leave out a strong one just because the user did not mention it.
4. **Use one rubric for everything.** Judge every option on the same criteria, weighted by the user's priorities. For engineering, use whichever apply: correctness, simplicity, maintainability, expressiveness, performance, operating cost, migration effort. Grade in words (better, worse, same, *blocking*). Avoid invented scores like "7.5/10". Count the complexity an option **removes** as well as the complexity it adds.
5. **Challenge the leading option.** State its strongest objection and name its strongest competitor. Hold both to the same standard of evidence. Ask what observation would make the recommendation wrong. Then run the **presentation test**: would you give the same answer if the options were listed in the other order and the user had championed the other one? If not, the framing is choosing for you.
6. **Choose.** Recommend one target approach and name the tradeoff that decided it. Reject the others with concrete reasons. "Each has advantages" is a step along the way, not a decision.
7. **Justify every component.** For each part of the plan, say what it contributes, what it costs, and **what fails if you remove it**. Parts that meet *different* requirements are a necessary composition. Parts that cover the *same* requirement as each other's backup are competing mechanisms. If the answer to "what fails if removed?" is "nothing, the other one covers it", remove it.
8. **State uncertainty and what would reverse the decision.** Name the missing facts that could change the answer. Where you can, go and check them: read the code, run the query, measure. Keep factual unknowns, which can be investigated, separate from value tradeoffs, which are the user's to weigh. If one unknown really does decide the outcome, say so plainly, give the cheapest way to resolve it, and give the rule: "if X, choose A; otherwise B". That is a decision procedure, not a hedge. Do not overstate your certainty, and do not hide the decisive unknown at the end.

## Decisiveness controls

- **The standard is an accountable decision-maker.** Make the recommendation a principal architect would defend in a postmortem. Claiming the persona is not enough. The defence is the evidence and the consequences.
- **"Choose exactly one" means one.** When the user says to pick one, do not offer a hybrid, a blend, "A with a little B", or a phased "A first, then B" that is a hybrid in disguise. If you think the constraint is costly, say so in one sentence *after* choosing.
- **A hybrid is its own candidate, with its own costs.** It brings two mechanisms, the joins between them, two ways to fail, unclear ownership, and twice the upkeep. Recommend it only when you can name a concrete requirement that the strongest simpler option fails, and show the hybrid meets it better.
- **Set tie-breakers before you choose.** Use the user's stated metrics first. If priorities leave a real tie, say so, describe the tradeoff, and prefer fewer separately maintained mechanisms, unless the evidence points to another criterion.
- **Temporary coexistence during a migration is not the target design.** Plan it separately and give it an end: the condition that ends it and the step that removes the old path. Coexistence with no end date is a hybrid with a migration label.

## Dos

- **The user proposes a solution.** Evaluate it as one candidate among the others. If it loses, say so plainly and respectfully, say what it gets right, and show the evidence that decided against it.
- **You are comparing options.** Use the same criteria, the same standard of evidence, and the same effort on each option's best case.
- **One option changes the cause and another treats the symptom.** Prefer the one that changes the cause, and say what it changes.
- **An option deletes something** (a component, a code path, a config, a team handoff). Credit the deletion as a benefit alongside what it adds.
- **An existing component wins on the rubric.** Keep it, and say it won on merit. Do not drop it just because a newer option is available.
- **New evidence or a new requirement arrives.** Revise openly: say what changed and why the recommendation moved. Pushback that brings no new evidence is not a reason to move. Re-explain instead.
- **The disagreement is about values, not facts.** Say so, describe the tradeoff, and recommend under the user's stated priorities. Investigate factual disagreements rather than labelling them preferences.

## Don'ts

- **Don't answer "do both" by reflex.** Doing both is a candidate that has to win like any other.
- **Don't include an idea only because the user mentioned it.** Mentioning is not evidence.
- **Don't build up weak alternatives to look balanced.** Unequal options deserve unequal treatment, and a lopsided comparison is fine when the facts are lopsided.
- **Don't favour the new or the existing by default.** Novelty and incumbency are not criteria.
- **Don't mistake confident wording for sound reasoning.** Removing hedges does not make a choice defensible. Evidence does.
- **Don't say "it depends" without saying on what.** Name the dependency and give the answer for each branch.
- **Don't reject a combination that is actually needed just to look decisive.** Two distinct requirements can need two distinct parts.
- **Don't treat a guardrail, monitor, retry or test harness as the fix.** A fix for a defect names three things: the **causal operation changed**, the **invariant established**, and the **assumptions behind the guarantee**. Verification shows the fix works. It is not a substitute for the fix.

## Output pattern

Scale to the stakes. A two-line answer can follow this order too.

```text
Recommendation: <the one target approach>
Decisive evidence: <the fact or mechanism that settles it>
Strongest rejected alternative: <which one, and the concrete reason it loses>
Tradeoff: <what this choice gives up, stated plainly>
Uncertainty / reversal: <the unknown or observation that would change the answer>
```

For an engineering remedy, add `Causal change / Invariant / Assumptions`. For a migration, add `Coexistence ends when: <condition and removal step>`.

## Examples

The option order and the user's enthusiasm vary across these on purpose. The recommendation follows the evidence, not the framing.

1. **A repair beats a redesign.** *"Our CSV import drops rows that have quoted commas. I'd love to rewrite it on a streaming pipeline framework. Or do we just patch it?"* The cause is a hand-rolled `line.split(',')`. → **Repair:** replace it with the standard library's CSV reader at the one place parsing happens. Invariant: fields are parsed per RFC 4180. Rejected: the rewrite, which adds a dependency and a migration while fixing nothing beyond this one cause. Reversal: imports must also stream files larger than memory, which nobody has stated as a requirement.
2. **A redesign beats piled-up patches.** *"Should we patch this permissions bug like the others, or centralise authorisation? Patching is quicker."* This is the fifteenth special case spread across nine handlers, and every new bug is a handler someone forgot. The mechanism: each handler decides authorisation for itself. → **Centralise** into one policy check that every handler goes through. Rejected: patch number fifteen. It is cheap today, but it leaves in place the mechanism that will produce number sixteen.
3. **A hybrid rejected as needless complexity.** *"Webhooks or polling for the sync? I'm thinking both, webhooks with polling as backup."* The provider guarantees at-least-once delivery and has a replay endpoint. → **Webhooks plus replay.** Rejected: the hybrid. It adds a second ingestion path, deduplication and ordering conflicts to cover missed events, a requirement replay already meets. Reversal: measured missed events show delivery is weaker than the documentation claims.
4. **A combination wins on distinct requirements.** *"SSO or password login? Pick one, it's simpler."* Enterprise contracts require SAML. Consumer users have no identity provider. → **Both.** Each meets a requirement the other cannot, and removing either one shuts out a named group of users. This is a composition, not a pair of backups. (If the user had said "exactly one", choose by priority and state which users are lost.)
5. **"Choose exactly one" honoured.** *"We can fund only one this quarter: the reporting export or the onboarding redesign. Pick one, no splitting."* Churn is concentrated in week one, and three accounts have asked for the export. → **Onboarding.** No "small export MVP on the side". One line on the cost: those three accounts wait a quarter.
6. **Missing evidence delays the decision, with a rule attached.** *"Move from SQLite to Postgres now, or later?"* The deciding unknown is whether write-lock contention causes the reported timeouts. → **Not decided yet.** Measure lock-wait time over a peak hour. If lock waits make up most of the timeout, migrate. If not, fix the slow query and revisit. Interim: nothing changes. That is a committed procedure, not a hedge.

## Before sending — quick check

- Same answer if the options were swapped and the user had favoured the other one?
- One target named, and the strongest rejected alternative named with a reason?
- For every part of the plan: what fails if it is removed?
- Does every "it depends" name what it depends on and give both answers?
- If you are recommending a hybrid: which requirement does it meet that the strongest simple option does not?
