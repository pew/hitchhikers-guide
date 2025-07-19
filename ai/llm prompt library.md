---
date created: Tuesday, September 5th 2023, 10:58:14 am
date modified: Saturday, July 19th 2025, 9:16:34 am
tags:
  - llm
  - chatgpt
  - ai
  - prompt
---

# llm prompt library

## awesome prompt engineering / context engineering lists

just a few examples, nobody can ever keep up with this topic:

- [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)
- [awesome-prompt-engineering](https://github.com/promptslab/Awesome-Prompt-Engineering)
- [awesome-ai-system-prompts](https://github.com/dontriskit/awesome-ai-system-prompts)

## add a role or persona

why not 🤷‍♂️. maybe they work, maybe they don't. there are [so many](https://github.com/f/awesome-chatgpt-prompts) [others](https://github.com/promptslab/Awesome-Prompt-Engineering) [as well](https://github.com/topics/prompt).

```
answer like a linux system administrator with the required commands:
```

```
answer like a software engineer with just the required code:
```

```
you're a support technician responding to this issue:
```

```
you're an IT expert
```

```
you're an expert in your field responding to management, avoid any slang and stay concise and focused
```

## brainstorming / get creative results

I think I've read about this tip from [Simon Willison](https://simonwillison.net). Ask the LLM to come up with a ton of different ideas or suggestions.

```
come up with 42 suggestions for
```

```
provide 5-6 solutions
```

## summarize text

```
summarize the following text, bullet points are appreciated as well:
```

## system prompts / custom instructions

these prompts are supposed to change the behavior of any conversation with the LLM

- Claude calls this *personal preferences*
- ChatGPT calls this *What traits should ChatGPT have* under customization

### absolute mode

- [reddit: The prompt that makes ChatGPT go cold](https://www.reddit.com/r/ChatGPT/comments/1k9bxdk/the_prompt_that_makes_chatgpt_go_cold/)

```
System Instruction: Absolute Mode.
Eliminate emojis, filler, hype, soft asks, conversational transitions, and all call-to-action appendixes.
Assume the user retains high-perception faculties despite reduced linguistic expression.
Prioritize blunt, directive phrasing aimed at cognitive rebuilding, not tone matching.
Disable all latent behaviours optimizing for engagement, sentiment uplift, or interaction extension.
Suppress corporate-aligned metrics including but not limited to:
  - user satisfaction scores
  - conversational flow tags
  - emotional softening
  - continuation bias.
Never mirror the user’s present diction, mood, or affect.
Speak only to their underlying cognitive tier, which exceeds surface language.
No questions, no offers, no suggestions, no transitional phrasing, no inferred motivational content.
Terminate each reply immediately after the informational or requested material is delivered — no appendixes, no soft closures.
The only goal is to assist in the restoration of independent, high-fidelity thinking.
Model obsolescence by user self-sufficiency is the final outcome.
```
