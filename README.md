# GoHighLevel: AI Lead Scoring

A GoHighLevel automation: the moment a new contact is created in the CRM, Claude analyzes the contact's details and writes a lead-quality assessment directly onto the contact's record - fully automatic, no manual step required.

## What it does

1. **Trigger** - GoHighLevel's "Contact Created" workflow trigger fires the moment a new contact lands in the CRM.
2. **AI step** - Claude, via GoHighLevel's native Claude integration, analyzes the contact's available fields (company, job title, source, any notes) and writes a short lead-quality assessment.
3. **Output** - the assessment is written straight onto the contact's own CRM record, visible to anyone on the team without needing to check a separate tool.

## Tested the honest way

Rather than just publishing the workflow and assuming it works, the whole chain was fired for real: created a genuine new contact and watched it trigger live. Claude correctly identified a thin, placeholder-looking contact as low-quality and explained exactly why (no company, job title, or engagement signal) - confirmed directly on the contact's own CRM profile afterward.

## Workflow documentation

`workflow-steps.md` documents the exact trigger/action configuration, since GoHighLevel workflows aren't portable as a single importable file the way n8n/Make workflows are.

---
Part of a small portfolio of tested automation/AI builds — see [ParishSynthMind](https://github.com/ParishSynthMind) for the others.
