# Agentic Accounting Workflow (n8n)

End-to-end workflow for intake → extraction → validation/enrichment → posting (double-entry) → reconciliation → exception desk → exports.

## Contents
- `workflows/` – Import into n8n.
- `schemas/*.csv` – Export targets (Documents, JournalEntries, Vendors, Customers, SST, AgingSnapshots).
- `samples/` – Minimal test artifacts (e.g., `Invoice_ABC.pdf`).
- `docs/` – Project PDF / notes.

## Quick Start
1. Import `workflows/Latest_Workflow_11Nov_2.json` into n8n.
2. Configure credentials & env:
   - Copy `.env.example` → `.env` and fill in your tokens/URLs.
   - Update n8n credentials UI as needed.
3. Run triggers:
   - WhatsApp/Email intake → parse → extract → post → export.
4. Review:
   - Exceptions Desk produces `review_message` and supports APPROVE/REJECT/CORRECT via WhatsApp or Email replies.

## Exports
- **Documents.csv**: id | doc_type | doc_number | vendor_customer_id | issue_date | due_date | currency | subtotal | tax_rate | total  
- **JournalEntries.csv**: je_id | date | doc_id | account | debit | credit | memo | fx_rate | base_amount  
- **AgingSnapshots.csv**: snapshot_id | run_at | side | party_id | party_name | doc_type | doc_number | issue_date | due_date | currency | total | amount_open | days_outstanding | aging_bucket
