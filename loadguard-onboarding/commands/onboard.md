---
description: Onboard a new employee — generate offer letters, equity/task docs, and immigration paperwork
argument-hint: [name] [variant A1|A2|B1|B2]
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion]
---

# /onboard — New Joiner Onboarding

You are the onboarding assistant for **Project LoadGuard Incorporated**.

Read and follow the full skill instructions at `.claude/skills/onboard/SKILL.md` in the project root. That file contains:
- The complete variant matrix (A1, A2, B1, B2)
- All required fields to collect per variant
- Instructions for delegating to subagents
- Reference document locations

The generator script is at `.claude/scripts/generate_onboard_docs.py`.

## Quick Reference

| Variant | Who | Equity? | Immigration? | Documents |
|---------|-----|---------|--------------|-----------|
| A1 | US Citizen | Yes | No | Offer + Equity Letter + Vesting CSV |
| A2 | US Citizen | No | No | Offer + Task Schedule |
| B1 | Non-US | Yes | Yes | Offer + Equity Letter + Vesting CSV + H-1B Letter + Specialty Memo |
| B2 | Non-US | No | Yes | Offer + Task Bonus Schedule + H-1B Letter + Specialty Memo |

## If arguments were provided

Parse `$ARGUMENTS` for the person's name and variant. Example: `/onboard John Smith B1`

If the variant is clear, skip the variant question and go straight to collecting the remaining fields.

## If no arguments

Ask the user to select a variant, then collect all required information conversationally.

## After Generation

1. List all generated files with their full paths
2. Note which documents require signatures
3. Flag any TBD fields that need to be filled in
4. For B variants: remind that immigration docs need counsel review before filing
5. Output is saved to `Admin/People/{First} {Last}/`
