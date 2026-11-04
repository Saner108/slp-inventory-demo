# Sound Lighting Pros — Microsoft Access Project

A BAIS 3350 Systems Analysis and Design team project covering customers, events, proposals, orders, equipment, workers, fulfillment, and billing.

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

The older workbook and CSV files document inventory preparation. Do not reimport them over V2.52 transaction data or assume their serial/barcode values match the current database.

SHA-256 for the current database:

```text
5e02780f688fb85d0bec8817bdfe5263f17f2106cb5c5cf37f3cb24db7cd9e1b
```

Prepared with AI assistance for inspection, consistency checking, and documentation. Project records are coursework examples and are not evidence of real approvals, payments, signatures, or verified company inventory.
