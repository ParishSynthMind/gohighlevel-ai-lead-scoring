# Workflow configuration — "GoHighLevel AI Lead Scoring"

GoHighLevel workflows aren't portable as a single importable file, so this documents the exact real step configuration from the live, published workflow.

## Trigger: Contact Created

- **Filters:** none — fires on every new contact, no pre-filtering.

## Step 1: Claude action — "Analyze new contact details"

- Native GoHighLevel action (flagged by the platform itself as a premium action, incurs additional charges per execution) — no separate Anthropic API key needed, the cleanest integration of all four no-code builds.
- **Model:** Sonnet 5.5
- **Effort:** Medium
- **Prompt:**
  ```
  Analyze this new contact and categorize lead quality as High, Medium, or Low based on the information available. Return a concise analysis that begins with exactly one label (High, Medium, or Low) followed by a short explanation.

  Contact details:
  Name: {{Contact.Full Name}}
  Email: {{Contact.Email}}
  ```

## Step 2: Update contact field — "Save AI Lead Analysis"

- **Action type:** Update field data
- **Field:** `AI Lead Analysis` (custom multi-line field, created fresh in this account since none existed)
- **Value:** `{{Claude action.#1 Analyze new contact details.Response}}` — writes Claude's full response directly onto the contact record.

## A real platform limitation, found and worked around honestly

The original plan was to branch contacts into Hot/Warm/Cold tags based on Claude's verdict. GoHighLevel's If/Else branching logic genuinely cannot read a Claude action's output to make tag decisions (confirmed by the platform's own AI builder: "The available branches cannot read this Claude action's response"). Rather than force a workaround that doesn't actually work on this platform yet, the build pivoted to writing Claude's full analysis into a readable custom field instead.

## Tested the honest way — not a manual test button

Published the workflow live, then created a genuine new contact ("Morgan Reyes," a deliberately thin test email) directly in Contacts to watch the whole chain fire on its own — no manual trigger. Claude correctly flagged the contact "Low" quality and explained exactly why: no company, job title, phone number, industry, or engagement signal, so fit/authority/budget/intent couldn't be assessed. Confirmed on the contact's own live CRM profile after a refresh.
