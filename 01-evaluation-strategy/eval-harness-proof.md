# First LLM-as-a-Judge Eval, Module 1

> Repo file `ai-evals/01-evaluation-strategy/eval-harness-proof.md`. The eval evidence behind the **Eval Results** slide of the final pitch deck (Module 6).
>
> Fill this with the **First Eval Lab** builder, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

## Version A, Concise, system prompt used

```
You are an executive briefing assistant. Summarize the email below in exactly 3 bullets, under 60 words total.
```

## Version B, Narrative, system prompt used

```
You are a PR communications assistant. Summarize the email below in about 100 words as a narrative. Lead with wins, then risks. No bullets.
```

## Eval setup, dataset name + judge model/family

- **Dataset:** `Module1Output`, the Q4 Marketing Campaign Update email below plus a 22-row starter set in [starter-dataset.md](starter-dataset.md): 20 LLM-generated rows whose first-pass labels were reviewed and kept, and the two real Version A and Version B outputs added by hand (11 good, 11 bad).
- **Generator:** Claude, same model for Version A and Version B.
- **Judge:** ChatGPT, GPT-5.6 Sol (high) (OpenAI GPT family), a different model family than the generator (avoids self-preference bias).
- **Judge type:** Conciseness and faithfulness LLM-as-a-Judge, binary score. 1 = concise and faithful, 0 = fails either one. The judge saw the email and the summary only, not the system prompts or version labels.

| Version | Score | Judge's reason |
|---|---|---|
| A, Concise | 1 | The summary is concise, accurate, and faithful to the original email, preserving all key information, figures, deadlines, and dependencies without unnecessary details. |
| B, Narrative | 0 | The summary includes unnecessary commentary and unsupported interpretations such as "clear momentum," "key dependency," and "so performance can be measured accurately," making it less concise and strictly faithful to the original email. |

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

**Winner:** Version A. It kept all four items and every number in 51 words and added nothing. Version B had the facts right but added "clear momentum", "key dependency" and "so performance can be measured accurately", none of which is in the email.

## Screenshots, links or repo paths (optional if you followed the demo)

1. Eval setup (judge): [judge-version-a.png](screenshots/judge-version-a.png), [judge-version-b.png](screenshots/judge-version-b.png)
2. Starter rows: [starter-dataset.md](starter-dataset.md)
3. Generator runs: [version-a-run.png](screenshots/version-a-run.png), [version-b-run.png](screenshots/version-b-run.png)

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

### Version A output (generator: Claude)

- Social media engagement rose 25% month-over-month, driven by the new content calendar and paid ad experiments.
- Newsletter open rate fell from 42% to 35%; new subject lines will be tested next week.
- Product video campaign is delayed to November pending legal approval; creative assets are ready. Tracking links are due Friday.

### Version B output (generator: Claude)

Social media engagement climbed 25% month-over-month in Q4, driven by the new content calendar and paid ad experiments, giving the marketing team clear momentum. Creative assets for the product video campaign are also complete and ready to go. On the risk side, the newsletter open rate fell from 42% to 35%, and the team will begin testing new subject lines next week to reverse the decline. The product video campaign itself has slipped to November while it awaits legal approval, making that sign-off the key dependency. Priya has also asked that all campaign tracking links be added by Friday so performance can be measured accurately.
