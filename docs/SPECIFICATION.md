# Requirements Specification: Timber Management System

**Author:** Mohamed Islam Zalat · **Role:** Business Analyst and Product Owner

> [!NOTE]
> This is the public summary of the specification I wrote (about 13 sections). It was the single source of truth for AI-assisted development in six phases. Real business data, customer names, financial figures and real-data examples have been removed.

**Contents:** [1. Business Context](#1-business-context) · [2. Users and Roles](#2-users-and-roles) · [3. Business Rules](#3-business-rules) · [4. Functional Requirements](#4-functional-requirements-by-module) · [5. Data Model](#5-data-model-overview) · [6. Data Management](#6-data-management) · [7. Non-Functional](#7-non-functional-requirements) · [8. Phases](#8-delivery-phases) · [9. Acceptance Criteria](#9-acceptance-criteria-as-defined)

---

## 1. Business Context

- A timber trading business buys sawn wood from suppliers, stores it in a yard, and sells to customers, mostly on credit and sometimes for cash.
- Wood is traded by size and by cubic metre. Each item is defined by category, length, width and thickness. Lengths can be non-standard (average lengths of a lot).
- Before this system, operations ran on paper notebooks and three Excel versions. The Excel workbook was the source of truth for business logic and initial data.

---

## 2. Users and Roles

| Role | Access |
|---|---|
| Owner | Everything, including users, settings and reopening closed days |
| Accountant | Everything except users, settings and reopening closed days |
| Sales | Create and confirm sales invoices and receipts; read customers, products and stock; no access to costs, purchases, suppliers, cash or profit |
| Viewer | Read-only, same restrictions as Sales |

Accounts are created by the owner only. There is no open sign-up.

---

## 3. Business Rules

| ID | Rule |
|---|---|
| BR-01 | Volume (m³) = length × width × thickness × quantity (all in metres). Price is per m³. Line amount = volume × price. |
| BR-02 | Each invoice keeps both the calculated amount and the agreed amount. The difference is a discount or surcharge and must be visible in reports. |
| BR-03 | An item is defined by category, length, width and thickness. Non-standard lengths are supported; a new size is created when first used on a confirmed invoice. |
| BR-04 | A cash sale produces exactly one receipt and one cash entry. A credit sale raises the customer balance by the agreed amount. |
| BR-05 | Balances (customers, suppliers, cash, stock) come from recorded movements, updated in the same transaction as the movement itself. |
| BR-06 | Important records are never deleted. Cancellation creates reversal entries, requires a reason and permission, and is logged. |
| BR-07 | Warnings for: stock going negative, agreed amount differing from calculated by more than a threshold (default 5%), and customers exceeding their credit limit. |
| BR-08 | The last price used for a customer and size is suggested on new invoices. |
| BR-09 | A closed cash day is locked. Only the owner can reopen it, with a logged reason. |
| BR-10 | Customer and supplier names are unique. Invoice numbers and customer codes use different prefixes so they cannot be confused. |

---

## 4. Functional Requirements by Module

- **Sales:** fast invoice entry, live volume and amount preview, cash and credit, confirmation, cancellation, printing, customer receipts, customer balance visible once the customer is chosen.
- **Purchases and suppliers:** purchase invoices entered at length level, supplier accounts, supplier payments.
- **Inventory:** stock by size, stock card per size with every movement, manual adjustments, periodic stocktake.
- **Finance:** customer and supplier statements, opening balances, expenses, rental income, loans and repayments, daily cash book with counted-versus-system closing.
- **Control:** audit log of every action, data-quality page, user and role management, settings.
- **Reports:** dashboard (cash, receivables, payables, stock value, monthly sales, aging, cash flow, discounts) and detailed reports with date filters, export and print.

---

## 5. Data Model Overview

Twenty collections grouped by purpose:

- **Master data:** users, settings, counters, customers, suppliers, wood categories, expense categories, products.
- **Transactions:** sales invoices, purchase invoices, customer receipts, supplier payments, expenses, rental income, loans, loan repayments, stocktakes.
- **Ledgers (append-only):** cash ledger, stock movements, audit log.
- **Control and helpers:** cash closes, product costs (restricted), customer last prices.

Design conventions: money stored as integer piasters, volume as integer units of 0.0001 m³, every record carries created and updated metadata, and running totals are updated in the same transaction as the ledger row.

---

## 6. Data Management

- **Excel import:** owner-only wizard with dry-run preview, idempotent writes with deterministic ids, resumable batches, and a reconciliation report comparing system values with the workbook's own totals. Differences must be explained or flagged, never hidden.
- **Export:** every list and report exports to CSV and XLSX. A full export includes analysis-ready fact and dimension tables and a data dictionary for use in Power BI, SQL or Python.
- **Backup:** full JSON backup and restore (owner only).

---

## 7. Non-Functional Requirements

- **Security:** deny by default; role-based rules on every collection; ledgers are create-only; cost, purchase, supplier and cash data restricted to owner and accountant.
- **Reliability:** every multi-record change is a single transaction; clear error messages with retry; protection against double submission.
- **Usability:** Arabic, right-to-left, mobile-first, large touch targets, draft autosave, thousand separators.
- **Technology constraints:** a stack that runs and deploys from Google AI Studio Build mode, with Firebase (Authentication and Cloud Firestore) as the backend.

---

## 8. Delivery Phases

| Phase | Scope |
|---|---|
| 1 | Foundation: layout, authentication and roles, security rules, settings, customers, suppliers, sizes, audit log |
| 2 | Transactions: sales, receipts, purchases, supplier payments, cancellation, ledgers, verification tool |
| 3 | Excel import with dry-run and reconciliation |
| 4 | Operations: inventory, stocktake, treasury, daily close, expenses, rent, loans, printing |
| 5 | Insight: dashboard, reports, data-quality page, full export |
| 6 | Hardening: role tests, performance, installable app, documentation |

Each phase was approved before the next one started.

---

## 9. Acceptance Criteria (as defined)

1. The application runs in the preview and can be published; the first run creates the owner account.
2. After import, reconciliation shows no unexplained differences.
3. A cash sale creates one cash entry and one receipt with no change to the customer balance; a credit sale raises the balance by the agreed amount.
4. Selling a non-standard length reduces the stock of that exact size.
5. Cancelling an invoice restores stock, cash and balance through reversal entries, with nothing deleted.
6. A Sales user cannot read cost, profit, supplier, purchase or cash data.
7. Ledger records cannot be edited or deleted from the client.
8. Reports export to CSV and XLSX with Arabic text intact, and the full export contains the fact and dimension tables.
9. The verification tool recomputes balances, stock and cash from the ledgers and reports zero mismatches.

These are requirements I defined. They are not a record of test results.

---

[Back to project README](../README.md)
