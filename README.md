# SLP Inventory Demo

A student inventory-data demo for the Sound Lighting Pros (SLP) database project in BAIS 3350, Systems Analysis and Design. It shows how a draft equipment list can be organized into categories, shared model details, and individual item records before being loaded into Microsoft Access.

**This is sample coursework data, not verified company inventory or a finished inventory-management application.**

## What This Is

This repository is **version 1 (v1) of an inventory database design**. It takes one long equipment list and organizes it into three connected tables:

- `EquipmentCategory` stores broad groups such as audio, lighting, and DJ equipment.
- `EquipmentModel` stores details shared by a type of equipment, such as a Behringer X32 Producer.
- `EquipmentItem` stores each physical or source-listed unit, including its serial/code value, condition, and service fields.

The important idea is to separate information about an equipment type from information about a specific piece of equipment. For example, the model name is stored once, while several individual items can point to that model.

## Why You Should Know This

This is the foundation for a useful inventory database. Knowing this structure helps the team avoid duplicate information, track each piece of equipment, and keep the data organized as the project grows. It also shows which values came from the source list and which values still need to be checked.

## What “v1” Means

v1 is a cleaned and separated **starting point**, not a finished inventory system. It keeps all 700 source rows, proposes IDs and relationships, and creates a structure that can be used for the next database step. It does not yet include verified inventory, complete rules, forms, reports, automatic imports, or a finished Access application.

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

`SLP_Equipment_Inventory_700_Separated.xlsx` is the easiest file to open, review, and edit. It contains the three tables as worksheets. Use it to check the data, fix source values, and prepare the tables for import.

Excel is a **preparation and review tool**, not the final database. It is easy to edit, but it does not reliably enforce links between tables or stop duplicate and invalid entries.

### CSV files

The files in `data/` are plain-text copies of the same three tables. CSV files are useful for reviewing changes on GitHub, running data checks, writing scripts, and importing one table at a time. They are not additional datasets; they are alternate versions of the workbook tables.

### Access file

There is **no `.accdb` or `.mdb` Access file in this repository yet**. This repository provides the data and proposed table structure for an existing or newly created Access database. Access files are not included because they are binary files, may contain local or sensitive data, and are harder to review than CSV files.

### How the files work together

1. Review and correct the tables in the Excel workbook.
2. Use the CSV files as clean, portable copies of those tables.
3. Create or open the Access database.
4. Import `EquipmentCategory.csv` first.
5. Import `EquipmentModel.csv` second, using `CategoryID` to connect each model to a category.
6. Import `EquipmentItem.csv` third, using `ModelID` to connect each item to a model.
7. In Access, define and test the relationships between the three tables.
8. Verify field names, data types, required fields, and IDs before using real production data.

The order matters because models depend on categories, and items depend on models.

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
