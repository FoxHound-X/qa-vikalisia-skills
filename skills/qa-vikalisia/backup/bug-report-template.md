# Bug Report Reference Template

Standard QA bug report format for Jira, GitHub Issues, GitLab, and internal QA documentation.

---

## 1. Blank Template

Copy this template for each new defect. Remove fields that are genuinely irrelevant, and mark unknown information as `Not provided` or `Not verified` rather than guessing.

# [BUG] [Component/Module]: [Brief summary of failure]

## Defect Summary

| Field | Value |
|---|---|
| Report Type | Bug |
| Bug ID / Ticket URL | [ID or link, if available] |
| Component | [Feature / Module / Service] |
| Reporter | [Name or team, if available] |
| Severity | [Blocker / Critical / Major / Minor / Trivial / Unassessed] |
| Priority | [Highest / High / Medium / Low / Unassessed] |
| Status | [Open / In Progress / Fixed / Retest / Closed, or project-specific status] |
| Report Date | [YYYY-MM-DD] |
| Related Test Case (Qase) | [Link Required] |


## Environment

| Field | Value |
|---|---|
| Platform | [Web / Android / iOS / API / Other] |
| Environment | [Staging] |
| Version / Build | [Version and build number] |
| Browser / Device | [Browser and version, or device model and OS] |
| Account / Role | [Test account identifier or role; do not include credentials] |

## Description

[Describe the observed defect clearly and objectively.]

## Preconditions

- [Required account state, permissions, data, or setup before reproducing]

## Steps to Reproduce

1. [First action]
2. [Second action]
3. [Continue until the defect occurs]

## Actual Result

[What actually happened. Include visible behavior and relevant system response.]

## Expected Result

[What should have happened according to the requirement, design, or accepted behavior.]


## Impact Assessment

- **Functional impact:** [What feature or workflow is affected]
- **Affected users / scope:** [Specific roles, users, platforms, or estimated scope; state if unknown]
- **Business impact:** [Customer, operational, financial, compliance, or other impact]
- **Data integrity impact:** [Whether data is missing, incorrect, duplicated, or unaffected]
- **Release impact:** [Whether the defect blocks release or affects acceptance criteria]


## Attachments / Evidence

| File / Link | Description |
|---|---|
| [filename or URL] | [What the evidence demonstrates] |

## Additional Notes

[Any relevant context not captured above.]


## 2. Field Definitions and Guidelines

### Severity vs. Priority

Severity describes the impact and seriousness of the defect. Priority describes how urgently the team should address it. Assess them independently according to the team's standards.

**Severity examples (guidance only):**

- **Blocker:** Testing or a critical business workflow cannot continue; no reasonable workaround exists.
- **Critical:** A major feature or essential workflow is unusable, or there is severe data/security impact.
- **Major:** Important functionality is broken, but the system or workflow may still be usable.
- **Minor:** A limited issue with a small functional impact.
- **Trivial:** Cosmetic or low-impact issue, such as a minor visual inconsistency.
- **Unassessed:** There is not enough information to determine severity yet.

**Priority examples (guidance only):**

- **Highest:** Immediate action is required, for example due to a production outage or severe ongoing impact.
- **High:** Should be addressed urgently in the current release or sprint.
- **Medium:** Should be scheduled in normal prioritization.
- **Low:** Can be addressed later when capacity allows.
- **Unassessed:** Priority has not yet been agreed.

Do not automatically map a severity value to a priority value. Follow the team's triage process.

### Writing Reproduction Steps

- Number the steps in the order a tester performs them.
- Include relevant navigation, input values, account role, and preconditions.
- Make the steps specific enough for another tester to repeat without guessing.
- Keep actual and expected results separate and observable.

### Evidence and Root Cause

- Separate confirmed observations from hypotheses.
- Never present a suspected root cause as confirmed without supporting evidence.
- Include timestamps, request/correlation IDs, sanitized logs, and relevant response codes when available.
- If evidence is unavailable, state that it was not captured or was not provided.
- Redact secrets and personal data that are not necessary to diagnose the defect.

### Reproducibility and Impact

- Record attempts and outcomes when known.
- Identify affected environments, platforms, roles, and versions based on evidence.
- Do not claim that all users or platforms are affected unless verified.
- State whether a workaround is known; do not invent one.

### Retest and Regression

- Do not mark a defect as retested or fixed unless verification actually occurred.
- Distinguish a retest of the reported defect from regression testing of related functionality.
- If verification has not happened, use `Not performed`.
- Link the relevant test run or attach evidence when available.
