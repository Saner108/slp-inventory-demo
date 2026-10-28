# SLP Inventory Demo

A student inventory-data demo for the Sound Lighting Pros (SLP) database project in BAIS 3350, Systems Analysis and Design. It shows how a draft equipment list can be organized into categories, shared model details, and individual item records before being loaded into Microsoft Access.

**This is sample coursework data, not verified company inventory or a finished inventory-management application.**

## What This Is

This repository is **version 1 (v1) of the inventory-data design**. It takes one flat equipment list and turns it into three related tables:

- `EquipmentCategory` stores broad groups such as audio, lighting, and DJ equipment.
- `EquipmentModel` stores details shared by a type of equipment, such as a Behringer X32 Producer.
- `EquipmentItem` stores each physical or source-listed unit, including its serial/code value, condition, and service fields.

The design separates information that belongs to a model from information that belongs to one individual item. For example, the model name is stored once, while multiple physical units can point to that model.

## Why You Should Know This

This is the foundation for a usable inventory database. Understanding the separation helps prevent duplicate model data, makes it possible to track individual equipment, and gives the team a consistent structure for importing, cleaning, and later expanding the inventory. It also makes clear which values are real source data, which values are proposed database fields, and which values still need verification.

## What “v1” Means

v1 is a cleaned and separated **starting point**, not a finished production system. It preserves the 700 source rows, proposes numeric keys and relationships, and provides a repeatable structure for the next database step. It does not yet include verified inventory, complete business rules, user forms, reports, automated imports, or a finished Access application.

Later versions may add verified serial numbers and asset labels, manufacturers and rates, condition and service workflows, validation rules, import automation, and an approved Access database.

## Explore the Demo

[Download the editable Excel workbook](SLP_Equipment_Inventory_700_Separated.xlsx), or view the CSV tables directly on GitHub:

| Table | Records | Purpose |
| --- | ---: | --- |
| [EquipmentCategory](data/EquipmentCategory.csv) | 27 | One record for each equipment category |
| [EquipmentModel](data/EquipmentModel.csv) | 273 | Shared model details and source model codes |
| [EquipmentItem](data/EquipmentItem.csv) | 700 | Individual source rows and their serial/code values |

`EquipmentCategory.CategoryID` links to `EquipmentModel.CategoryID`. Each model's `ModelID` links to its individual records in `EquipmentItem`.

For example, a model is listed once in `EquipmentModel`, while multiple units can reference that same model in `EquipmentItem`. A unit's serial number and condition belong to the individual item, not to the shared model.

## File Guide

### Excel workbook

`SLP_Equipment_Inventory_700_Separated.xlsx` is the easiest file for a person to review or edit. It contains the three separated tables in spreadsheet form and is useful for checking the proposed structure, correcting source values, and preparing data for import. Excel is not the final database: it does not enforce relationships or prevent duplicate and invalid entries as reliably as Access can.

### CSV files

The files in `data/` are plain-text exports of the same three tables. CSV is useful for version control, review, data-processing scripts, and importing one table at a time. The CSV files are not separate datasets; they are alternate copies of the workbook tables.

### Access file

There is **no `.accdb` or `.mdb` Access file in this repository yet**. This repository provides the data and proposed table structure that can be imported into an existing or newly created Access database. The `.accdb` and related lock-file extensions are ignored by Git because Access databases are binary, can contain local or sensitive data, and are not a good replacement for the reviewable CSV exports.

To continue in Access, create or open the target database, import `EquipmentCategory.csv`, then `EquipmentModel.csv`, then `EquipmentItem.csv`, and define the relationships described above. Verify field names, data types, required fields, and key behavior against the approved database design before importing production data.

## What Changed

The starting workbook contained one combined list: Category, Item, Model ID, and Serial #. This version separates those details into three linked tables, preserves all 700 source rows, and adds numeric staging IDs. Original text model codes are retained in `OriginalModelCode`.

One source model code appeared both with and without a `(sample)` label. It remains one model, while `OriginalItemLabel` preserves the exact label from each source row. Model entries that combine variants, repeat labels, or appear incomplete are flagged in `ReviewNote`, not silently split or merged.

## Important Limits

- 699 serial values are generated `SAMPLE-` placeholders. The remaining value, `AC241`, is an unverified source code. None should be presented as a verified manufacturer serial.
- The 273 model entries are source groupings, not 273 confirmed distinct manufacturer models. Some labels combine variants, cable types, software, or bundles.
- Manufacturer, description, rental rates, barcodes, conditions, service statuses, and dates are intentionally blank where the source did not supply verified values. Blank does not mean zero cost, good condition, or available.
- Numeric keys are proposed staging IDs. Preserve or remap them consistently when loading an existing Access database.
- `OriginalModelCode`, `ReviewNote`, and `OriginalItemLabel` are workbook reference fields, not additions to the approved database schema. Only the first six model columns and first nine item columns map to their existing database tables.
- Load categories before models, and models before items. Complete required fields and verify the database field names before importing. No Access import or production enforcement is demonstrated here.

## Checks Performed

The exported workbook was reopened and checked for unique item IDs, matching parent keys, 700 retained item rows, and exact reconstruction of every original category, item label, model code, and serial/code value. The CSV files were checked against the workbook tables. The original inventory workbook was not changed.

Prepared with AI assistance for data organization, consistency checks, and documentation. This repository demonstrates the inventory-data portion of a team coursework project; it does not claim to be a deployed business system.
