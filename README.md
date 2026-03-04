# Cover Letters & Portfolio

## AI-Powered Legal Onboarding System

The `loadguard-onboarding/` directory contains an employee onboarding system I built in Claude Code for a hardware startup. It generates immigration-ready legal documents end-to-end:

- **Offer letters** with H-1B compliant specialty occupation language
- **H-1B support letters** addressed to USCIS/DOL
- **Specialty occupation justification memos** referencing BLS standards
- **Equity incentive letters** with vesting schedules
- **E-Verify** and I-9 compliance references

The system uses a variant matrix (A1/A2/B1/B2) to handle US citizens vs. non-US citizens, equitied vs. task-compensated employees, and routes to the correct document set automatically.

### How it works

1. `/onboard [name] [variant]` — Claude Code slash command triggers the flow
2. Subagents handle each variant's document requirements
3. A Python generator script produces formatted DOCX files ready for signature

Built because I needed to sponsor engineers and couldn't afford immigration counsel. The system has successfully onboarded employees with filing-ready documents.
