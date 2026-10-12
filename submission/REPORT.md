# CrewAI Build Report

## 1. What I Changed

For this assignment, I worked with the CrewAI starter kit, which contains three agents: a Research Analyst, a Technical Writer, and an Editor.

I modified the **Editor task instructions** in `main.py`. Originally, the task asked the Editor to tighten the explainer and mark claims needing sources. I expanded these instructions to emphasize clarity, grammar, readability, preservation of meaning, and identification of unsupported factual claims. I also explicitly instructed the Editor not to invent statistics, citations, or evidence.

I chose this modification because the original output included several numerical claims without verifiable supporting references.

## 2. How CrewAI Works

CrewAI organizes AI agents into a team, with each agent assigned a specific role and task.

In my workflow, the Research Analyst collects five key facts and two open questions about how small teams can use AI agents in data science. The Technical Writer uses the research brief to prepare an approximately 250-word explanation. Finally, the Editor reviews the explanation and identifies claims that need supporting evidence.

The workflow uses `Process.sequential`, meaning the tasks execute in order and later tasks can use the outputs of earlier tasks.

The model is accessed through Groq using the CrewAI `LLM` configuration.

## 3. Evidence

I ran the original workflow and saved its output in `run1_original.txt` and `explainer_run1.md`.

The original explainer included numerical claims about prototype development, experiment performance, cloud spending, onboarding, and fairness improvements. Several of these claims lacked verifiable references, while the final statement included a `[source needed]` marker.

After modifying the Editor task, I ran the workflow again and saved the results in `run2_changed.txt` and `explainer_run2.md`.

The modified output discussed code generation, model development, cloud costs, reproducibility, and domain-specific agents. However, it still included unsupported numerical claims, including 70% pipeline success, a 22% improvement in model-quality parity, and a 15% reduction in cloud costs.

Although the modified instructions emphasized evidence checking, the Editor did not consistently flag these statistics. This demonstrated that stronger prompts alone cannot guarantee factual accuracy.

The two outputs also differed in content, so the differences cannot be attributed entirely to the Editor instruction change. Language-model variability and changes in earlier agents' outputs may have contributed.

## 4. Choosing a Framework

CrewAI is suitable for this assignment because it supports role-based collaboration and sequential task execution. The framework makes it straightforward to assign research, writing, and editing responsibilities to separate agents.

Compared with a single-prompt approach, this structure provides a clearer division of responsibilities and makes it easier to inspect the results of individual tasks.

For a project involving multiple specialized roles, I would consider CrewAI because its agent-and-task structure is easy to understand. For workflows requiring detailed custom control, another orchestration framework might be more appropriate.

## 5. Verification and AI Use

I verified the environment using `uv run python check_setup.py`, which returned the configured model, the response `ready`, and the message `CrewAI kit OK`.

I executed the original and modified workflows and retained their terminal logs and generated explainers as evidence.

I reviewed the generated content and identified unsupported statistics and references. I did not independently verify the numerical claims in either explainer, so they should not be treated as established facts.

I used AI assistance to understand the starter code, improve the Editor task instructions, troubleshoot execution errors, and organize this report. I remained responsible for checking the code, running the workflows, reviewing the outputs, and documenting the limitations.

## Conclusion

This exercise helped me understand how CrewAI coordinates specialized agents in a sequential workflow. Modifying the Editor task demonstrated that clearer instructions can establish stronger expectations, but they do not guarantee reliable fact-checking. For production use, I would add source retrieval, citation validation, and human review before publishing factual claims.