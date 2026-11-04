# Sound Lighting Pros — Inventory and Systems Analysis Project

This repository contains a BAIS 3350 Systems Analysis and Design team project for Sound Lighting Pros (SLP). Its purpose is to model and document an event-production business system that connects customers, events, proposals, orders, equipment, workers, fulfillment, and billing, while also showing how a large equipment list can be prepared for database use.

The project highlights team collaboration in a remote setting. Shared database snapshots, portable CSV tables, and an editable workbook give teammates a common source for reviewing changes, checking data, and coordinating work without requiring everyone to use Microsoft Access at the same time. It also assists with real-world development and preparation by practicing requirements analysis, relational data design, inventory organization, validation, documentation, and the limitations that must be resolved before a system is production-ready.

This is coursework and demonstration data, not a deployed business application or verified company inventory.

## Project purpose and learning goals

- Design a relational information system for an event-production company.
- Separate equipment categories, shared equipment models, and individual equipment items so the data can scale without unnecessary duplication.
- Connect operational records such as customers, events, proposals, orders, reservations, workers, invoices, payments, and deliveries.
- Give a remote team reviewable files and repeatable checks for collaborative development.
- Prepare students for real-world development by documenting assumptions, identifying data-quality gaps, and distinguishing a working prototype from a production system.

## Current database: V2.52

**[Download SLP_DB_V2.52.accdb](https://github.com/Saner108/slp-inventory-demo/raw/refs/heads/main/SLP_DB_V2.52.accdb)**

Open a local working copy in Microsoft Access for Windows. GitHub stores this database file; it does not run the Access application. Preserve a recovery copy before making changes.

The November 4, 2026 read-only inspection found:

- 23 business tables, 198 fields, and 27 relationship paths.
- 32 forms, seven reports, 13 named business queries, and two standard VBA modules.
- 700 equipment-item records and 273 shared equipment-model records.
- Connected saved customer, event, proposal, order, reservation, worker-assignment, invoice, payment, and delivery records.

Compared with the inspected V2.51 snapshot, V2.52 changes 700 equipment barcodes and 699 serial-number values. Numeric keys, relationships, transaction records, accepted prices, saved forms, reports, queries, and VBA are unchanged. The new identifier formats do not establish verified physical asset labels or manufacturer serial numbers.

## Verification and remaining work

Existing-record checks found no orphan foreign keys, checked duplicate-key combinations, equipment/worker overlaps, or source-price mismatches. These are snapshot checks, not tests of future saves or native workflow enforcement.

The earlier V2.51 Windows session verified the startup menu and reproduced a Customer lookup prompt for `DisplayText`. Native V2.52 testing remains pending. Open items include that lookup, consistent settlement accounting, delivery payment enforcement, package component reservations, and report coverage/formatting. Working authentication and role enforcement remain deferred.

The Help-text cleanup has not been applied. No audit history was deleted. This upload is the reviewed, unchanged V2.52 snapshot, not a claim that the system is production-ready, that Deliverable 4 was submitted, or that the training video is complete.

## Repository files

| File | Purpose |
|---|---|
| [SLP_DB_V2.52.accdb](SLP_DB_V2.52.accdb) | Current reviewed Access snapshot |
| [SLP_DB_V2.accdb](SLP_DB_V2.accdb) | Earlier database version retained for reference |
| [SLP_Equipment_Inventory_700_Separated.xlsx](SLP_Equipment_Inventory_700_Separated.xlsx) | Original inventory preparation workbook |
| [data/](data/) | Earlier inventory CSV exports; not synchronized V2.52 exports |
| [INVENTORY_PREPARATION.md](INVENTORY_PREPARATION.md) | Original inventory documentation and source-data limitations |

The older workbook and CSV files document inventory preparation and provide the most transparent way to review the 700-row staging dataset. They are not synchronized V2.52 exports. Do not reimport them over V2.52 transaction data or assume their serial/barcode values match the current database.

## Collaboration and development use

The repository is organized so that different contributors can work from the same documented baseline:

1. Use the README and `INVENTORY_PREPARATION.md` to understand scope, assumptions, and known limitations.
2. Review the workbook or CSV files when checking inventory structure and source values.
3. Use the Access file for forms, reports, queries, relationships, and business-process review.
4. Record and verify changes before treating them as part of the shared project baseline.

This workflow mirrors real development preparation: teams work from shared artifacts, validate dependencies and data quality, communicate known gaps, and avoid treating sample or unverified values as operational truth.

SHA-256 for the current database:

```text
5e02780f688fb85d0bec8817bdfe5263f17f2106cb5c5cf37f3cb24db7cd9e1b
```

Prepared with AI assistance for inspection, consistency checking, and documentation. Project records are coursework examples and are not evidence of real approvals, payments, signatures, or verified company inventory.
