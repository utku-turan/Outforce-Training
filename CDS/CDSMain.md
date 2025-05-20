# Core Data Services (CDS)
- Core Data Services (CDS) is a semantic data modeling layer in SAP that allows you to define views and data models on top of database tables.
- It supports code pushdown by moving data-intensive operations (joins, filters, aggregations) to the HANA DB layer.
- CDS views can serve:
  - ABAP SQL consumers
  - OData services for Fiori/UI5
  - RAP data models
  - Embedded analytics

## Why Use CDS?
- Declarative syntax → cleaner, more maintainable
- Performance via HANA pushdown
- Reusability & extensibility
- Integration with OData, Fiori Elements, and RAP
- Rich annotation support for UI, authorization, etc.

## CDS View Syntax (Simple Example)
```abap
@AbapCatalog.sqlViewName: 'ZCDS_BASIC'
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Basic Product View'
define view zcds_product as select from mara
{
  key matnr,
      ersda,
      matkl,
      mtart
}
```

## CDS Basics
- Key Concepts, Tools & Environments
- CDS vs traditional views vs Open SQL
- CDS syntax and annotations overview
- CDS naming conventions (I_ and C_ interfaces)
- Details can be found [here](/CDS/CDSBasics.md).

## CDS View Types
- Basic Views (no logic, reusable)
- Composite Views (joins, unions)
- Consumption Views (UI-oriented, analytical)
- Interface Views (exposed for consumption)
- Analytical Views (cube, dimension, fact)
- External Views (proxy for external entities)
- Details can be found [here](/CDS/CDSViewTypes.md).

## Annotations
- `@AbapCatalog.*`
- `@UI.*`
- `@OData.*`
- `@ObjectModel.*`
- `@AccessControl.*`
- `@Analytics.*`
- Details can be found [here](/CDS/CDSAnnotations.md).

## CDS Associations and Joins
- Path expressions vs joins
- Composition of associations
- `LEFT OUTER` vs `INNER` joins in CDS
- ON conditions and cardinality
- Details can be found [here](/CDS/CDSAssociations.md).
- [Composition vs Aggregation in CDS](/CDS/CDSCompositionVsAggregation.md)

## CDS Parameters
- Using parameters in views
- How to consume parameterized views in ABAP
- Details can be found [here](/CDS/CDSwithParameters.md).

## CDS with OData and Fiori
- `@OData.publish: true` (auto exposure)
- Using CDS views in Fiori Elements
- UI annotations for fields, tables, charts, facets

## CDS and RAP
- CDS as the data model layer in RAP
- Mapping behavior to CDS views
- Projection vs Interface views
- BDEF/BIMP dependencies

## Authorization with CDS
- DCL (Data Control Language)
- Defining access control using `@AccessControl.authorizationCheck`
- PFCG roles integration

## CDS Extensions
- Extending existing CDS views
- Adding fields and annotations via EXTEND VIEW
- Limitations of extension

## CDS View Entities (vs CDS DDIC-based Views)
- View entities (new syntax & runtime engine)
- Differences from classic CDS views (DDIC-based)
- Migration from classic to CDS view entities
- Details can be found [here](/CDS/CDSViewEntity.md)

## CDS and Performance
- Code pushdown to DB layer
- Using `FILTER`, `CAST`, `CASE`, `VALUE`, `GROUP BY`, `UNION`
- Index usage and tuning
- Restrictions for performance-critical views

## Testing & Debugging CDS
- Using ADT preview
- SQL trace (ST05), PlanViz, and Explain
- Debugging with `SELECT FROM <CDS>` in ABAP

## CDS View Publishing and Exposure
- SEGW vs RAP exposure
- Versioning and transport strategy

## CDS in ABAP SQL
- Consuming CDS in Open SQL
- Using path expressions in SELECT statements
- CDS with table functions

## Advanced Topics
- CDS Table Functions (AMDP integration)
- Hierarchies in CDS (analytical queries)
- Temporal joins and valid-from modeling
- CDS annotations for Analytics and SmartFilterBar 
