# Timber Management System
### Business Analysis & Product Ownership Case Study

**Transforming a real timber trading business from fragmented spreadsheets into an integrated management system.**

<p align="center">
  <a href="https://mohamedzalat412.github.io/Timber-Management-System/">
    <strong>🌐 View Live Portfolio</strong>
  </a>
</p>

---

## 📌 Project Overview

The **Timber Management System** is a business analysis and product ownership case study based on a real, family-run timber trading business.

The business initially relied on separate notebooks and multiple Excel files to manage customers, suppliers, sales, purchases, collections, and inventory.

As operations grew, maintaining accurate records, tracking balances, and connecting daily transactions became increasingly complex.

The objective was to analyze the existing business processes, identify operational challenges, define structured requirements, and guide the development of an integrated web-based management solution.

> This repository contains the portfolio case study website and its documentation. It does not contain the application's source code.

## 🎯 Business Challenges

| Business Area | Challenge |
|---|---|
| Record Management | Customer, supplier, cash, and collection records were scattered across separate files. |
| Transaction History | Editing or deleting old transactions could change balances and stock without preserving history. |
| Pricing | Negotiated prices were not clearly tracked against calculated invoice amounts. |
| Inventory | Checking available stock by timber size required manual record searches. |
| Repeated Data Entry | The same information was entered across multiple spreadsheets. |
| Data Quality | Incorrect entries, unusual discounts, negative stock, and cash differences could go unnoticed. |

## 🔍 Business Analysis Approach

The project followed a structured approach:

1. **Process Analysis** – Understanding the existing workflows and how the business operates.
2. **Problem Identification** – Identifying operational gaps, manual tasks, and data consistency issues.
3. **Requirements Definition** – Translating business needs into requirements, business rules, edge cases, and acceptance criteria.
4. **Solution Design** – Defining workflows, data relationships, access roles, and implementation priorities.
5. **AI-Assisted Development** – Guiding the development process through structured specifications and iterative reviews.
6. **Validation** – Defining test scenarios and comparing migrated Excel balances with the system.

## 🧩 Key Business Decisions

| Decision | Business Value |
|---|---|
| Balances from Ledger Rows | Balances are derived from recorded movements instead of manually entered totals. |
| Reversals, Not Deletions | Original transactions are preserved, with reversal entries used for cancellations. |
| Calculated vs. Agreed Price | Both amounts are stored, making negotiated discounts measurable. |
| Stock by Timber Size | Each distinct timber size has its own stock card and running balance. |
| Integrated Operations | Sales, purchases, inventory, accounts, and cash share connected records. |
| Data Quality Checks | Alerts help identify unusual discounts, negative stock, credit limit issues, cash-close differences, and duplicate names. |

## 🔄 Core Business Workflow

**From Customer Request to Completed Sale**

```text
Customer Request
       ↓
Select Timber Dimensions
       ↓
Calculate Volume
       ↓
Calculate Price
       ↓
Confirm Sale
       ↓
Record Payment
       ↓
Update Stock & Accounts
```

The system supports cash sales, credit sales, and partial payments.

The calculated amount (volume × price per m³) may differ from the final agreed amount after negotiation. Unpaid amounts remain recorded against the customer's account.

## 🖥️ System Features

The running application includes:

- **Management Dashboard** – Cash, receivables, payables, stock, and monthly sales KPIs.
- **Sales Invoices** – Invoice records with payment type, volume, and confirmation status.
- **Inventory Management** – Stock cards for each timber size, with running balances in pieces and cubic meters.
- **Financial Tracking** – Customer and supplier balances based on recorded transactions.
- **Cash Management** – Tracking cash movements and monthly cash inflows and outflows.
- **Reports** – Approximately 18 reports covering financial position, sales by size, and monthly activity.
- **Data Quality Alerts** – Checks for unusual discounts, negative stock, credit limits, and duplicate names.
- **Export & Backup** – Structured data exports suitable for further analysis, plus full backup functionality.

## 👨‍💻 My Role & Responsibilities

My contribution focused on the business and product side of the project.

| Area | Responsibilities |
|---|---|
| Business Analysis | Analyzed real business operations and existing workflows. |
| Requirements Engineering | Defined business needs, rules, edge cases, and acceptance criteria. |
| Process Design | Structured workflows and mapped relationships between business operations. |
| Product Ownership | Organized priorities, phased specifications, and implementation direction. |
| AI-Assisted Development | Guided the AI-assisted build, reviewed generated outputs, and iterated on the solution. |
| Validation | Defined test cases and acceptance criteria; supported validation against real business scenarios. |

## 🤖 AI-Assisted Development

The application code was generated using **Google AI Studio (Gemini)** based on my specifications and iterative guidance.

I did not manually write the application code.

My role focused on:

- Understanding and documenting the business problem.
- Translating business requirements into structured specifications.
- Guiding the AI-assisted development process.
- Reviewing generated outputs and refining the solution.
- Defining validation scenarios based on actual business workflows.

### Technology Stack

- Google AI Studio
- Gemini
- React
- TypeScript
- Firebase
- Firestore

## ✅ Testing & Validation

I defined test cases and acceptance criteria to evaluate the system against key business scenarios.

| Scenario | Expected Business Result |
|---|---|
| Cash Sale | Invoice recorded, stock decreased, cash updated, and customer payment reflected. |
| Credit Sale | Invoice recorded, stock decreased, and unpaid amount added to the customer's balance. |
| Partial Payment | Payment recorded and remaining amount retained as outstanding debt. |
| Purchase | Purchase recorded against the supplier, stock increased, and payment status reflected. |
| Cancellation | Original transaction preserved and reversal entries used to adjust stock and balances. |
| Volume & Pricing | Volume calculated from dimensions and quantity, with calculated and agreed amounts stored separately. |

**Validation note:** These are defined test scenarios and acceptance criteria, not a claim that every test has been executed. The business owner separately compared migrated Excel balances with the system.

## 📈 Outcomes & Learnings

### What Changed

- Fragmented spreadsheets were consolidated into one integrated application.
- Sales, inventory, and financial records became connected.
- Transactions became traceable through reversal entries and an audit log.
- Structured records became available for further analysis.

### Key Learnings

- AI-assisted development depends on clear business requirements.
- Acceptance criteria make implementation phases easier to evaluate.
- Transaction traceability should be considered from the beginning.
- Understanding the business problem is more important than starting with the technology.

## 🚀 Future Opportunities

The following are planned areas for future development and analysis, not currently implemented features:

- SQL-based business data analysis.
- Power BI dashboards.
- Python-based data analysis.
- Sales trend analysis by month, customer, and timber size.
- Business performance indicators.
- Reporting automation.

## 🔗 Project Links

- 🌐 **Live Portfolio:** [View Case Study](https://mohamedzalat412.github.io/Timber-Management-System/)
- 💻 **GitHub Repository:** [Timber Portfolio](https://github.com/mohamedzalat412/Timber-Management-System)
- 💼 **LinkedIn:** [Mohamed Islam Zalat](https://www.linkedin.com/)

## 👤 About Me

**Mohamed Islam Zalat**  
Computer Science Student – Tanta University

Interested in Business Analysis, Product Ownership, Requirements Engineering, and Digital Transformation.

---

> **Note:** This case study uses real business workflows. Sensitive business information, including names, phone numbers, and financial values, is intentionally excluded from the public portfolio.
