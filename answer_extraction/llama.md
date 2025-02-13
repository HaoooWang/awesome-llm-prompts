

## Extract short-form answer from QA pairs in WebInstruct
- [Demystifying Long Chain-of-Thought Reasoning in LLMs](https://arxiv.org/abs/2502.03373)
- We use the Llama-3.1-8B-Instruct model to extract short-form answer from QA pairs in WebInstruct, with the following prompt template:
```
Problem: {Problem}

Solution: {Solution}

Based on the Problem and the Solution, extract a short final answer that is easy to check.
Provide the short final answer in the format of "The final answer is $$\boxed{...}$$"

- If the answer is a mathematical object, write it in LaTeX, e.g., "The final answeris $$\boxed{\frac{1}{2}}$$"
- If the answer is a boolean, write it as "True" or "False", e.g., "The final answeris $$\boxed{True}$$"
- If the Problem can’t be answered in a short form, respond with "" like "The finalanswer is $$\boxed{}$$"
```