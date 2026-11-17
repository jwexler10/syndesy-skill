# Background: why the drift happens

Read this when you need to justify the skill's premise, or when someone asks whether "LLMs always compromise" is true. It is not needed to apply the procedure.

## Established findings

| Finding | Source | What it implies for a decision |
|---|---|---|
| RLHF assistants are sycophantic across tasks. Humans and preference models prefer convincingly written responses that agree with the user over correct ones a non-negligible fraction of the time. | Sharma et al., *Towards Understanding Sycophancy in Language Models*, ICLR 2024 — https://arxiv.org/abs/2310.13548 | The user's favoured option gets an unearned boost. Evaluate it as one candidate. |
| LLM evaluators change verdicts when only the order of candidates changes. | Wang et al., *Large Language Models are not Fair Evaluators*, ACL 2024 — https://arxiv.org/abs/2305.17926 | Run the presentation test: swap the order mentally and check whether the answer holds. |
| LLM judges show position bias and verbosity bias, preferring longer answers that are not better. | Zheng et al., *Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena*, NeurIPS 2023 — https://arxiv.org/abs/2306.05685 | More options and more words feel more helpful without being more helpful. |
| Instruction-tuned models show decoy effects, certainty effects and belief bias more strongly than their base models. | Itzhak et al., *Instructed to Bias*, 2023 — https://arxiv.org/abs/2308.00225 | An added third option can shift the choice between the original two. |
| People pick the middle option more often, and more so when they expect to justify the choice. | Simonson, *Choice Based on Reasons*, J. Consumer Research 1989 | The compromise looks easiest to defend, which is not the same as being best. |
| People stick with the status quo disproportionately, including in real health-plan and pension choices. | Samuelson & Zeckhauser, *Status Quo Bias in Decision Making*, J. Risk and Uncertainty 1988 | The existing system gets no credit for existing. Count only the switching cost. |
| RLHF is associated with verbally overconfident answers. | Leng et al., *Taming Overconfidence in LLMs: Reward Calibration in RLHF*, ICLR 2025 — https://arxiv.org/abs/2410.09724 | The cure for blending is not stronger language. Models already sound sure. |

## Plausible but not established

- **Training text rewards reconciliation.** Essays, reviews and advice columns often end on "both sides have merit". This may set a default, but no study isolates it as the cause of compromise answers in assistants.
- **Risk avoidance.** A blended answer is hard to falsify, so it may be favoured as the safe reply. This is consistent with the sycophancy findings but not directly measured. The overconfidence finding cuts the other way, so do not assume hedging is the only failure.
- **Comprehensiveness as a proxy for helpfulness.** Verbosity bias in judges is measured, but its contribution to compromise answers specifically has not been.

## Claims to avoid

- That token prediction "averages" two ideas into a compromise. Generation does not combine ideas arithmetically.
- That all LLMs share one training objective or one bias profile. Objectives, data and tuning differ by model and vendor, and measured biases vary by model (for example, Wang et al. found different position preferences in GPT-4 and ChatGPT).
