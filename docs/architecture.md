# TenderBough — proposed AWS architecture

TenderBough uses AWS to read large tender packs quickly, extract requirements accurately and keep every bid confidential.

## Request flow

1. Tender pack
2. Amazon S3
3. Textract
4. Bedrock
5. DynamoDB
6. Bid team review
7. Submission checklist

## Services

### Amazon Bedrock

**Role:** Identify and compare requirements

Finds obligations, submission instructions and evaluation criteria, classifies them, and compares addenda with earlier versions — always citing section and page.

### Amazon Textract

**Role:** Read tender packs

Extracts text, tables and forms from long PDFs and scanned documents, including returnable schedules and pricing tables.

### Amazon S3

**Role:** Store tender and evidence files

Keeps tender packs, addenda and your evidence library encrypted and versioned, separated per tender and per customer.

### Amazon DynamoDB

**Role:** Hold matrices and checklists

Stores requirements, owners, evidence links, review decisions and checklist status for fast collaborative editing.

### AWS Lambda

**Role:** Run extraction and comparisons

Orchestrates extraction, builds matrices, compares addenda and checks evidence expiry as documents are added.

## Principles

- **Page-linked** — Every requirement links to its section and page.
- **Bids stay confidential** — Your bids are never shared or used for training.
- **Humans sign off** — Matrices are reviewed before anyone relies on them.

## Safeguards

- **Bid managers review** — Extracted requirements are reviewed and approved by your team.
- **Traceable to source** — Each requirement links back to the tender page it came from.
- **No legal or bid advice** — TenderBough organises requirements; strategy and legal review stay with your experts.
- **Confidential bids** — Encrypted, access-controlled and isolated per tender.

## MVP scope

Bring a live or recent tender. We extract the requirement matrix and document inventory, your bid manager reviews it, and we track evidence and checklist status through to submission.

- Tender pack upload
- Requirement matrix with page links
- Document inventory
- Submission checklist
- Evidence library basics
