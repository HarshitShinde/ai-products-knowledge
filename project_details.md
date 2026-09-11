# iMatchX — AI-Powered 3-Way Match Exception Triage

## 1. Overview

| | |
|---|---|
| **Product name (proposed)** | iMatchX |
| **Alternate name options** | iReconX, iClearX, iTriageX, MatchIQ |
| **Parent ecosystem** | Intellect Design Arena — sits at the boundary of iCPX (Corporate Procurement eXchange) and iAPX (Accounts Payable eXchange) |
| **Organization** | Intellect Design Arena, Mumbai |
| **Stage** | AI Design Process — Stage 1 (identifying target intelligence: performance metrics + scope) |
| **Document owner** | Harshit Shinde |
| **Last updated** | 2026-09-11 |

**One-line pitch:** iMatchX uses AI to automatically explain and resolve routine PO–GRN–Invoice mismatches, so Accounts Payable teams only spend time on the exceptions that genuinely need a human.

---

## 2. Problem Statement

When a company buys something, three documents get generated:

1. **PO (Purchase Order)** — what was ordered, at what price.
2. **GRN (Goods Receipt Note)** — what was actually received.
3. **Invoice** — what the supplier is billing for.

Before payment, Accounts Payable checks that all three agree on item, quantity, and price — the **3-way match**. In practice, they rarely match perfectly: partial deliveries, price/tax variances, late GRNs, mismatched item codes, and duplicate invoices are all common.

Today, every mismatch — regardless of how trivial or how serious — gets routed to a human AP clerk, who must manually open all three documents, diagnose the reason for the mismatch, and decide whether to approve or reject the invoice. In a mid-size enterprise this happens for thousands of invoices a month. The process is:

- **Slow** — payments get delayed, hurting supplier relationships and forfeiting early-payment discounts.
- **Repetitive** — most mismatches fall into a handful of recurring, low-risk patterns.
- **Inconsistent** — decisions depend on which clerk reviews the case and how much time they have.
- **Risky in the wrong direction** — genuinely risky cases (e.g., duplicate or fraudulent invoices) get the same shallow attention as trivial rounding differences, because volume forces speed over scrutiny.

**Problem statement:** *AP teams lack an automated way to diagnose why a PO–GRN–Invoice match failed and to safely clear the low-risk majority of exceptions, causing payment delays and wasted manual effort on routine cases.*

---

## 3. Performance Metrics

Each metric is anchored to the existing human baseline (what an AP clerk currently does), per the AI Design Process Stage 1 principle of grounding targets in a known reference performance.

| Metric | Definition | Why it matters | V1 directional target |
|---|---|---|---|
| **Auto-resolution rate** | % of mismatched invoices the AI classifies and resolves without human involvement | Core efficiency gain | 40–50% |
| **Auto-resolution accuracy** | Of AI-resolved cases, % matching what the human clerk would have decided (via sampling/audit) | Trust and correctness | ≥ 98% |
| **False-approve rate** | % of AI auto-approvals that were actually wrong (e.g., approved a duplicate invoice) | Financial/fraud risk control — the metric finance will care about most | Near-zero (< 0.5%) |
| **Time-to-resolution** | Avg. time from mismatch flagged → resolved, AI-assisted vs. current manual process | Business ROI | Reduce from days to hours |
| **Reason-classification accuracy** | For cases still routed to a human, does the AI correctly identify the mismatch reason (price variance, quantity variance, missing GRN, duplicate, etc.)? | Speeds up human review even when it can't auto-resolve | High agreement with clerk's own tagging |

**Note on precision:** These are first-pass, directional targets, not final commitments. Per Stage 1 guidance, it's acceptable to stay generic here and revisit once real historical mismatch data has been reviewed and the later design stages (data gathering, build, evaluation) have been iterated at least once.

---

## 4. Scope

### In scope (V1)
- **Transaction type:** standard PO-based purchases only (not services, not capital expenditure).
- **Data:** one geography / business unit's historical transaction data to start, to avoid currency, tax, and approval-policy variance.
- **Mismatch types covered:** the four most common — price variance, quantity variance, missing/late GRN, duplicate invoice.
- **AI output:** classification of the mismatch reason + a recommendation (auto-approve / auto-reject / route to human with explanation).
- **Human oversight:** a human retains final sign-off even on "auto-resolved" cases in V1 (approve-and-notify model, not approve-and-forget).

### Out of scope (V1)
- Non-PO / free-text invoices.
- Cross-currency or cross-entity invoices (adds FX and consolidation complexity).
- Fully autonomous payment release without human notification.
- Government procurement (iGPX) — this is specifically an iCPX/iAPX (corporate procurement) boundary problem.

### Expansion path (post-V1)
- Widen to services/capex invoices.
- Add more mismatch types beyond the initial four.
- Increase auto-resolution rate and reduce the mandatory human-notify step as accuracy is proven across audit cycles.
- Extend to cross-currency/cross-entity scenarios once the core model is validated.

---

## 5. Anything Else of Worth

### Why this problem was chosen (selection rationale)
- **High volume, repetitive** — clear, measurable ROI in time and cost.
- **Existing human baseline** — AP clerks already do this today, giving a natural yardstick for AI performance.
- **Bounded, well-defined task** — three documents, a fixed set of fields to compare — good fit for a first, limited product rather than an open-ended workflow.
- **Fits existing architecture** — iCPX/iAPX are already composed of 111 APIs / 17 microservices; iMatchX can be scoped as one new microservice rather than a new platform.

### Data requirements
- Historical PO, GRN, and Invoice records (ideally 12+ months) with the eventual human decision (approved/rejected) and reason, to serve as ground truth for both training and baseline comparison.
- Access needs to be confirmed with whichever business unit's iCPX/iAPX deployment is used as the pilot source.

### Key risks / open questions
- **False-approve risk** is the biggest trust barrier — needs a conservative rollout (shadow mode → notify-only → limited auto-approve) rather than going live with auto-approval immediately.
- **Data availability** — have not yet confirmed access to real historical mismatch logs; this is the first blocker to resolve before Stage 2 (data gathering).
- **Naming/positioning** — since the feature spans iCPX (PO) and iAPX (invoice), product placement/ownership within the org needs to be settled early.
- **Change management** — AP clerks' workflow changes; needs buy-in from finance/AP stakeholders, not just a technical build.

### Rollout approach (suggested)
1. **Shadow mode** — AI runs alongside existing manual process, decisions logged but not acted on; measure accuracy against real clerk decisions.
2. **Notify-only mode** — AI recommendations shown to clerks to speed up their review, but clerk still makes the final call.
3. **Limited auto-approve** — only for the lowest-risk mismatch category (e.g., small rounding/tax variances) with a human notification and audit trail.
4. **Expand scope** — add more mismatch types and raise auto-approve thresholds as trust and accuracy are demonstrated.

### Stakeholders to involve
- AP/Finance operations team (source of ground truth and eventual users).
- iCPX and iAPX product owners (architecture/integration alignment).
- Compliance/audit (sign-off on auto-approval thresholds and audit trail requirements).

### Success criteria for moving past V1
- Auto-resolution rate and accuracy targets consistently met over a defined pilot period (e.g., one full quarter) with false-approve rate held near zero, validated by a compliance/audit review.
