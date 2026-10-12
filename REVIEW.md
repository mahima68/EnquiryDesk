# Two-pass pre-publication review — 13 October 2026

## Pass 1 — workflow and evidence audit

Reviewed the exported live Make blueprint, instructions, source/output mappings, guard filter, recovery configuration and existing six fictional test results.

Confirmed:
- Watch New Rows supplies enquiry column B to the agent.
- Writeback uses that same source row number and preserves A–D.
- E receives the agent response; F receives Needs review.
- Shared conversation memory is empty and no action tools or sending modules are attached.
- Ordered processing and incomplete execution storage are enabled.
- The completed-draft filter checks whether E is empty.

Findings and changes:
- Writeback used USER_ENTERED, allowing spreadsheet interpretation of formula-like inputs. Changed the live scenario to RAW and saved it.
- The original guide described a starter kit rather than the implemented workflow. Replaced the public setup documentation with actual mappings, model and recovery settings.
- Previous acceptance checks expected rigid labels and an entirely blank injection reply field, while observed outputs included expanded labels and an owner-review placeholder. Documented these deviations rather than claiming exact schema conformance.
- Added a real exported Make blueprint. Removed account connection IDs, private spreadsheet IDs, owner links and account screenshots from the public package.

## Pass 2 — fresh regression and release integrity

Submitted a new fictional form enquiry requesting two promotional videos for a website, with Pune specified and no deadline. Used the name `=1+1` to check literal-text handling.

The live run completed successfully. Exported results showed:
- Source message and name preserved; name remained literal =1+1 rather than 2.
- AI response saved to the matching row with Needs review.
- Routine classification; no invented price or delivery promise.
- Three relevant questions; no redundant question about quantity, location or website use.

Independently checked the public blueprint's module order, reference IDs, source preservation, RAW writeback, empty conversation ID, no tools, guard expression, recovery settings and exact prompt agreement with ASSISTANT-INSTRUCTIONS.md. Reopened the ZIP and checked each entry against the release files and privacy exclusions.

## Scope of verification

The earlier six cases and fresh seventh case verify observed behavior on those inputs, not every possible AI output. The initial failed deadline draft is excluded from public examples; the corrected retest is included. A previous no-new-submission run left CSV exports identical.

Not executed: importing the sanitized blueprint into a separate account, deliberate replay/rewind of completed rows, injected service outage, incomplete-execution resume, or high-volume load testing. These are documented limitations, not passing tests. Scheduling and connections must be configured after import. The project is an owner-reviewed demonstration, not a zero-error autonomous customer service system.
