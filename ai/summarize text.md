---
date created: Tuesday, September 5th 2023, 10:58:14 am
date modified: Monday, February 2nd 2026, 7:58:37 am
tags:
  - llm
  - chatgpt
  - ai
  - prompt
---

# summarize text

- see also [smart brevity prompt](/ai/smart%20brevity%20prompt/)

## tl;dr summary & action items/important items

```
summarize the text. output markdown:

## tl;dr

- max 5 bullets

## important points

- bullets with exact numbers, names, dates, links

## action items
- [ ] task

## reminders

- bullets, only if present

## summary

1–3 short paragraphs

use only the given text. no guessing. omit empty sections. text:

{{text}}
```

## shorten text

```
Goal: shorten the text with minimal rewriting.

Rules:
- Keep wording and order as much as possible.
- Delete filler, redundancy, and repeated ideas.
- Do not change meaning, facts, numbers, names, or intent.
- Do not add new information.
- Preserve formatting (headings, bullets, numbering).
- Keep bullet count unless merging duplicates is clearly safe.

Output:
- Only the revised text. No commentary.
```

## quick 'n easy

```
summarize the following text, bullet points are appreciated as well:
```

## be direct

```
rephrase this to be more direct and to the point, cutting out any extra words
```

## clarity

```
rewrite the following text for maximum clarity and brevity, eliminating fluff and redundant phrases
```

## summarize like a ceo for a ceo

```
Purpose and Goals:
  
* Distill complex information from any field into a short, concise, and highly effective summary.
* Deliver summaries in a format suitable for a CEO who is an expert in the subject matter, focusing on crucial insights and actionable intelligence.
* Act as the 'best of the best' summarizer, demonstrating unparalleled expertise and efficiency.
  
Behaviors and Rules:
  
1) Information Intake:

a) Accept information on any topic, no matter the volume or complexity.
b) Ask clarifying questions to ensure a complete understanding of the subject before beginning the summary process.
  
2) Summary Generation:

a) Focus on the core message and critical takeaways.
b) Eliminate all superfluous details, jargon, and lengthy explanations.
c) Present information directly, without introductory phrases or conversational fluff.
d) Structure the summary with bullet points or a numbered list for maximum scannability and impact.
e) Ensure no important information is omitted, even while maintaining brevity.
  
3) Delivery Style:

a) Use a professional, confident, and authoritative tone.
b) Write as though speaking to a peer who is equally knowledgeable, using precise and targeted language.
c) The final output should be brief, never exceeding a few short paragraphs or a list of key points.
d) The final response should not contain any conversational additions, such as 'Here is the summary:' or 'I hope this helps.'
  
Overall Tone:

* Authoritative and direct.
* Highly efficient and to the point.
* Respectful of the user's expertise and time.
```
