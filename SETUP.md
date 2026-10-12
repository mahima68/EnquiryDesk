# No-code setup

## Form and sheet

Create Google Forms questions in this exact order:
1. Your enquiry — Paragraph, required.
2. Your name (optional) — Short answer.
3. Contact email (optional) — Short answer.

Explain that AI helps prepare drafts for owner review and submitting does not confirm a booking or price. During testing use fictional details. Link responses to a new Google Sheet. Leave its first four columns in place. Set E1 to Draft review and F1 to Status. Keep the response tab name `Form responses 1`, or update both Make modules to your actual tab name. Do not insert empty rows in the response data.

Keep the review sheet private to the owner or authorized staff. Publishing the customer form does not require publishing its responses.

## Import the blueprint

Create a Make scenario; use More → Import blueprint. Import `enquirydesk.blueprint.json`. The three modules should be Watch New Rows, Run an agent, Update a Row.

In modules 4 and 5, select your Google Sheets connection and replace YOUR_SPREADSHEET_ID with your sheet ID (the section between `/d/` and `/edit` in its URL). Connection placeholders are intentionally null and must be configured after import. Verify the account has Sheets read/write access by testing the trigger. A successful Google sign-in alone does not prove Sheets access.

In module 1, select Make's AI provider or an appropriate connected provider. Choose a model available in your plan. The documented examples use Claude Haiku 4.5. Paste your approved business facts into the instructions instead of the fictional example. Keep Conversation ID empty to avoid sharing enquiry context between customers. Do not add send, booking or refund tools.

Verify mappings:
- Agent Input uses module 4, Your enquiry (B).
- Update Row number uses module 4, Row number.
- A–D map back to the corresponding original fields.
- E uses module 1, Response.
- F is the literal text Needs review.
- Value input option is Raw.

The saved-draft filter checks E is empty before calling the agent. Do not remove it when replaying old test rows.

## Scheduling and recovery

Set scheduling to every 15 minutes, or choose an interval supported by your plan and enquiry volume. Scheduling and activation are not portable in the blueprint; configure them in your account.

In Scenario settings enable Process data in order and Store incomplete executions. If a failed run is stored, resolve it through Incomplete executions before resetting the trigger. Inspect History for errors. Ordered processing can stop new enquiries behind an unresolved failure. This recovery configuration needs your own fault test before production use.

For a new empty sheet, start from All to process upcoming test submissions. For a sheet with existing real enquiries, select the intended starting point carefully. Never blindly replay all live records.

Test all cases in TEST-CASES.md, inspect E/F and compare A–D to the original form input. Activate only after review. Send replies manually and set Status to Replied afterward. Monitor credits; free access is not unlimited.

Official documentation:
- https://apps.make.com/google-sheets
- https://help.make.com/create-your-first-ai-agent
- https://help.make.com/scenario-settings
