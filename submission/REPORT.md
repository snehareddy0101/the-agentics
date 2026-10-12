# CrewAI Build Report

**Name:** Sneha Latha Astum
**Topic I used:** How small teams can use AI agents in data science

## 1. What I Changed

## 1. What I Changed

For this assignment, I used the CrewAI starter kit, which contains three agents: a Research Analyst, a Technical Writer, and an Editor. I selected the topic "How small teams can use AI agents in data science" to understand how multiple AI agents collaborate to complete a research and writing task.

I made one meaningful modification in the `main.py` file, specifically in the `editing_task` section. The original Editor task focused on improving the explanation and identifying claims that required sources. I expanded the task description to emphasize clarity, grammar, readability, and preserving the original meaning. I also instructed the Editor to mark unsupported factual claims with `[source needed]` and avoid inventing statistics, citations, or evidence.

I chose this modification because the original generated explanation contained numerical claims without verifiable supporting references. My goal was to make the Editor more cautious about factual accuracy and evaluate whether clearer instructions would improve the final output.

## 2. How CrewAI Works

CrewAI is a framework that allows multiple AI agents to collaborate on tasks using clearly defined roles and responsibilities. The three main components I worked with were Agents, Tasks, and Crew.

An **Agent** represents a specialist with a particular role, goal, and backstory. In my project, the Research Analyst gathers information, the Technical Writer prepares an explanation, and the Editor reviews the written content. These roles help the language model understand what each agent is expected to accomplish.

A **Task** defines the work assigned to an agent. Each task includes a description and an `expected_output` that explains what the result should look like. In my workflow, the Research Analyst produces a research brief containing five key facts and two open questions. The Technical Writer uses that information to prepare an approximately 250-word explainer. The Editor then improves the writing and identifies unsupported claims.

A **Crew** connects the agents and tasks into a workflow. My project uses `Process.sequential`, meaning the tasks run in a specific order, and each task can use information produced by previous tasks.

The agents use a language model accessed through Groq using CrewAI's `LLM` configuration. My modification worked by changing the instructions provided to the Editor without changing the number of agents or the execution order. However, the results showed that instructions alone do not guarantee accurate fact-checking.

## 3. Evidence

I ran the original workflow and saved its output in `run1_original.txt` and `explainer_run1.md`.

The original explainer included numerical claims about prototype development, experiment performance, cloud spending, onboarding, and fairness improvements. Several of these claims lacked verifiable references, while the final statement included a `[source needed]` marker.

After modifying the Editor task, I ran the workflow again and saved the results in `run2_changed.txt` and `explainer_run2.md`.

The modified output discussed code generation, model development, cloud costs, reproducibility, and domain-specific agents. However, it still included unsupported numerical claims, including 70% pipeline success, a 22% improvement in model-quality parity, and a 15% reduction in cloud costs.

Although the modified instructions emphasized evidence checking, the Editor did not consistently flag these statistics. This demonstrated that stronger prompts alone cannot guarantee factual accuracy.

The two outputs also differed in content, so the differences cannot be attributed entirely to the Editor instruction change. Language-model variability and changes in earlier agents' outputs may have contributed.

## 4. Choosing a Framework

I would choose CrewAI for projects where multiple AI agents need to collaborate on a task with clearly defined responsibilities. In this assignment, CrewAI allowed me to organize the workflow into three specialized roles: Research Analyst, Technical Writer, and Editor. Each agent completed a specific task, and its output contributed to the next stage. This structure made the workflow easier to understand and helped me identify which part of the process needed improvement.

For example, in a data science project, CrewAI could support a research workflow in which one agent collects background information, another prepares a technical summary, and a third reviews the results. However, human verification would still be necessary, especially when the output contains factual or numerical claims.

Compared with CrewAI, **LangGraph** provides more explicit control over the workflow using nodes, edges, and shared state. Based on the class demonstration, LangGraph also supports human approval checkpoints before certain actions are executed. This would be useful when a data science workflow involves sensitive information or important decisions.

CrewAI would be easier for me to use when building a straightforward team of specialized agents. LangGraph would be more suitable when I need complex branching, repeated checks, or human approval before continuing.## 4. Choosing a Framework

I would choose CrewAI for projects where multiple AI agents need to collaborate on a task with clearly defined responsibilities. In this assignment, CrewAI allowed me to organize the workflow into three specialized roles: Research Analyst, Technical Writer, and Editor. Each agent completed a specific task, and its output contributed to the next stage. This structure made the workflow easier to understand and helped me identify which part of the process needed improvement.

For example, in a data science project, CrewAI could support a research workflow in which one agent collects background information, another prepares a technical summary, and a third reviews the results. However, human verification would still be necessary, especially when the output contains factual or numerical claims.

Compared with CrewAI, **LangGraph** provides more explicit control over the workflow using nodes, edges, and shared state. Based on the class demonstration, LangGraph also supports human approval checkpoints before certain actions are executed. This would be useful when a data science workflow involves sensitive information or important decisions.

CrewAI would be easier for me to use when building a straightforward team of specialized agents. LangGraph would be more suitable when I need complex branching, repeated checks, or human approval before continuing.

## 5. Verification and AI Use

I verified the environment using `uv run python check_setup.py`, which returned the configured model, the response `ready`, and the message `CrewAI kit OK`.

I executed the original and modified workflows and retained their terminal logs and generated explainers as evidence.

I reviewed the generated content and identified unsupported statistics and references. I did not independently verify the numerical claims in either explainer, so they should not be treated as established facts.

I used AI assistance to understand the starter code, improve the Editor task instructions, troubleshoot execution errors, and organize this report. I remained responsible for checking the code, running the workflows, reviewing the outputs, and documenting the limitations.

## Conclusion

This exercise helped me understand how CrewAI coordinates specialized agents in a sequential workflow. Modifying the Editor task demonstrated that clearer instructions can establish stronger expectations, but they do not guarantee reliable fact-checking. For production use, I would add source retrieval, citation validation, and human review before publishing factual claims.