---
name: onboard-b2
description: Generate onboarding documents for a Non-US Citizen task-compensated (non-equitied) employee with immigration paperwork
allowed-tools: Read, Write, Bash, Glob
---

# Onboard B2 — Non-US Citizen, Task-Compensated Employee (Immigration-Ready)

You generate the onboarding document package for a **Non-US Citizen who will be compensated per task/scope**, including all immigration-relevant documents.

## IMPORTANT: H-1B and Task-Based Compensation

For H-1B purposes, the employee MUST be a full-time W-2 salaried employee. Task-based compensation is structured as:
- A **base salary** at or above prevailing wage (required by DOL for H-1B)
- **Task completion bonuses** on top of the base salary
- The base salary is guaranteed; task bonuses are additional compensation for deliverable completion

This is NOT a contractor/1099 arrangement. The offer letter must make this crystal clear.

## Documents to Generate

### 1. Immigration-Ready Offer of Employment Letter with Task Bonuses

Combines immigration-ready language from B1 with task-based structure from A2:

- **Specialty Occupation Language**: Full specialty occupation description with degree requirements
- **Position Duties**: Detailed description demonstrating specialty-level work
- **Compensation Structure**:
  - Base salary at or above prevailing wage (stated explicitly)
  - Task completion bonuses as described in attached Task Bonus Schedule (Exhibit A)
  - Language: "In addition to your base salary, you will be eligible for task completion bonuses as set forth in the Task Bonus Schedule attached hereto as Exhibit A."
- **Immigration Sponsorship Section**: H-1B petition, LCA, Company bears costs
- **Prevailing Wage Compliance**: Base salary alone meets or exceeds prevailing wage
- **Full-Time**: 40+ hours/week, permanent position
- **Return Transportation**: Per 8 CFR § 214.2(h)(4)(iii)(E)
- All other standard offer letter sections

If an Introductory Period is requested, same H-1B-safe language as B1.

### 2. Task Bonus Schedule (Exhibit A) — DOCX

A table-format document:
- Task #
- Scope / Description
- Deliverable(s)
- Bonus Amount ($ amount — clearly labeled as "bonus" not "compensation")
- Deadline / Target Date
- Acceptance Criteria
- Status (Pending)

Below the table:
- Clarification: "These bonuses are in addition to, and do not replace, the base salary described in the Offer of Employment Letter."
- Total potential bonus compensation
- Payment terms: bonuses paid in next payroll cycle following acceptance
- Task Schedule may be amended by mutual written agreement

### 3. H-1B Support Letter

Same structure as B1:
- Company description
- Position as specialty occupation
- Employee qualifications
- Prevailing wage confirmation
- Full-time employment confirmation
- Compensation structure explanation (base salary + task bonuses)

### 4. Specialty Occupation Justification Memo

Same as B1:
- Why the position requires specialized knowledge
- Degree requirement and relation to duties
- Industry standards
- Employee's specific qualifications
- Prior experience relevance

## How to Generate

Run the generator script:

```bash
cd /path/to/project
python3 .claude/scripts/generate_onboard_docs.py \
  --variant B2 \
  --name "FULL_NAME" \
  --position "POSITION_TITLE" \
  --start-date "START_DATE_OR_TBD" \
  --reports-to "REPORTS_TO" \
  --work-location "WORK_LOCATION" \
  --salary "BASE_SALARY" \
  --tasks "TASKS_JSON" \
  --citizenship "COUNTRY" \
  --visa-status "CURRENT_STATUS" \
  --degree "DEGREE_AND_FIELD" \
  --university "UNIVERSITY_NAME" \
  --prior-employer "PRIOR_EMPLOYER_DESCRIPTION" \
  --specialty-justification "WHY_SPECIALTY_OCCUPATION"
```

The `--tasks` JSON for B2 uses "bonus" language:
```json
[
  {
    "description": "Task description",
    "deliverable": "What constitutes completion",
    "bonus": "$5,000",
    "deadline": "2026-04-30",
    "criteria": "Acceptance criteria"
  }
]
```

After generating, report back:
1. What files were created and where
2. Remind the user that ALL immigration documents should be reviewed by immigration counsel before filing
3. Flag any fields left as TBD that must be completed before filing
4. Note: the base salary MUST meet or exceed prevailing wage — this is non-negotiable for H-1B
