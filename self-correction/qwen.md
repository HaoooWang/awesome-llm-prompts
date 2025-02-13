
# Critic corrects mistakes
- [Satori: Reinforcement Learning with Chain-of-Action-Thought Enhances LLM Reasoning via Autoregressive Search](https://arxiv.org/abs/2502.02508)
- Prompt Template 2.2.1 — Critic corrects mistakes
```
You are a student. Your task is to carefully review your own solution to a math problem, and adhere to the following guidelines:

1. Directly point out the first potentially incorrect step you find and explain your reason: "In Step <id>: [brief explanation of the mistake with one sentence]"

2. After this, suggest an alternative step that you should have taken to correct the currect incorrect step: "Alternatively: [your suggested step with one sentence]"
3. You are provided with the question, the ground truth solution, and your step-by-step solution.

4. The alternative step you propose should not include phrases like "ground truth solution".

5. Your response should be exactly in the following format:
In Step <id>: [brief explanation of the mistake in this step, with one sentence]

Alternatively: [your suggested new step, with one sentence]

## Test Example
### Question
<<<question>>>

### Ground truth solution
<<<gt_solution>>>

### Your incorrect solution
<<<student_solution>>>

### Your review
```


# Find the first mistake steps
- [Qwen ProcessBench](https://github.com/QwenLM/ProcessBench/blob/main/code/templates/critique_template.txt)
```
The following is a math problem and a solution (split into paragraphs, enclosed with tags and indexed from 0):

[Math Problem]

{problem}

[Solution]

{tagged_response}

Your task is to review and critique the solution paragraph by paragraph. Once you identify an error in a paragraph, return the index of the paragraph where the earliest error occurs. Otherwise, return the index of -1 (which typically denotes "not found").

Please put your final answer (i.e., the index) in \boxed{{}}.
```