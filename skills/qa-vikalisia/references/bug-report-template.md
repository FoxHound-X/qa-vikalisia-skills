# BUG: Deduct Point triggers Voucher Claim notification instead of Deduct Point

## Defect Summary

| Field | Value |
|---|---|
| Report Type | Bug |
| Component | Where You Test |
| Severity | Major, Minor |
| Priority | High, medium, or Low |
| Report Date | dd-mm-yyyy |

| Platform | Environment | Version / Build |
|---|---|---|
| Web Portal (Merchant) | Staging | Link/none |
| Android App | Staging | Version/none |
| iOS App | Staging | Version/none
---

## Preconditions

1. Member account logged in on Android or iOS client with push notification permissions enabled.
2. Member account has sufficient active points balance (balance > deduct amount).
3. Merchant account authenticated with permission to access Point Management.

---

## Steps to Reproduce

1. Open Merchant Web Portal: `https://jeevawasa.omnihotelier.net/inject/point`.
2. Search and select target member (`user_id: 884920`).
3. Select transaction action **Deduct Point**.
4. Enter point amount: `50`.
5. Enter transaction note: `Testing deduct notification`.
6. Submit and confirm the deduction.
7. Observe push notification and notification center on the member mobile device.
8. Tap the received notification to verify deep link target.

---

## Actual Result

- Push notification title: `"Voucher Claim"`
- Push notification body: `"Voucher successfully claimed."`
- Deep link behavior: Redirects to **My Voucher** page.
- Database state: Points deducted correctly in database (balance changed from `500` to `450`), but wrong notification event triggered.

---

## Expected Result

- Push notification title: `"Deduct Point"`
- Push notification body: `"50 points deducted by Merchant Jeevawasa. Remaining balance: 450 points."`
- Deep link behavior: Redirects to **Points History / Transaction Details** page.

---

## Technical Context

Suspected root cause: Event routing mismatch on point deduction endpoint. The deduction handler triggers `VOUCHER_CLAIM_EVENT` instead of `POINT_DEDUCTED_EVENT`.

### Sample Payload (FCM / APNs)

```json
{
  "to": "device_token",
  "data": {
    "type": "VOUCHER_CLAIM",
    "transaction_id": "TX-DED-20261101-001",
    "amount": 50
  }
}
Attachments
- web_merchant_deduct_confirmation.png
- mobile_incorrect_notification_receipt.png
- mobile_deeplink_redirect_voucher.mp4