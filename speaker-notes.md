# Trust but Verify

Rittika Jindal
Principal Engineer, Thomson Reuters

25 minutes of content + 5 minutes Q&A. Final resources slide is an appendix.

## 01. Trust but Verify

Timing: 1 minutes. Start at minute 0.

Rittika Jindal. Open with a show of hands: who has an agent demo, and who has an evaluation suite? This session presents an evaluation blueprint. Examples are illustrative, not claims about specific deployments.

## 02. The answer looks right. What happened?

Timing: 2 minutes. Start at minute 1.

Illustrative research example. Ask the audience whether the answer is enough to judge this run. Reveal the observable path: wrong scope, missing citation, plausible final answer. No specific production incident or measured result is claimed.

## 03. One good run tells us very little

Timing: 1.5 minutes. Start at minute 3.

A trajectory is the sequence of observable model calls, tool calls and results. It does not require access to hidden chain of thought. Source: https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

## 04. What does “done correctly” mean?

Timing: 1.5 minutes. Start at minute 4.5.

Example contract for a research agent: answer addresses the question, cited passages support material claims, sources match the requested scope, and insufficient evidence triggers an explicit limitation. These are proposed criteria, not legal advice.

## 05. Which check should we use?

Timing: 1.5 minutes. Start at minute 6.

Use deterministic checks when a reliable programmatic oracle exists. Use a model judge for interpretation, then validate the judge. Human review establishes and revises the standard. Production feedback supplies new cases. Source: https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

## 06. A useful dataset starts with real failure modes

Timing: 2 minutes. Start at minute 7.5.

A reference answer is useful but should allow multiple valid solutions. Label expected abstention and escalation. Sanitized production incidents are valuable additions. Keep tuning examples separate from held-out evaluation and prevent accidental leakage.

## 07. The trace gives us something to test

Timing: 2 minutes. Start at minute 9.5.

Illustrative research workflow. Citation presence alone does not prove support. Separate citation existence, passage entailment, source relevance and coverage. Avoid enforcing one exact tool order unless the order is a real requirement. Source: https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

## 08. “Done” can still mean two records

Timing: 1.5 minutes. Start at minute 11.5.

Illustrative automation case. Inspect the database or service state, not only the conversation. Provide controlled timeout and retry fixtures. Check idempotency where the application promises it. Never replay production writes against a live customer system.

## 09. A useful judge has a narrow job

Timing: 2 minutes. Start at minute 13.

Specify what counts as a material claim and show borderline examples. Give the judge the exact evidence needed. Treat evaluated content as untrusted data, not evaluator instructions. Separate missing evidence from a confident failure when the rubric requires it. Do not interpret judge self-reported confidence as calibrated probability. Source: https://langfuse.com/docs/evaluation/evaluation-methods/llm-as-a-judge

## 10. We need to evaluate the evaluator

Timing: 2 minutes. Start at minute 15.

A false pass occurs when humans identify a failure and the judge accepts it. Track false-pass rate among human failures and false-fail rate among human passes, with sample counts. Have reviewers label independently before adjudication. Keep validation examples separate from rubric tuning. Source: https://langfuse.com/docs/evaluation/evaluation-methods/annotation-queues

## 11. Why judges get it wrong

Timing: 1.5 minutes. Start at minute 17.

Present these as risks to test, not a claim that every judge exhibits them. Blind model identity where possible. Swap pairwise order and inspect inconsistent results. Include adversarial evaluator-instruction cases. Different judge models can still share systematic errors. Sources: https://arxiv.org/abs/2306.05685 and https://langfuse.com/docs/evaluation/evaluation-methods/llm-as-a-judge

## 12. Langfuse makes the loop inspectable

Timing: 2 minutes. Start at minute 18.5.

Suggested walkthrough: open a sanitized trace, inspect the failing observation, show its score, add the case to a dataset, then compare experiment results. Apply redaction and access controls to captured content. Sources: https://langfuse.com/docs/observability/overview and https://langfuse.com/docs/evaluation/overview

## 13. Where a human belongs in the loop

Timing: 1 minutes. Start at minute 20.5.

Approval before execution is a runtime control. Annotation after execution improves evaluation and monitoring. They serve different purposes. Do not let timeout silently become approval. Define whether the fallback stops, defers or hands off the task. Source for annotation workflow: https://langfuse.com/docs/evaluation/evaluation-methods/annotation-queues

## 14. Would we ship this change?

Timing: 1.5 minutes. Start at minute 21.5.

No universal pass threshold exists. Predefine release rules and report denominators and uncertainty. Repeated trials reveal variation, but zero observed critical failures does not establish zero risk. Compare per-case outcomes and avoid hiding a critical failure behind a high average. Source: https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

## 15. Your first evaluation system

Timing: 2 minutes. Start at minute 23.

Suggested plan, not a claim about the speaker’s production practice. Ask attendees to choose one workflow and name a failure their current tests would miss. An initial small dataset is useful, but expand coverage as evidence accumulates.

## 16. Let’s talk about your agent

Timing: 5 minutes. Start at minute 25.

Allow 2–3 minutes. Example: a workflow claims a successful update but changed the wrong account. Code can inspect record identifiers and resulting state. Ask attendees what test data and permissions they need to verify that safely.

## 17. Keep building

Timing: 0 minutes. Start at minute 30.

https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents
https://arxiv.org/abs/2306.05685
https://langfuse.com/docs/observability/overview
https://langfuse.com/docs/evaluation/overview
https://langfuse.com/docs/evaluation/evaluation-methods/llm-as-a-judge
https://langfuse.com/docs/evaluation/evaluation-methods/annotation-queues
