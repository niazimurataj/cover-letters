---
name: onboard-a2
description: Generate onboarding documents for a US Citizen task-compensated (non-equitied) employee
allowed-tools: Read, Write, Bash, Glob
---

# Onboard A2 — US Citizen, Task-Compensated (Non-Equitied) Employee

You generate the onboarding document package for a **US Citizen who will be compensated per task/scope** rather than receiving equity.

## Documents to Generate

### 1. Offer of Employment Letter with Task Schedule

A formal offer letter that includes:
- Position and title
- Full-time or part-time designation (as specified)
- Compensation model: **task/scope-based** — each completed deliverable triggers payment
- Reference to the attached Task Schedule for compensation details
- Work location
- Start date
- At-will employment
- Reference to CIIAA as condition of employment
- Employee benefits eligibility (if full-time)
- No conflicts representation
- Governing law (Delaware)
- Entire agreement, severability
- Signature blocks for CEO and the employee

The compensation section should state:
> "Your compensation will be determined on a task-completion basis as set forth in the Task Schedule attached hereto as Exhibit A. Each task defines a scope of work and a corresponding payment amount. Payment will be made upon the Company's confirmation that the deliverable has been satisfactorily completed, in accordance with the Company's standard payroll schedule."

### 2. Task Schedule (Exhibit A) — DOCX

A table-format document attached as Exhibit A with columns:
- Task #
- Scope / Description
- Deliverable(s)
- Compensation ($ amount)
- Deadline / Target Date
- Acceptance Criteria
- Status (Pending)

Below the table, include:
- Total potential compensation (sum of all tasks)
- Payment terms: Net 15 from acceptance of deliverable
- Dispute resolution: deliverable acceptance determined by CEO or designee
- Amendment: Task Schedule may be amended by mutual written agreement
- Note: completion of tasks does not guarantee additional tasks or continued employment

### How to Generate

Run the generator script:

```bash
cd /path/to/project
python3 .claude/scripts/generate_onboard_docs.py \
  --variant A2 \
  --name "FULL_NAME" \
  --position "POSITION_TITLE" \
  --start-date "START_DATE" \
  --reports-to "REPORTS_TO" \
  --work-location "WORK_LOCATION" \
  --tasks "TASKS_JSON"
```

The `--tasks` argument is a JSON string:
```json
[
  {
    "description": "Task description",
    "deliverable": "What constitutes completion",
    "compensation": "$5,000",
    "deadline": "2026-04-30",
    "criteria": "Acceptance criteria"
  }
]
```

After generating, report back what files were created and where.
