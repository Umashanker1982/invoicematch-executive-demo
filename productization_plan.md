# Productization plan: InvoiceMatch release 1

How InvoiceMatch moves from a working prototype to a supported product, based on the decisions and feedback in [feedback_log.md](feedback_log.md) (IDs such as F-5, D-1, and C-2 refer to that log).

**Frameworks used:** Google **HEART** for adoption metrics, **Prosci ADKAR** for onboarding, and an **Aha! product launch checklist** for launch readiness.

## 1. Launch scope

| In release 1 | Not in release 1 (later) |
|---|---|
| PO-backed digital USD invoices (about 76% of volume) | Scanned or paper invoices (release 2) |
| AI reading, 10 matching rules, approval routing, review queue, audit log | Non-PO invoices, credit notes (release 3) |
| ERP **approval status** update (the only write) | Payments, PO or vendor changes (never: out of the product's boundary) |
| 10 pilot vendors, then all vendors (D-2) | Other currencies (release 2) |

## 2. Release criteria

| Gate | Criteria | Evidence |
|---|---|---|
| **Pilot start** (week 1) | Security review passed (C-1); CFO statement published (D-3); training complete for the pilot team | Signed review; training records |
| **Turn on auto-approval** (week 7) | C-2: shadow mode on real invoices with ≥ 97% field accuracy, **0** wrong would-be approvals, ≥ 98% agreement with human decisions for 2 weeks; Compliance sign-off (D-4) | Shadow-mode report |
| **Full rollout** (week 12) | C-3 drills passed; 4 weeks of auto-approval with 0 wrong approvals; HEART targets below on track | Drill records; scorecard |

## 3. Target users

| User | Need | What they use |
|---|---|---|
| **AP specialists** (primary, 6 people) | Less routine checking; clear exceptions | Review queue |
| **AP Manager** | Team capacity, control, a backlog owner | Queue, scorecard |
| **Approvers** (Finance Controller, CFO) | Approve within limits with evidence | Approval screen |
| **Internal Audit, Compliance** | Evidence on demand | Read-only audit role (B-4) |
| **Procurement** | Fewer one-off emails; vendor price trends | Monthly report (B-5) |

## 4. Onboarding (Prosci ADKAR)

| ADKAR stage | Action |
|---|---|
| **Awareness** | CFO and AP Manager explain why: 790 hours a month, overtime, $210,000 leakage |
| **Desire** | CFO statement on jobs (D-3); show the team's own invoices being handled |
| **Knowledge** | 45-minute role-based training; sandbox with sample invoices |
| **Ability** | Two weeks in shadow mode per person; one floor champion per team |
| **Reinforcement** | Weekly "you said, we did" notes; every correction becomes a test case |

## 5. Adoption metrics (Google HEART)

| HEART | Goal | Signal | Metric | Target by week 12 |
|---|---|---|---|---|
| **Happiness** | Users find it helpful | Survey | AP satisfaction (1–5) | ≥ 4.2 |
| **Engagement** | Work happens in the tool | Queue usage | Exceptions resolved in the queue, not by email | ≥ 80% |
| **Adoption** | All eligible users active | Weekly active users | Specialists with ≥ 20 invoices a week | 6 of 6 |
| **Retention** | No return to manual checking | Shadow work | Auto-approved invoices re-checked by hand | ≤ 5% |
| **Task success** | Fast, correct decisions | Audit log | Median exception resolution time; wrong auto-approvals | ≤ 1 day; **0** |

**Business outcome:** manual AP hours a month, from 790 toward 342 by month 6.

## 6. Support

| Level | Who | Handles |
|---|---|---|
| L1 | Customer IT service desk | Access, "where is my invoice", how-to |
| L2 | AP platform team (with the runbook) | Alerts, rollbacks, safety switch, key rotation |
| L3 | FDE / vendor engineering | Code, rules, and model issues (hypercare, then a support agreement) |

Response targets: Sev 1 within 15 minutes, Sev 2 within 4 hours. Hypercare lasts weeks 7–10, with the FDE team on call.

## 7. Operations

- **Monitoring:** error rate, AI latency and cost, fallback rate, exception rate, nightly audit-chain check.
- **Safety switch:** `AUTO_APPROVE_LIMIT=0` sends every invoice to people within minutes.
- **Release process:** every change passes the tests, the regression gate, and the safety gate (0 wrong auto-approvals); rule or limit changes need Compliance sign-off (F-10).
- **Runbook:** incident playbooks for gateway down, ERP down, wrong approval, exception spike, audit chain broken, secret exposed.

## 8. Risks, dependencies, and mitigations

| Risk or dependency | Impact | Mitigation | Owner |
|---|---|---|---|
| Accuracy on real vendor layouts is unproven | Wrong reads, low trust | Shadow mode first (C-2); add real layouts to the test set | FDE lead |
| Staff fear for jobs (F-6) | Low adoption, workarounds | CFO statement (D-3); champions; people keep every exception | CFO, AP Manager |
| **Dependency:** ERP API access | No status write, double entry | ERP lead commits a slot by week 4 | ERP lead |
| **Dependency:** InfoSec review (F-3) | Pilot cannot start | Review booked for week 2 | InfoSec |
| AI gateway outage | Slower processing | Rules fallback; people review; outage drill (C-3) | Platform lead |
| Prompt injection (F-4) | A misread invoice | AI cannot approve; more injection test cases (B-6) | FDE team |

## 9. Prioritized next backlog

Ranked by value and by what blocks the launch.

| Rank | Item | Why now | From | Effort |
|---|---|---|---|---|
| **B-1** | Real ERP connector (read POs, vendors, contracts; write approval status) | Blocks the pilot; removes double entry | D-2 | Large |
| **B-2** | Contract and PO links on each held invoice | Top request from AP; quick trust win | F-5 | Small |
| **B-3** | Company single sign-on with roles | Needed for real users and audit | C-1 | Medium |
| **B-4** | Read-only audit role and CSV export | Audit can sample without IT | F-8 | Small |
| **B-5** | Monthly price-drift report for Procurement | Turns exceptions into vendor savings | F-7 | Small |
| **B-6** | 10 more prompt-injection test cases | Closes a security question | F-4 | Small |
| **B-7** | Mailbox and e-invoice intake | Needed for full volume | D-2 | Medium |
| **B-8** | Bank-change verification workflow | Highest fraud value after launch | Roadmap | Medium |

## 10. Launch checklist (based on the Aha! launch checklist)

| Area | Item | Owner | Status |
|---|---|---|---|
| Product | Release 1 scope frozen; release criteria agreed | FDE lead | ✅ Agreed in workshop |
| Security | InfoSec review signed (C-1) | Kevin | ⏳ Week 3 |
| Readiness | Training complete; champions named | Priya | ⏳ Week 1 |
| Communication | CFO statement published (D-3) | Diana | ⏳ Week 1 |
| Support | L1/L2 trained; runbook handed over | Platform lead | ⏳ Week 6 |
| Operations | Dashboards and alerts live; drills passed (C-3) | Platform lead | ⏳ Week 10 |
| Measurement | HEART scorecard live and shared every 2 weeks | FDE lead | ⏳ Week 2 |
