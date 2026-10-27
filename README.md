# SLP Inventory Demo

A student inventory-data demo for the Sound Lighting Pros (SLP) database project in BAIS 3350, Systems Analysis and Design. It shows how a draft equipment list can be separated into categories, shared model details, and individual item records for a Microsoft Access database.

**This is sample coursework data, not verified company inventory or a finished inventory-management application.**

## Explore the Demo

[Download the editable Excel workbook](SLP_Equipment_Inventory_700_Separated.xlsx), or view the CSV tables directly on GitHub:

| Table | Records | Purpose |
| --- | ---: | --- |
| [EquipmentCategory](data/EquipmentCategory.csv) | 27 | One record for each equipment category |
| [EquipmentModel](data/EquipmentModel.csv) | 273 | Shared model details and source model codes |
| [EquipmentItem](data/EquipmentItem.csv) | 700 | Individual source rows and their serial/code values |

`EquipmentCategory.CategoryID` links to `EquipmentModel.CategoryID`. Each model's `ModelID` links to its individual records in `EquipmentItem`.

For example, a model is listed once in `EquipmentModel`, while multiple units can reference that same model in `EquipmentItem`. A unit's serial number and condition belong to the individual item, not to the shared model.

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
