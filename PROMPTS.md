# Widget prompts

Each widget below references the shared `Content to Analyze` input widget
(linked via PartyRock's `@` mention, not plain text).

## Main Claims

```
Extract the 1-3 main factual claims from @Content to Analyze.
Output as a simple bullet list only, no headers, no extra commentary.
Max 10 words per claim.
```

## Credibility Score

```
Analyze @Content to Analyze and respond in exactly this format, nothing else:

Score: a number from 0 to 100
Label: one word only, choose from Trustworthy, Questionable, Untrustworthy, or Fabricated
Reason: one sentence, under 15 words
```

## AI Writing Detection

```
Analyze @Content to Analyze for AI-generated writing patterns. Respond in exactly this format, nothing else:

Likelihood: one word only, choose from Low, Medium, or High
Why: one sentence, under 15 words
```

## Plain Language Explanation

```
In exactly 2 short sentences, explain why @Content to Analyze is or isn't trustworthy. Simple language, no jargon, no headers, no extra text.
```

## About This Tool

```
Paste any text, claim, article excerpt, or social media caption below to
check it for misinformation. This tool extracts the main claims, scores
credibility, flags AI-generated writing patterns, and explains its
reasoning in plain language.
```

## Notes on iterating these prompts

- Referencing the input widget requires typing `@` and selecting it from the
  dropdown — plain curly-brace or `@Widget Name` text does not connect to
  the widget's actual content.
- Square brackets (`[...]`) inside a prompt are also parsed as a widget
  reference by PartyRock, so format instructions use plain words
  ("a number from 0 to 100") instead of bracketed placeholders
  ("[0-100]") to avoid broken references.
