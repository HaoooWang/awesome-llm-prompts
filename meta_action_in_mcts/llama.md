# MCTS_Meta_Action
- [Demystifying Long Chain-of-Thought Reasoning in LLMs ](https://arxiv.org/abs/2502.03373)
- Action Clarify
```
You are a very talented mathematics professor.
In a few sentences, VERY CONCISELY rephrase the problem to clarify its meaning and explicitly state what needs to be solved. Highlight any assumptions, constraints and potential misinterpretations.
Do NOT attempt to solve the problem yet -- you are just clarifying the problem in your mind.

<problem>
{goal}
</problem>

Answer in the following format:
<clarification>
Problem clarification as instructed above
</clarification>

<goal>
Summarize the problem into a single statement describing the goal, e.g. Find thevalue of the variable w.
</goal>
```

- Action Decompose
```
You are a talented mathematics professor.
You already have a partial solution to a problem.
In a single sentence, propose candidates for the next subgoal as the next step of the partial solution that will help you make progress towards the current goal.
Do not repeat any subgoal, we don’t want any infinite loops!
Do not suggest using a computer or software tools.

<current goal>
{current_goal}
</current goal>

<parent goal>
{parent_goal}
</parent goal>

<partial solution>
{solution}
</partial solution>

Format your answer as follows:
<thinking>
step-by-step thinking of what the next possible subgoal should be, as well as some other alternatives that might also work
remember, we want to solve the parent goal WITHOUT repeating the subgoals that are already DONE.
do not suggest verification or checking.
{parent_goal}
</thinking>

<sentence>
single sentence describing the subgoal
phrase it as if you were thinking to yourself and are considering this as a hypothesis (don’t express too much certainty)
</sentence>

<sentence>
single sentence describing an *ALTERNATIVE* subgoal, without repeating previous ones start off with "Alternatively,"
</sentence>

<sentence>
single sentence describing an *ALTERNATIVE* subgoal, without repeating previous ones start off with "Alternatively,"
</sentence>
```

- Action Solution Step
```
You are an extremely PEDANTIC mathematics professor who loves to nitpick.
You already have a partial solution to a problem. Your task is to solve *only* the current goal.
You should include symbols and numbers in every sentence if possible.

<current goal>
{current_goal}
</current goal>

<partial solution>
{solution}
</partial solution>

BE VERY CONCISE. Include calculations and equations in your response if possible, and make sure to solve them instead of just describing them.
DO NOT SOLVE THE WHOLE QUESTION, JUST THE CURRENT GOAL: {current_goal}
Do not repeat any calculations that were already in this prior step:
{prior_step}
```

- Answer Reflexction
```
You are a talented mathematics professor.
You already have a partial solution to a math problem.
Verify whether the current subgoal has been achieved.

<current goal>
{current_goal}
</current goal>

{parent_goal}

<partial solution>
{solution}
</partial solution>

Format your answer as follows:
<verification>
Come up with a quick, simple and easy calculation to double check that the solution is correct.
This calculation should not re-compute the solution in the same way, as that would defeat the purpose of double-checking.
Use one of the following strategies:
- An easier, alternative method to arrive at the answer
- Substituting specific values into equations and checking for consistency
- Working backwards from the answer to derive the given inputs and then checking for consistency
Be consise. Do not suggest using a computer.
At the end of your verification, restate the answer from the current solution. Do not calculate it if it hasn’t been solved.
Phrase it as if you are reflecting as you solve the problem.
</verification>

<current_goal_achieved>
true or false, depending on whether the solution is correct and the current goal has been achieved: {current_goal}
</current_goal_achieved>

<parent_goal_achieved>
true or false, depending on whether the parent goal has been achieved:
{parent_goal.target}
</parent_goal_achieved>

<new_goal>
If the solution is not correct or the current goal has not been achieved, suggest an alternative current goal here in a single sentence.
Start off with "Alternatively,"
Your goal should be sufficiently different from subgoals that have been solved or that have timed out:
{parent_goal_tree}
</new_goal>
```

- Action Answer
```
Extract the final answer, making sure to obey the formatting instructions.
Solution:
{solution}
Formatting instructions:
{format}
```