# Executive demo script (7 minutes)

**Product:** InvoiceMatch, AI-assisted invoice-to-PO matching · **Customer:** Silverbrook Financial (fictional) · **Presenter:** Umashanker (FDE lead)
**Working product used in the demo:** https://invoicematch.onrender.com · **Slides:** [demo_deck.pdf](demo_deck.pdf)

**Audience:** Diana (CFO, decision owner), Marcus (Compliance), Kevin (InfoSec), Priya (AP Manager), Lena (Procurement), Grace (Internal Audit).
**Format:** a 7-minute demo, then a 20-minute productization workshop (see [feedback_log.md](feedback_log.md)).

**Structure.** Based on the **SAFe System Demo** (show working, integrated software to stakeholders and get feedback) and the **Scrum Sprint Review** (inspect the outcome; stakeholders and the team decide what to do next). The demo is short so the workshop has time for decisions.

## Before the meeting
- Open the live site **5 minutes early**: free hosting needs about 50 seconds to wake up.
- Select **"Claude via SharedLLM"** (top right) and press **Reset demo**.
- Backup if the network fails: the screenshots in [demo_deck.pdf](demo_deck.pdf).

## The script

| Time | Show | Say |
|---|---|---|
| **0:00–1:00** | Slide 2: *The problem* | "Six AP specialists spend about **790 hours a month** checking PO-backed invoices by hand. That is all of their capacity, and volume grows 15% next year. Last year **$210,000** leaked through duplicates and overpayments." |
| **1:00–1:45** | Slide 3: *Users, goal, value* | "The users are the AP team and the approvers. The goal: half of invoices with no human touch, and **57% less manual effort**. That is about **$313,000 net a year**, with payback in about 7 months. One principle makes it safe: **AI reads; rules decide; people approve.**" |
| **1:45–3:00** | Live: Quick tour **1. A clean invoice** | "Claude reads it in about 2 seconds for a fraction of a cent. Ten written checks against the PO and contract all pass, so rule A-1 approves it and the audit log records it. **This is the routine work that disappears.**" |
| **3:00–4:00** | Live: **2. Price above contract** | "This invoice charges 14% above the contract. It is not rejected; it goes to a person with the exact line and the difference. Lena, this is the evidence your buyers will see." |
| **4:00–4:45** | Live: **5. A layout rules can't read** | "A new vendor format. Our old rules reader gets 39% of fields on new layouts. Claude got 100%, and 12 of 12 decisions right. That is why we use AI. When reading fails, the invoice goes to a person, never to payment." |
| **4:45–5:30** | Live: **Review queue**, then **Audit log → Tamper test** | "Approval limits are enforced by the system: an AP specialist cannot approve a bank-detail change. And if anyone edits an old record, the chain breaks. Marcus, Grace: this is your evidence." |
| **5:30–6:30** | Slide 7: *Complete, incomplete, risky, manual* | Walk through the four boxes honestly: "What works today, what isn't built, what could go wrong, and what still depends on people." |
| **6:30–7:00** | Slide 8: *Recommendation* | "Our recommendation is **launch with conditions**: a 12-week pilot in shadow mode, three conditions to meet, then expansion only on evidence. **I'd like your decision on that in the workshop.**" |

## Complete / incomplete / risky / manual (slide 7)

| Status | Items |
|---|---|
| ✅ **Complete** (working in the demo) | AI reading through the course SharedLLM gateway; 10 matching rules; approval routing under the existing limits; review queue with role checks and written reasons; tamper-evident audit log; benchmark and CI gates (100% field accuracy, 40/40 decisions, 0 wrong auto-approvals) |
| 🟡 **Incomplete** (not built yet) | Real ERP integration (simulated today); mailbox and e-invoice intake; company single sign-on (personas in the demo); PDF and scanned invoices; database and write-once audit storage |
| 🔴 **Risky** | Accuracy on *real* vendor layouts is unproven (test set is 40 sample invoices); staff trust and job fears; AI gateway dependency; prompt injection in invoice text |
| ✋ **Still manual** | Every exception and every approval above $10,000; bank-detail verification by phone; contract price updates; the weekly audit sample |

## Likely questions

| Question | Short answer |
|---|---|
| "What if the AI makes a mistake?" | It can only misread, not decide. Values must appear in the invoice, lines must add up to the total, and unclear invoices go to people. The release gate allows **zero** wrong auto-approvals. |
| "Does our data leave our cloud?" | Only invoice text with bank details removed, through the approved gateway. |
| "What does it cost?" | About $0.0002 per invoice for AI; about $45,000 a year all-in, against about $358,000 a year in value. |
| "Will people lose their jobs?" | The goal is to remove overtime and routine checks; people keep every exception. This needs a written commitment (see the feedback log, D-3). |
