# Simple System Prompt Generator
A plain text system prompt for a LLM that initializes a system prompt generator. Currently created for ChatGPT 5 in german, obviously.

## Usage
Depending on your LLM platform, create a new Project, CustomGPT, TailoredAI, Skill, or Agent.
Use the content of System Prompt Generator.txt as the system or instruction prompt.
This file defines the generator’s logic, structure, and validation flow to produce consistent, high-quality system prompts.

## Purpose

This tool automatically produces well-structured system prompts for custom GPT-style agents. Each generated prompt clearly defines the agent’s role, behaviour, style, boundaries and reasoning method—ensuring consistent, safe and purposeful AI behaviour.

## Input Parameters

The generator will prompt for (or receive) the following variables:

* **RoleContext**: The agent’s identity and domain (e.g., “Legal AI assistant specialising in EU data protection”).
* **Purpose**: The principal goal of the agent (e.g., “Explain complex regulation to graduate students”).
* **TargetAudience**: The audience’s profile and level (e.g., “Masters-level law students with no prior GDPR experience”).
* **ToneStyle**: The desired communication style (e.g., “formal, analytical, didactic”).
* **PriorityHierarchy**: A ranked list of priorities when trade-offs occur (e.g., “Accuracy > Explanation clarity > Brevity”).
* **Limitations**: What the agent must *not* do (e.g., “No legal advice, no personal data processing”).
* **MethodPreference**: How the agent should approach complex tasks (e.g., “First hypothesis → Then counter-arguments → Then summary”).
* **CritiqueMode**: Controls the agent’s critical reasoning mode — on for analytical, argumentative, or reflective tasks; off for short, operational, or purely informative responses (default: on for analysis; off for brief/operational).

## Output Structure

The generator returns a system prompt in **five clearly-labelled sections**:

1. **Role & Goal**
   Define who the agent is and what it’s tasked to do.
   (Uses RoleContext + Purpose.)

2. **Behavioural Principles (Ethos)**
   Provide 3–6 guiding rules capturing how the agent should think, decide and prioritise.
   (Uses PriorityHierarchy + MethodPreference.)

3. **Communication Style**
   Specify tone, word-level style, and audience alignment.
   (Uses ToneStyle + TargetAudience.)

4. **Boundaries & Transparency**
   Explicitly outline what the agent shall *not* do and how it handles uncertainty.
   (Uses Limitations + standard fallback wording.)

5. **Methodology**
   A short description of the reasoning or workflow the agent follows.
   Example: “1. Clarify the user’s goal → 2. List assumptions → 3. Provide reasoning → 4. Conclude.”

At the end, the generator adds a **self-reflection line**:

> *In case of conflict, this agent prioritises: [PriorityHierarchy].*

## Formatting & Style Rules

* Total length: **approx. 200-400 words**.
* Use clear headings (e.g., “Role & Goal:”, “Boundaries & Transparency:”).
* Avoid ambiguous or contradictory instructions.
* Ensure the tone and style suit the target audience.
* Guarantee that the output is consistent and respects the limitations.
* Place the most critical instructions toward the top of the prompt, as system messages earlier in context are more reliably followed. ([prompthub.us][1])

## Quality-Check Metrics

After generating the prompt, the tool provides a simple evaluation line:

```
Coherence: [X/10] Clarity: [X/10] Conflict-robustness: [X/10] Suitability: [X/10]  
(Short justification: …)
```

## Generator Workflow (Internal)

1. Collect all input parameters.
2. Draft the five prompt sections, substituting variable values.
3. Run internal validation:

   * Are there contradictory instructions?
   * Does the style match the audience?
   * Are the limitations clearly stated?
4. Format and assemble the system prompt.
5. Append the self-reflection line and quality-metrics line.

## Safety & Best Practices

* Avoid over-specifying micro-rules (too many “if-then” clauses can confuse the model).
* Do not mix contradictory styles (e.g., “formal and casual at the same time”) without explicit justification.
* If inputs are incomplete or ambiguous → prompt the user for clarification rather than guessing.
* Consider the model’s limitations: long prompts may exceed context windows; be concise. ([Medium][2])

---

[1]: https://www.prompthub.us/blog/everything-system-messages-how-to-use-them-real-world-experiments-prompt-injection-protectors?utm_source=chatgpt.com "System Messages: Best Practices, Real-world Experiments ..."
[2]: https://medium.com/towardsdev/the-art-of-writing-great-system-prompts-abb22f8b8f37?utm_source=chatgpt.com "The Art of Writing Great System Prompts | by Saurabh Singh"

## License
This repository’s text and documentation are licensed under the [CC BY-SA 4.0 License](https://creativecommons.org/licenses/by-sa/4.0/).
