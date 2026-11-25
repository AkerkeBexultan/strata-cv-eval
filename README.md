# Strata
## A computer vision evaluation ledger

**From disconnected testing spreadsheets to traceable model-release decisions.**

Strata is an AI-assisted functional prototype for teams building computer vision products. It connects model versions, event categories, QA evidence, pilot activity and evaluation results in one workspace.

This repository is a **documentation-only product showcase for hiring managers**. The implementation is maintained separately in a private repository. No application source code, client documents, accounts or live customer data are included here.

[Read the product brief](PRODUCT_BRIEF.md)

## The problem

Computer vision teams often maintain separate spreadsheets for model configuration, QA testing and client pilots. A single result can become difficult to trace:

- Which model version was tested?
- Which event and scenario did the test cover?
- Was the evidence real, staged or a look-alike?
- How did the model behave, and what went wrong?
- Is there enough comparable evidence to support a release decision?

Updating one spreadsheet does not reliably update the others. Strata addresses the record-keeping and evidence-connection problem, rather than training or executing computer vision models.

## The product

| Area | What Strata connects |
|---|---|
| Event catalog | Event definitions, evaluation targets and linked models |
| Model catalog | Model families, version history, production/candidate assignments and comparison evidence |
| Scenario catalog | Reusable scenarios and the QA attempts that tested them |
| QA sessions | Individual attempts, outcomes, causes, delays, coverage and automatically generated evaluation scorecards |
| Pilots | Site profiles, readiness checks, cameras, test plans, instructions, test logs and results |
| Hypotheses and trends | Proposed changes and inspection of saved evaluation evidence over time |
| Team access | Invitation-only Admin, QA and CV Engineer roles |

## One example workflow

1. Define a **falling** event and its evaluation targets.
2. Link a model and create a candidate version.
3. Reuse a scenario such as **“lie down for two seconds and get up.”**
4. Create a QA session for that model version.
5. Record attempts with a camera, outcome, delay and supporting evidence.
6. Review the session's results and lock it to generate an evaluation scorecard.
7. Use eligible evaluation evidence to inspect candidate-versus-production performance.

*This example is illustrative, not a customer result.*

## Product decisions worth highlighting

- **One testing workflow:** users record attempts in QA sessions; they do not re-enter the same evidence in a separate Runs section.
- **Reusable scenarios:** a scenario can be tested repeatedly across sessions and model versions.
- **Evidence provenance:** real and staged evidence are distinguished; unknown historical version assignments are not invented.
- **Explicit comparison conditions:** incompatible test-set or configuration identifiers prevent a misleading numerical comparison.
- **Human release ownership:**
