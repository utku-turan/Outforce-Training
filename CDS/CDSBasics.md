# Core Data Services (CDS) Basics
## Key Concepts
| Concept                    | Explanation                                                           |
| -------------------------- | --------------------------------------------------------------------- |
| `@AbapCatalog.sqlViewName` | The DDIC technical view name (for classic CDS)                        |
| `define view`              | CDS view declaration                                                  |
| `select from`              | Data source (usually a base table or another CDS view)                |
| `key`                      | Fields that define uniqueness in CDS (doesn’t enforce PK at DB level) |

## Important Notes
- CDS views are read-only unless used in RAP with proper behavior definitions.
- Can include joins, associations, filters, aggregations, case expressions, and more.
- They are defined in ADT (Eclipse), not in SE11 (although visible there after activation).

## Tools & Environments
| Tool                  | Purpose                                           |
| --------------------- | ------------------------------------------------- |
| **ADT (Eclipse)**     | Create/edit CDS views; UI support for annotations |
| **SE11**              | View structure of CDS (not for editing)           |
| **SE80**              | Legacy editor; not used for CDS                   |
| **ST05**              | SQL trace for performance/debugging CDS           |
| **SEGW / SEGW OData** | Traditional OData consumption (superseded by RAP) |

## Authorization Check Options
| Option                             | Description                            |
| ---------------------------------- | -------------------------------------- |
| `#NOT_REQUIRED`                    | No authorization check done at runtime |
| `#CHECK`                           | Authorization via DCL activated        |
| `#CHECK_WITH_INHERITED_PRIVILEGES` | Advanced control                       |

## CDS vs SE11 Views
| Feature              | SE11 View | CDS View            |
| -------------------- | --------- | ------------------- |
| Created in           | SE11 GUI  | Eclipse (ADT)       |
| Read/write           | Both      | Read-only (default) |
| Supports annotations | ❌         | ✅ Yes               |
| OData support        | ❌         | ✅ With annotations  |
| Extensible           | Limited   | ✅ Extend View       |

## CDS Naming Convention (Best Practice)
| Prefix | Meaning                        |
| ------ | ------------------------------ |
| `I_`   | Interface view (reusable, RAP) |
| `C_`   | Consumption view (UI/Fiori)    |
| `Z/Y`  | Custom namespace               |
