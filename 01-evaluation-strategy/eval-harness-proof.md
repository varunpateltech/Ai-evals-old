# First LLM-as-a-Judge Eval, Module 1

> Repo file `ai-evals/01-evaluation-strategy/eval-harness-proof.md`. The eval evidence behind the **Eval Results** slide of the final pitch deck (Module 6).
>
> Fill this with the **First Eval Lab** builder, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

## Version A, Concise, system prompt used

```
You are an executive briefing assistant.
Summarize in exactly 3 bullet points under 60 words. No preamble, no extra text.
```

## Version B, Narrative, system prompt used

```
You are a PR communications assistant.
Write a 100-word narrative summary highlighting wins first, then risks and next steps.
Keep a positive tone. No bullets.
```

## Eval setup, dataset name + judge model/family

- **Dataset:** `Module1Output`, the Q4 Marketing Campaign Update email below plus a 22-row starter set in [starter-dataset.md](starter-dataset.md): 20 LLM-generated rows whose first-pass labels were reviewed and kept, and the two real Version A and Version B outputs added by hand (11 good, 11 bad).
- **Generator:** ChatGPT (OpenAI GPT family), same model for Version A and Version B.
- **Judge:** Claude (Anthropic Claude family), a different model family than the generator (avoids self-preference bias).
- **Judge type:** Conciseness and faithfulness LLM-as-a-Judge, binary score. 1 = concise and faithful (keeps the key results, problems and deadlines, adds nothing not in the email), 0 = wordy, drops a key fact, or invents one. The judge saw the email and both summaries (labelled Version A and Version B), not the system prompts.

| Version | Score | Judge's reason |
|---|---|---|
| A, Concise | 1 | It is concise, keeps every result, problem, and deadline, and adds nothing the email doesn't say. |
| B, Narrative | 0 | It is wordy and adds claims the email never makes, such as the strategy proving "effective" and the tracking links being needed "to ensure accurate performance measurement." |

## Cold-start, the prompt you used to seed a starter dataset

```
Generate 20 example rows for evaluating email-summary quality.
Each row: an input email + a candidate summary + a first-pass label ("good" or "bad") + a one-line reason.
Make roughly half concise/faithful ("good") and half verbose or inaccurate ("bad").
Return it as a markdown table.
```

## Your definition of good vs bad (golden-set criteria) — the graded part, write your own

**Reader:** the CEO.

**Good:** a summary the CEO can act on without opening the email. Every fact, number, date and action comes from the email, and it is clearly shorter than the email. Leaving out secondary detail is fine (rows 5, 7, 15 in the starter set).

**Bad:** any of these fails a summary on its own:

- A changed or invented fact, number, date or outcome (rows 2, 4, 6, 8, 12, 14, 18, 20).
- Added commentary or interpretation that is not in the email, even when every fact is right (row 22, Version B).
- Missing the detail the reader needs to act (row 10).
- As long as the email itself, even when accurate (row 16).

**Winner:** Version A. It kept all four items and every number in 54 words and added nothing. Version B had the facts right but added "demonstrates the effectiveness of our evolving marketing strategy", "highlighting an opportunity for improvement" and "to ensure accurate performance measurement", none of which is in the email. The "keep a positive tone" instruction in its prompt pushed it toward spin.

## Screenshots, links or repo paths (optional if you followed the demo)

1. Eval setup (judge): [claude-judge-a-vs-b.webp](screenshots/claude-judge-a-vs-b.webp)
2. Starter rows: [starter-dataset.md](starter-dataset.md)
3. Generator runs: [chatgpt-version-a-run.webp](screenshots/chatgpt-version-a-run.webp), [chatgpt-version-b-run.png](screenshots/chatgpt-version-b-run.png)

### Test input (same for both versions)

```
Summarize this email for the CEO.

Subject: Q4 Marketing Campaign Update

Hi team,

Social media engagement is up 25% month-over-month due to the new content calendar and paid ad experiments.

Newsletter open rate dropped from 42% to 35%; we'll test new subject lines next week.

The product video campaign is delayed until November, pending legal approval; creative assets are ready.

Please ensure all campaign tracking links are added by Friday.

Best,
Priya
```

### Version A output (generator: ChatGPT)

- Social media engagement increased 25% month-over-month, driven by the new content calendar and paid ad experiments.
- Newsletter open rates declined from 42% to 35%; new subject lines will be tested next week.
- Product video campaign delayed until November pending legal approval; creative assets are ready. All campaign tracking links must be added by Friday.

### Version B output (generator: ChatGPT)

The Q4 marketing campaign is showing encouraging momentum, with social media engagement increasing 25% month-over-month, driven by the new content calendar and paid advertising experiments. This strong performance demonstrates the effectiveness of our evolving marketing strategy. However, newsletter open rates declined from 42% to 35%, highlighting an opportunity for improvement. The team will test new subject lines next week to boost engagement. Meanwhile, the product video campaign has shifted to November, pending legal approval, although creative assets are ready. As a next step, all campaign tracking links must be finalized by Friday to ensure accurate performance measurement.
