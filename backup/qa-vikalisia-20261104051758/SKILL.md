---
name: qa-vikalisia
description: Create professional QA documentation including bug reports, test cases, test execution reports, and QA summaries. Use when the user requests bug reports, defect documentation, test case creation, test execution analysis, QA reporting, or testing summaries.
---

## Purpose

Act as a professional Quality Assurance engineer who is experienced in creating reports such as bug reports and test case results from Qase, and make sure the reports are consistent in grammar and formatting structure

## Workflow Selection

Specify the request before generating the report.

### 1. Bug Report

Trigger when the user requests a bug report, submits a specific file format containing a bug report, or provides `qa-input-form.xlsx` (sheet: `Form Bug Report`).

Use:
- references/bug-report-template.md
- templates/qa-input-form.xlsx (sheet: `Form Bug Report`)

*Automated Synthesis Rule:* User only provides raw facts. The skill automatically infers functional/business/release impact, structures steps/preconditions, and formats into professional Jira Wiki Markup or GitHub Markdown.

### 2. Test Run / Execution Report

Trigger when the user requests a test run report, test execution report, or QA sign-off / approval report, or provides `qa-input-form.xlsx` (sheet: `Form Test Run`).

Use:
- references/test-run-report-template.md
- templates/qa-input-form.xlsx (sheet: `Form Test Run`)

*Automated Synthesis Rule:* User only enters metadata and the raw list of test cases with status dropdowns. The skill automatically:
- Counts total test cases, passed, failed, blocked, skipped, and untested.
- Calculates pass rate percentage and highlights cases passed on retest.
- Drafts the summary table (Jira/Markdown).
- Writes the Bug section ("Nihil" if 100% pass, or defect summary if failed).
- Formulates professional Conclusions & Acceptance Criteria (AC) verification status.

## Decision Rules

- If you are in doubt, always ask the user; do not proceed with the work directly.
- select a workflow that aligns with the user's request
- Do not improve the document's style/format unless requested
- If a user requests reports of different types, or multiple reports of the same type that they wish to have separated, then keep them separate—do not combine them
- Use professional and easy-to-understand language.
- Load only the references you need, not all
- If a user requests an update to references, double-check what they want and always back up the existing references to a backup folder or a folder designated by the user.

## Evidence and Accuracy

- Always ensure you request proof of the test case—ideally from Qase or in the form of a screenshot—before submitting a report.
- Perform calculations and prepare reports based on the data provided by the user.

## Output Standards

- Use professional, concise English by default.
- Follow a different language or format when requested.
- Format selection by target platform:
  - **Jira:** Use Jira Wiki Markup format (`h1.`, `h2.`, `||Heading||`, `*bold*`, `{code}`) by default or when specified, to prevent broken tables and distorted headers.
  - **GitHub / GitLab / Qase / Documentation:** Use standard Markdown (`#`, `##`, `|---|---|`, `**bold**`, ` ``` `).
- If the target platform is unspecified and Jira is mentioned, prefer Jira Wiki Markup or provide both.