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

---

## 3. Concrete Example (Standard Markdown)

# [BUG] [Checkout]: Payment fails with 500 error when applying expired coupon code

## Defect Summary

| Field | Value |
|---|---|
| Report Type | Bug |
| Bug ID / Ticket URL | PROJ-1042 |
| Component | Checkout / Payment Service |
| Reporter | QA Vikalisia |
| Severity | Critical |
| Priority | High |
| Status | Open |
| Report Date | 2026-11-01 |
| Related Test Case (Qase) | https://app.qase.io/case/PROJ-88 |

## Environment

| Field | Value |
|---|---|
| Platform | Web |
| Environment | Staging (v2.14.0-rc1) |
| Version / Build | Build #412 |
| Browser / Device | Chrome 130.0 / macOS Sonoma |
| Account / Role | Buyer test account (`buyer_test_01@example.com`) |

## Description

When a user attempts to complete checkout after applying an expired coupon code (`EXPIRED50`), the checkout API crashes with HTTP 500 Internal Server Error instead of validating the coupon and displaying a user-friendly error message. The user is stuck on the checkout screen and order placement fails.

## Preconditions

- User is logged in with active buyer account.
- Shopping cart contains at least 1 item.
- An expired coupon code exists in staging DB (`EXPIRED50`, expired on 2026-10-15).

## Steps to Reproduce

1. Navigate to `/cart` and click **Proceed to Checkout**.
2. On checkout page, expand **Discount Code / Coupon** section.
3. Enter `EXPIRED50` in coupon input field and click **Apply**.
4. Observe green badge "Coupon Applied" incorrectly appears.
5. Select payment method (Credit Card) and click **Place Order**.

## Actual Result

Page shows infinite spinner for 5 seconds, followed by toast notification: `"Something went wrong. Please try again."`
Network tab shows:
- `POST /api/v1/orders/checkout` returns `500 Internal Server Error`.
- Response body: `{"error": "NullPointerException: coupon.getDiscountRule() is null"}`.

## Expected Result

Step 4 should fail immediately with validation error: `"Coupon code has expired."`
Checkout button should remain active with original order total, allowing user to remove invalid coupon and proceed without 500 server crash.

## Impact Assessment

- **Functional impact:** Blocks users with expired coupons from completing order checkout.
- **Affected users / scope:** All web buyer users entering expired promotional codes.
- **Business impact:** Direct drop-off at final payment step, potential revenue loss.
- **Data integrity impact:** No orphaned orders created in DB; cart state remains unchanged.
- **Release impact:** Blocks release of checkout v2.14.0.

## Attachments / Evidence

| File / Link | Description |
|---|---|
| `checkout_500_error_console.png` | Screenshot of browser console and network response |
| `checkout_reproduce_recording.mp4` | Screen recording of reproduction steps |

## Additional Notes

- Issue does not occur when valid coupon code or no coupon code is applied.
- Backend service log correlation ID: `req-b84f2910-449e`.

---

## 4. Jira Wiki Markup Template (Alternative for Jira Text / Classic Mode)

*Use this format if your Jira editor uses classic Jira Text Formatting / Wiki Markup instead of Markdown.*

```jira
h1. [BUG] [Component]: Brief summary of failure

h2. Defect Summary
||Field||Value||
|Report Type|Bug|
|Bug ID / Ticket URL|[ID or link]|
|Component|[Feature / Module]|
|Reporter|[Name or team]|
|Severity|[Blocker / Critical / Major / Minor]|
|Priority|[Highest / High / Medium / Low]|
|Status|Open|
|Report Date|[YYYY-MM-DD]|
|Related Test Case (Qase)|[Link Required]|

h2. Environment
||Field||Value||
|Platform|[Web / Android / iOS / API]|
|Environment|[Staging]|
|Version / Build|[Version and build]|
|Browser / Device|[Browser and OS]|
|Account / Role|[Test account role]|

h2. Description
[Describe defect clearly]

h2. Preconditions
* [Precondition 1]
* [Precondition 2]

h2. Steps to Reproduce
# [First action]
# [Second action]
# [Third action]

h2. Actual Result
[Observed system behavior]

h2. Expected Result
[Expected system behavior]

h2. Impact Assessment
* *Functional impact:* [Affected workflow]
* *Affected users / scope:* [Affected scope]
* *Business impact:* [Business impact]
* *Data integrity impact:* [Data integrity impact]
* *Release impact:* [Release blocker assessment]

h2. Attachments / Evidence
||File / Link||Description||
|[filename or URL]|[What evidence demonstrates]|

h2. Additional Notes
[Logs or extra context]
```

### Concrete Jira Wiki Markup Example:

```jira
h1. [BUG] [Checkout]: Payment fails with 500 error when applying expired coupon code

h2. Defect Summary
||Field||Value||
|Report Type|Bug|
|Bug ID / Ticket URL|PROJ-1042|
|Component|Checkout / Payment Service|
|Reporter|QA Vikalisia|
|Severity|Critical|
|Priority|High|
|Status|Open|
|Report Date|2026-11-01|
|Related Test Case (Qase)|https://app.qase.io/case/PROJ-88|

h2. Environment
||Field||Value||
|Platform|Web|
|Environment|Staging (v2.14.0-rc1)|
|Version / Build|Build #412|
|Browser / Device|Chrome 130.0 / macOS Sonoma|
|Account / Role|Buyer test account (buyer_test_01@example.com)|

h2. Description
When a user attempts to complete checkout after applying an expired coupon code (EXPIRED50), the checkout API crashes with HTTP 500 Internal Server Error instead of validating the coupon and displaying a user-friendly error message. The user is stuck on the checkout screen and order placement fails.

h2. Preconditions
* User is logged in with active buyer account.
* Shopping cart contains at least 1 item.
* An expired coupon code exists in staging DB (EXPIRED50, expired on 2026-10-15).

h2. Steps to Reproduce
# Navigate to /cart and click *Proceed to Checkout*.
# On checkout page, expand *Discount Code / Coupon* section.
# Enter EXPIRED50 in coupon input field and click *Apply*.
# Observe green badge "Coupon Applied" incorrectly appears.
# Select payment method (Credit Card) and click *Place Order*.

h2. Actual Result
Page shows infinite spinner for 5 seconds, followed by toast notification: "Something went wrong. Please try again."
Network tab shows:
* POST /api/v1/orders/checkout returns 500 Internal Server Error.
* Response body:
{code:json}
{"error": "NullPointerException: coupon.getDiscountRule() is null"}
{code}

h2. Expected Result
Step 4 should fail immediately with validation error: "Coupon code has expired."
Checkout button should remain active with original order total, allowing user to remove invalid coupon and proceed without 500 server crash.

h2. Impact Assessment
* *Functional impact:* Blocks users with expired coupons from completing order checkout.
* *Affected users / scope:* All web buyer users entering expired promotional codes.
* *Business impact:* Direct drop-off at final payment step, potential revenue loss.
* *Data integrity impact:* No orphaned orders created in DB; cart state remains unchanged.
* *Release impact:* Blocks release of checkout v2.14.0.

h2. Attachments / Evidence
||File / Link||Description||
|checkout_500_error_console.png|Screenshot of browser console and network response|
|checkout_reproduce_recording.mp4|Screen recording of reproduction steps|

h2. Additional Notes
* Issue does not occur when valid coupon code or no coupon code is applied.
* Backend service log correlation ID: req-b84f2910-449e.
```


