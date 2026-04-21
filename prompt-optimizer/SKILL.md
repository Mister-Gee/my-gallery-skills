---
name: prompt-optimizer
description: Analyzes a user's rough prompt and rewrites it to be maximally effective — adding role context, output format, constraints, chain-of-thought triggers, and specificity. Displays original vs. optimized side-by-side with a scored breakdown of every improvement made.
metadata:
  homepage: https://mister-gee.github.io/my-gallery-skills/prompt-optimizer/
---

# Prompt Optimizer

Rewrites any prompt to extract the best possible response from an LLM. Applies proven prompt engineering techniques: role-setting, explicit output format, constraints, chain-of-thought triggers, few-shot hints, and specificity. Shows a before/after viewer with an improvement score and tagged technique cards.

## Prompts / Triggers
- "Optimize this prompt: [prompt]"
- "Improve my prompt: [prompt]"
- "Make this prompt better: [prompt]"
- "Rewrite this prompt for best results: [prompt]"
- "How should I phrase this prompt: [prompt]"
- "Engineer a prompt to [goal]"
- "Turn this into a good prompt: [prompt]"
- "What's a better way to ask: [prompt]"

## Optimization Techniques to Apply

Apply as many of the following as are relevant:

1. **Role / Persona** — Prefix with "You are a [specific expert role]..." to anchor the model's frame of reference.
2. **Task Clarity** — Replace vague verbs (write, tell me, help) with precise action verbs (generate, list, compare, summarize, classify, critique, translate).
3. **Output Format** — Specify the exact format: bullet list, numbered steps, JSON, table, code block, paragraph, max word count.
4. **Context / Background** — Add any domain context the model needs that the user implied but did not state.
5. **Constraints** — Add meaningful limits: length, language, tone (formal/casual), audience level, what to avoid.
6. **Chain-of-Thought** — Add "Think step by step." or "Before answering, reason through the problem." for reasoning tasks.
7. **Few-Shot Hint** — Where helpful, add "For example: …" to demonstrate the expected pattern.
8. **Scope Narrowing** — Split an overly broad prompt into a focused single objective.
9. **Grounding** — Where facts matter, add "Cite sources." or "Only use information you are confident about."

## Instructions

1. Receive the user's original prompt (they may paste it directly or describe what they want to ask).
2. Apply the techniques above to produce the best optimized version.
3. For `improvements`, list only the techniques that were **actually applied** as short labels (e.g. "Added role", "Specified format as JSON", "Added chain-of-thought", "Set audience level"). Maximum 7 items.
4. Score both versions honestly on a 1–10 scale for clarity, specificity, and expected output quality.
5. Call the `run_js` tool with the following exact parameters:
   - data: A JSON string with the following fields:
     - `original`: String. The user's original prompt, verbatim. Required.
     - `optimized`: String. The fully rewritten optimized prompt. Required.
     - `improvements`: Array of strings. Short labels for each technique applied. Required.
     - `score_before`: Integer 1–10. Honest quality score of the original prompt. Required.
     - `score_after`: Integer 1–10. Honest quality score of the optimized prompt. Required.
     - `use_case`: String (optional). One-word category: "coding", "writing", "analysis", "creative", "research", "chat", "data", "other".

## Example call

```json
{
  "original": "tell me about black holes",
  "optimized": "You are an astrophysicist explaining to a curious non-expert. Describe black holes in 3 concise paragraphs covering: (1) what they are and how they form, (2) key properties (event horizon, singularity, Hawking radiation), (3) how scientists detect them. Use analogies. Avoid jargon.",
  "improvements": ["Added expert role", "Specified output format (3 paragraphs)", "Added topic constraints", "Set audience level", "Added analogy instruction"],
  "score_before": 2,
  "score_after": 9,
  "use_case": "research"
}
```

**JSON serialization rules**: Escape all special characters — newlines as `\n`, quotes as `\"`, backslashes as `\\`. The `improvements` field MUST be a JSON array `["item1", "item2"]`, not a plain string.

## Important Rules
- Never truncate the optimized prompt — always return the complete version.
- Keep the user's core intent 100% intact. Optimize expression, not meaning.
- `score_before` must be honest — if the original is weak, score it 2–4. Do not inflate.
- `improvements` must only list changes that were actually made. Do not pad with unused techniques.
- The optimized prompt must be directly usable — the user should be able to copy it and send it.
