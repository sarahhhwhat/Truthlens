# TruthLens

A misinformation and content-credibility checker, built for **First Commit**
(Bharat Builds Tour) — Build It track, running entirely on **Amazon Bedrock**
via **PartyRock**.

**Live app:** https://partyrock.aws/u/sarahhhwhat/cgwLc5Ww-/Truthlens

## What it does

Paste any text — a claim, an article excerpt, a social media caption — and
TruthLens returns:

- **Credibility Score** (0–100) with a one-line reason and a label
  (Trustworthy / Questionable / Untrustworthy / Fabricated)
- **Main Claims** — the 1–3 factual claims extracted from the text
- **AI Writing Detection** — a likelihood estimate (Low/Medium/High) that the
  text shows AI-generated writing patterns
- **Plain Language Explanation** — a short, jargon-free explanation of the
  reasoning, not just a verdict

## Example results

| Input | Score | Label |
|---|---|---|
| "Scientists confirm that drinking coffee cures COVID instantly." | 5 | Fabricated |
| "The World Health Organization declared COVID-19 a pandemic on March 11, 2020." | 95 | Trustworthy |
| "Vitamin C boosts your immune system and can help prevent colds." | — | Partially true (nuanced explanation, not a binary score) |
| "I think remote work is better than office work." | — | Flagged as opinion, not a factual claim |

That last row matters as much as the scores — the tool distinguishes between
false claims, verified facts, partially-true claims, and unverifiable
opinions, instead of forcing everything onto a single true/false scale.

## How it's built

TruthLens is built entirely in **PartyRock**, AWS's no-code AI app builder,
which runs on **Amazon Bedrock** underneath. Each output is its own widget,
driven by a tightly-scoped prompt referencing the shared `Content to Analyze`
input:

- `Main Claims` — extracts 1–3 factual claims as a short bullet list
- `Credibility Score` — returns a score, a one-word label, and a one-line reason
- `AI Writing Detection` — returns a likelihood and a one-line reason
- `Plain Language Explanation` — a 2-sentence explanation in plain language

See [`PROMPTS.md`](./PROMPTS.md) for the exact prompt text used in each widget.

No separate backend, server, or infrastructure — PartyRock handles the
orchestration and the Bedrock calls.

## Screenshots

Widget setup and build process — see [`/screenshots`](./screenshots).

## Scope and known limitations

Built and scoped for a 4-day hackathon window:

- **Text input only.** PartyRock doesn't fetch live URLs (it treats a pasted
  link as plain text rather than reading the page), so URL support was
  dropped in favor of a single, honest "paste text" input.
- **No image/screenshot upload.** PartyRock's widgets support document
  formats (PDF, TXT, DOCX, HTML, CSV) but not image OCR, so screenshot and
  reel support isn't in this version.

## What's next

- Live URL fetching (would need a custom Lambda + Bedrock pipeline, moving
  beyond what PartyRock alone can do)
- Screenshot/OCR support for social media posts and reels (via Amazon Textract)
- A proper AWS-deployed version (Ship It track) — Lambda, API Gateway,
  DynamoDB, and Bedrock directly, for a live public URL

## AI tools used

Built with PartyRock (Amazon Bedrock / Claude under the hood). Planning,
prompt drafting, and this write-up were done with help from Claude.

## Built for

**First Commit** — Event 01 of the Bharat Builds Tour, Sept 17–20, 2026.
