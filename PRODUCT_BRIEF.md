# Strata — Product brief

**Version:** 1.0 functional prototype  
**Category:** Computer vision evaluation and product operations  
**Audience:** Product managers, technical leads, QA specialists and CV engineers

## 1. Product summary

Strata is a connected ledger for the evidence behind computer vision product decisions.

It records what was tested, which model version was used, how the test was performed, what happened and how the result relates to an event's evaluation targets. It also connects field-pilot planning and feedback to the broader product record.

**Product goal:** make model-evaluation evidence easier to maintain, inspect and trace without reconciling disconnected spreadsheets.

## 2. Problem and opportunity

The starting workflow relies on separate spreadsheets and documents for model configuration, QA testing, site readiness and pilot evaluation.

These tools are individually flexible but do not maintain reliable relationships between records. As versions, attempts and pilot activity accumulate, teams must manually answer questions such as:

- Which evidence belongs to this model version?
- Has this scenario been tested again after a model change?
- Is a missed event a repeat problem or an isolated observation?
- Does a candidate have comparable evidence against the production version?
- Are we missing evidence, or is the available evidence below the required target?

Strata's opportunity is not to replace the model-development pipeline. It is to provide a shared operational record around that pipeline.

## 3. Users and access

| User | Main need | Current application role |
|---|---|---|
| Product manager / technical lead | Review evidence, coordinate testing and pilots, and make informed release decisions | Admin |
| QA specialist | Record attempts, review outcomes, identify coverage gaps and complete QA sessions | QA |
| CV engineer | Maintain model definitions, versions and model-event configuration | CV Engineer |

Access is invitation-only. Signing up for an identity alone does not grant workspace membership. Admin manages invitations and application roles.

## 4. Core record structure

- **Event:** the behavior the product should detect, with its evaluation targets and error priorities.
- **Model and version:** the model family and the specific version being configured or evaluated.
- **Scenario:** a reusable test situation linked to an event.
- **QA session:** a collection of attempts for one model version, covering one or more events.
- **QA attempt:** one execution or observation, including camera, scenario, outcome, delay and optional supporting evidence.
- **Evaluation scorecard:** automatically generated totals and evaluation output from a completed, locked QA session.
- **Pilot:** the site context, readiness, cameras, test plan, instructions and actual field-test record.
- **Hypothesis:** a proposed change and the reasoning and evidence associated with investigating it.

The model version's evaluation history can contain multiple QA sessions and scorecards. A scorecard is not an automatic summary of every attempt ever recorded for that version.

## 5. Primary workflow

**Configure → test → inspect → preserve → compare**

1. Admin defines events, evaluation targets and reusable scenarios.
2. Admin or a permitted engineer maintains model versions and event links.
3. QA creates a session for one model version.
4. QA records attempts and attaches available evidence.
5. The session shows calculated outcomes, metrics, coverage and causes.
6. Finishing and locking the session preserves its attempt evidence and automatically generates its evaluation scorecard.
7. Admin inspects eligible evaluation evidence and model-version comparisons.
8. Production/candidate assignments remain explicit human-managed records.

There is no separate manual Runs workflow in the current interface. Internal evaluation records support traceability and calculations without requiring duplicate user entry.

## 6. Pilot workflow

Pilot management brings three previously separate document functions into the product:

1. **Site profile and readiness:** site context, contacts, readiness questions and camera inventory.
2. **Testing guidance and planning:** instructions, event coverage and model-version assignments in the test plan.
3. **Test log and results:** actual observations, outcomes and pilot summaries.

A pilot can involve multiple model families. Planned versions describe intended testing; the version recorded on an actual attempt describes the evidence.

Historical aggregate observations are kept distinct from detailed logged attempts. Missing historical provenance is left explicit rather than inferred from a later plan.

## 7. Evaluation approach

Strata uses recorded evidence to calculate metrics such as recall, precision, F-beta, false alarms and alert-delay summaries.

Important distinctions:

- **Record state is not readiness:** Draft/Locked describes editability; Ready/Not ready/Not enough data/No data describes an evaluation outcome.
- **Real and staged evidence are not interchangeable:** the session overview can show pooled summaries, while scorecards separate these sources and readiness uses real evidence.
- **Targets are event-specific:** the product can represent different priorities for misses and false alarms.
- **Comparability must be explicit:** the current comparison checks test-set and configuration identifiers. It does not independently verify that an external dataset is identical.
- **Missing evidence is visible:** absent denominators and unknown provenance should not become fabricated results.

## 8. Deliberate trade-offs and current limits

| Decision | Reason |
|---|---|
| Keep attempts inside QA sessions | Make testing work easy to organize and avoid duplicate entry |
| Reuse scenarios across sessions | Support repeated testing of the same situation across model versions |
| Generate scorecards automatically | Derive evaluation evidence from the actual testing record |
| Preserve historical event membership | Later catalog edits must not add or remove events from old evaluation evidence |
| Keep model assignment manual | Recording a release decision is different from deploying infrastructure |
| Retain unknown historical provenance | A precise-looking but invented model assignment would be misleading |

Current boundaries:

- This is an AI-assisted functional prototype, not evidence of customer adoption or business impact.
- No model training, automated inference execution or edge-deployment integration is included.
- Locking preserves recorded evidence, but evaluation verdicts still use current targets and scoring settings; a fully frozen historical scoring policy is not implemented.
- The public showcase contains documentation only, with no application code, customer documents, user accounts or live data.

## 9. Proposed measures of success

These are evaluation criteria for future validation, not achieved results:

- Time needed to trace a metric back to its model version and supporting attempts.
- Time spent reconciling QA, model and pilot records outside the product.
- Completeness of version, scenario, camera and outcome references in recorded attempts.
- Ability to identify missing or incompatible evidence before a release discussion.
- QA session completion and repeat usage by intended team roles.
- Qualitative feedback from PMs, technical leads, QA and CV engineers about whether the connected record improves their decisions.

## 10. Portfolio perspective

Strata demonstrates how a spreadsheet-based operational problem can be translated into a connected product: defined users and permissions, reusable records, structured workflows, calculated outputs and explicit limits on what the evidence can support.

The next validation step is to observe intended users completing realistic QA and pilot tasks, then assess whether the product reduces reconciliation effort and improves evidence traceability.
