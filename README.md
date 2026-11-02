# AI Spend Policy Setup Assistant

**[Try the live demo](https://karishma0502-pixel.github.io/ai-spend-policy-assistant/)**: it opens in a labelled sample mode, with no key or sign-up.

Turns an ambiguous expense policy into a reviewed, tested set of approval rules. The AI proposes, code checks, and a person decides.

**[Watch the 3:36 walkthrough](https://www.loom.com/share/08eb69d91637477d9151d52dece56ac9)**

[![Video walkthrough of the assistant](https://cdn.loom.com/sessions/thumbnails/08eb69d91637477d9151d52dece56ac9-62dc0bbf276ddbbd.gif)](https://www.loom.com/share/08eb69d91637477d9151d52dece56ac9)

## The problem

A company's written expense policy rarely holds every decision a spend platform needs. "Conference spending above NZ$2,000 requires Finance approval" doesn't say whether the limit is per purchase or per trip, or who approves first. The Finance Manager setting it up is accountable for getting it right, but isn't the person who can decide what the policy means.

## How it works

1. **Upload.** You upload or paste your spend policy and related documents, such as emails, an authority table, working notes and an HR export.
2. **Read.** The AI reads all the documents together. It extracts every rule with the exact quote and source, and raises questions where documents conflict, are silent, or ask for something the platform can't do. It decides nothing.
3. **Check in code.** Plain code, not AI, verifies that every quote exists in the source text, checks the HR file for missing, self-approving or looping approvers, and flags any rule the AI didn't ask about. You can add that rule as a question with one click.
4. **Decide.** Each question goes to the role allowed to answer it, for example the CFO. You pick the role and source document and write the decision. The page checks that the role has authority and stores the decision next to its source.
5. **Review and export.** The finish screen shows every rule with its quote and source, every decision with who made it, and the checks. You download a reviewed rule set as JSON, CSV or clean text. Unresolved items are held back, not guessed.

The built-in examples go further, using a fictional company: they draft the settings, test them on example trips, and require a person's approval before export. Nothing is applied to a live platform, no stakeholder is contacted, and no money moves.

## Evaluation

I ran 12 test cases with real AI on 28 October 2026 and judged each one myself: **12 Pass, 0 Needs work, 0 Fail**. The Evals tab in the demo shows every result and lets you run the cases again.

![The Evals tab showing 12 of 12 cases passing](docs/images/evals.png)

The cases cover routing, the exact NZ$2,000 boundary, split purchases, ambiguity, conflicting sources, unauthorised answers, missing approvers, self-approval and approval loops, missing receipts, instructions hidden in a document, edits after approval, and a simulator failure.

**What testing changed:** running the evals exposed a crash, which I fixed before recording these results. A later change makes the coverage check notice amounts that no question mentions, and that change came after the recorded run.

**What this doesn't show:** these are passes on fictional data in specific runs, and AI output varies between runs. No Finance Manager has piloted this, and no time saving has been measured.

## Run it

Use the [live demo](https://karishma0502-pixel.github.io/ai-spend-policy-assistant/), or open `index.html` in a browser. There is no build step.

Sample mode needs no key. Real AI needs your own Claude API key, and your account pays for what you run, so use a separate key with a low spending limit. The key is held in memory for that tab, sent only to Anthropic, and never stored in this repo.

## Limits

- AI results vary between runs, and it reads up to 12 rules and 10 questions per run.
- The built-in examples cover one fictional company and one conference policy. Nothing is connected to a real spend platform.
- The CFO's answers are scripted. The page checks a chosen role against a fixed map and doesn't verify anyone's identity.
- Your own documents stop at rules, questions and an export of those. Drafting and scenario tests work on the built-in cases only.
- Quotes from a PDF can't be checked against the source, so use a `.txt` copy for that.
- The HR check needs a CSV or TSV file with ID and manager columns.
- Nothing is saved between visits.

All companies, people and amounts are fictional.

## Documents

- [Product requirements](docs/PRD.md)

## Credits

Built for the Product Faculty Agentic AI capstone. The page's design system and AI connection helper come from the Product Faculty capstone kit and remain theirs. No open-source licence is granted for this repo.
