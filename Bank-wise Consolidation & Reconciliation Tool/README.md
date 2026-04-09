# Bank-wise Consolidation & Reconciliation Tool (BSC Tool)

## 📌 Overview
- **Problem**: Finance teams reconcile multi-bank statements across inconsistent Excel formats, remarks, and naming conventions—driving manual effort, errors, and delayed reporting.
- **Solution built**: Developed a Windows desktop application that **validates bank statement file names**, **parses Excel statements**, **standardizes transaction categorization (Inwards/Outwards)**, and **generates a consolidated, styled Excel output** with balance tracking.
- **Why it matters**: Achieved faster, more reliable daily consolidation for **India1 Payments Ltd** by reducing spreadsheet-heavy reconciliation work and improving traceability across banks and transaction types.

## 🚀 Key Features
- Implemented **Tkinter desktop UI** with progress tracking and guided input for **opening balance**.
- Designed **automated filename validation** using an allowlist of prefixes; moved invalid files to an **Error** folder for clean triage.
- Implemented **multi-format Excel ingestion** (e.g., `.xlsx`, `.xls`, `.xlsb`) with bank-specific parsing rules driven by configuration.
- Built **rule-based transaction aggregation** by **Date + Remark**, mapping raw remarks to standardized business headings.
- Generated a consolidated `output.xlsx` with **multi-level headers** (Details / Inwards / Outwards / Working) and **auto-styling** (column sizing, borders, header fills).
- Computed **Opening Balance → Closing Balance** progression using aggregated daily credits/debits per bank.

## 🛠️ Tech Stack
- **Languages**:
  - Python
- **Frameworks**:
  - Tkinter (desktop UI)
- **Tools & Libraries**:
  - Pandas (data processing, aggregation)
  - OpenPyXL (Excel write/styling)
  - CSV / JSON (configuration, metadata)
- **Platforms**:
  - Windows

## 📚 Project Learnings
- Developed strong proficiency in **data cleansing**, **transaction normalization**, and **Excel automation** for finance workflows.
- Implemented **configuration-driven parsing** using JSON mappings to handle heterogeneous bank statement layouts.
- Improved practical skills in **desktop UI engineering**, **error handling**, and **file pipeline design** (Ready/Error/Completed).
- Strengthened understanding of **reconciliation concepts**: credits vs debits, settlement categorization, and balance roll-forward.

## 📊 Results / Output
- Produced a consolidated Excel workbook at `BWCFiles/Completed/output.xlsx`.
- Delivered standardized reporting sections:
  - **Details**: Date, Purpose, Type, Bank, SAP Code, Opening Balance
  - **Inwards / Outwards**: categorized movement totals
  - **Working**: Closing Balance and utilization-related fields
- Achieved a repeatable pipeline that converts multiple bank statements into a single, finance-ready output with consistent headings.

## 🧠 Output Learnings
- Observed that **remark-to-heading mapping quality** is the primary driver of consolidation accuracy; clean mappings reduce uncategorized or mis-bucketed totals.
- Learned that **date normalization** (Excel serial vs datetime) is essential for reliable day-level aggregation across banks.

## 🔍 Output Interpretation
- The consolidated `output.xlsx` serves as a daily operational view of **cash movement** and **bank-wise balances**, enabling faster close processes and improved decision-making.
- Standardized headings support downstream **MIS reporting**, **SAP/GL alignment**, and settlement visibility across multiple banking partners.

## ⚠️ Challenges & Solutions
- **Inconsistent bank statement formats →** Implemented **JSON-driven column mapping** (date, debit, credit, remarks, CR/DR separator) per bank.
- **Invalid or unexpected filenames →** Enforced **prefix-based validation** and automatically routed non-compliant files to `BWCFiles/Error/`.
- **Remarks variability across banks →** Implemented **remarks-to-heading mapping** to normalize raw narratives into standardized categories.
- **Excel date serial inconsistencies →** Normalized to datetime using a consistent baseline conversion for stable aggregation.
- **Readability of final output →** Implemented **OpenPyXL styling** (borders, alignment, header colors, auto-fit sizing).

## 🔮 Future Improvements
- Add **audit logs** (per file, per rule, per transaction) to improve traceability and compliance reviews.
- Implement **unmapped-remarks reporting** to proactively highlight mapping gaps and reduce manual follow-ups.
- Add **performance optimizations** for large files (chunking, vectorized operations, caching intermediate aggregates).
- Introduce **packaging/distribution** (PyInstaller) for a cleaner Windows deployment experience.
- Add optional **SQLite persistence** for historical runs, reruns, and trend reporting across periods.

## ✅ Conclusion
- Designed and implemented a finance-grade consolidation workflow that standardizes multi-bank inputs into a single, consistent reconciliation output.
- Improved operational reliability for **India1 Payments Ltd** by reducing manual Excel effort and increasing repeatability in bank-wise consolidation.

