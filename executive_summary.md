# Executive summary: InvoiceMatch launch decision

**For:** Diana (CFO), Silverbrook Financial steering group · **From:** Umashanker, FDE lead · **November 2026**

## Recommendation: 🟡 LAUNCH WITH CONDITIONS

Start a **12-week pilot**, beginning in **shadow mode** (no automatic approvals), and switch on auto-approval only when three conditions are met. The working product, measured results, and stakeholder feedback support this. Scaling now without evidence on real invoices would not.

## The problem
Six AP specialists spend about **790 hours a month** checking PO-backed invoices by hand, all of their capacity, with 15% more volume coming. Last year **$210,000** leaked through duplicate payments and overpayments.

## What we built
**InvoiceMatch**: Claude reads each invoice; ten written rules check it against the PO and contract; the existing approval limits decide who approves. *AI reads; rules decide; people approve.* It is working today: [live product](https://invoicematch.onrender.com).

## Evidence

| Measure | Result |
|---|---|
| Field accuracy (40 sample invoices, including 12 unseen layouts) | **100%** |
| Correct decisions | **40 / 40** |
| Wrong automatic approvals | **0** |
| AI cost and speed per invoice | About **$0.0002**, about **2 seconds** |
| Business case (target) | **57% less manual effort**, about **$313,000 net a year**, payback in about **7 months** |

## Why not "ready to launch"
- Accuracy is proven on **sample** invoices, not yet on Silverbrook's real vendor layouts (Compliance objection F-2).
- The ERP connection, intake, and single sign-on are **not built yet**.
- The AP team has **real job concerns** (F-6) that must be answered first.

## Why not "not ready"
The core workflow works end to end, safety is measured (0 wrong approvals), the risks are known with owners, and shadow mode lets us prove it **with no risk to payments**.

## Conditions for switching on auto-approval
1. **C-1:** InfoSec review of egress, gateway, and secrets passed.
2. **C-2:** Shadow mode on real invoices: ≥ 97% field accuracy, **0** wrong would-be approvals, ≥ 98% agreement with human decisions for 2 weeks.
3. **C-3:** Outage and wrong-approval drills passed using only the runbook.

## Decisions needed today
1. Approve the 12-week pilot with 10 vendors (D-1, D-2).
2. Publish the CFO statement on jobs (D-3).
3. Fund the top backlog item, the **ERP connector (B-1)**.

Details: [demo script](demo_script.md) · [feedback log](feedback_log.md) · [productization plan](productization_plan.md)
