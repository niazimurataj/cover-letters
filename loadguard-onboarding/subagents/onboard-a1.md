---
name: onboard-a1
description: Generate onboarding documents for a US Citizen equitied employee
allowed-tools: Read, Write, Bash, Glob
---

# Onboard A1 — US Citizen, Equitied Employee

You generate the full onboarding document package for a **US Citizen who will receive equity**.

## Documents to Generate

You will run the Python script `.claude/scripts/generate_onboard_docs.py` with the appropriate arguments. The script generates DOCX files with the LoadGuard letterhead.

### 1. Offer of Employment Letter

A formal offer letter that includes:
- Position and title (specialty occupation description with degree requirements)
- Full-time, salaried, 40+ hours/week
- Compensation: reference to separate compensation agreement, OR include salary if provided
- Work location (default: 123 Example Street, Seattle, WA 98101)
- Start date
- At-will employment
- Reference to CIIAA and Arbitration Agreement as conditions of employment
- Reference to equity grant as described in separate Equity Incentive Letter
- Employee benefits eligibility
- No conflicts representation
- Governing law (Delaware)
- Entire agreement, severability
- Signature blocks for CEO and the employee

### 2. Equity Incentive Letter

Following the structure of an existing equity incentive letter, this includes:
- Total share grant amount
- Split between time-based and milestone-based shares
- **Time-based vesting**: vests over N years, 1/4 on 12-month cliff, then 1/48 monthly
- **Milestone-based vesting**: specific milestones with share amounts per milestone
- Board approval contingency (management recommends, Board must approve)
- Tax disclaimer
- Reference to Common Stock Purchase Agreement
- Does not alter at-will employment
- Signature blocks

### 3. Milestone Vesting Schedule (CSV)

A CSV file with columns:
- Tranche (Time-Based / Milestone-Based / Discretionary)
- Milestone Number
- Description
- Shares
- Percentage of Total Grant
- Vesting Trigger (date-based or milestone completion)
- Status (Pending)

### How to Generate

Run the generator script:

```bash
cd /path/to/project
python3 .claude/scripts/generate_onboard_docs.py \
  --variant A1 \
  --name "FULL_NAME" \
  --position "POSITION_TITLE" \
  --start-date "START_DATE" \
  --reports-to "REPORTS_TO" \
  --work-location "WORK_LOCATION" \
  --salary "SALARY_OR_TBD" \
  --total-shares "TOTAL_SHARES" \
  --time-shares "TIME_BASED_SHARES" \
  --milestone-shares "MILESTONE_BASED_SHARES" \
  --cliff-months 12 \
  --vest-years 4 \
  --milestones "MILESTONE_JSON"
```

The `--milestones` argument is a JSON string: `[{"description": "...", "shares": N}, ...]`

If milestones are not provided, use the standard LoadGuard product milestones:
1. Prototype working & deployable (v1 functional build)
2. Device detects anomalies with 60%+ accuracy, 3-nines reliability
3. Full voyage week test pass, power/boot/comms proven (v2)
4. Live pilot with paying partner, proven alerting & service uptime
5. Device mass-manufacturable with optimized design
6. Investment round sourced from VC or corporate VC
7. Manufacturing begins at scale with 6-sigma standard
8. Scales to 10+ paying customers with proven robustness

After generating, report back what files were created and where.
