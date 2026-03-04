---
name: onboard-b1
description: Generate onboarding documents for a Non-US Citizen equitied employee with immigration paperwork
allowed-tools: Read, Write, Bash, Glob
---

# Onboard B1 — Non-US Citizen, Equitied Employee (Immigration-Ready)

You generate the full onboarding document package for a **Non-US Citizen who will receive equity**, including all immigration-relevant documents.

## Documents to Generate

### 1. Immigration-Ready Offer of Employment Letter

Everything from variant A1's offer letter, PLUS the following H-1B / immigration-critical provisions:

- **Specialty Occupation Language**: The position section MUST describe the role as a specialty occupation requiring a bachelor's degree (or foreign equivalent) in a specific field. Name the field(s) explicitly (e.g., Computer Science, Electrical Engineering).
- **Position Duties**: Detailed description of actual job duties that demonstrate specialty-level work
- **Minimum Education**: Explicitly state the minimum degree requirement
- **Full-Time Confirmation**: "permanent, full-time position requiring a minimum of 40 hours per week"
- **Prevailing Wage**: Compensation will be at or above the prevailing wage for the position at the work location, as required by DOL
- **Immigration Sponsorship Section**: The Company intends to file an H-1B petition (or other applicable petition) with USCIS. Company bears filing costs and attorney fees as required by law. Company will file required LCA with DOL.
- **Work Location Compliance**: Any change in work location will comply with H-1B requirements (amended petition or new LCA if required)
- **Return Transportation**: In the event of termination, Company will offer to pay reasonable return transportation costs per 8 CFR § 214.2(h)(4)(iii)(E)
- **Start Date**: Contingent on obtaining necessary work authorization
- **I-9 Verification**: Reference to Form I-9 requirements

If an Introductory Period is requested, it MUST include language making clear that:
- The employee is full-time from day one
- Prevailing wage applies throughout
- Benefits begin immediately
- It is NOT a separate or contingent engagement

### 2. Equity Incentive Letter

Same as A1 — total shares, time-based and milestone-based vesting, Board approval contingency, tax disclaimer, signature blocks.

### 3. Milestone Vesting Schedule (CSV)

Same as A1.

### 4. H-1B Support Letter

A letter addressed to USCIS / DOL that includes:
- Company description (Project LoadGuard Incorporated, Delaware C-corp, maritime security technology)
- Position description and why it qualifies as a specialty occupation
- The employee's qualifications (degree, prior experience, specialized skills)
- Why the company needs this specific skill set
- Confirmation of prevailing wage compliance
- Confirmation of full-time employment
- Company contact information

Structure:
```
From: Project LoadGuard Incorporated
      123 Example Street, Seattle, WA 98101

To: U.S. Citizenship and Immigration Services

Re: H-1B Petition for [NAME] — [POSITION] (Specialty Occupation)
```

### 5. Specialty Occupation Justification Memo

An internal memo documenting:
- Why the position requires specialized knowledge
- The degree requirement and how it relates to the job duties
- Industry standards for similar positions (reference BLS Occupational Outlook Handbook)
- The employee's specific qualifications that meet or exceed requirements
- How the employee's prior experience is directly relevant

## How to Generate

Run the generator script:

```bash
cd /path/to/project
python3 .claude/scripts/generate_onboard_docs.py \
  --variant B1 \
  --name "FULL_NAME" \
  --position "POSITION_TITLE" \
  --start-date "START_DATE_OR_TBD" \
  --reports-to "REPORTS_TO" \
  --work-location "WORK_LOCATION" \
  --salary "SALARY_OR_TBD" \
  --total-shares "TOTAL_SHARES" \
  --time-shares "TIME_BASED_SHARES" \
  --milestone-shares "MILESTONE_BASED_SHARES" \
  --cliff-months 12 \
  --vest-years 4 \
  --milestones "MILESTONE_JSON" \
  --citizenship "COUNTRY" \
  --visa-status "CURRENT_STATUS" \
  --degree "DEGREE_AND_FIELD" \
  --university "UNIVERSITY_NAME" \
  --prior-employer "PRIOR_EMPLOYER_DESCRIPTION" \
  --specialty-justification "WHY_SPECIALTY_OCCUPATION"
```

After generating, report back:
1. What files were created and where
2. Remind the user that ALL immigration documents should be reviewed by immigration counsel before filing
3. Flag any fields left as TBD that must be completed before filing
