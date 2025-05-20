# CDS Annotations
CDS annotations are metadata tags (preceded by @) that influence:
- OData behavior
- UI rendering (Fiori Elements)
- Authorization
- Analytics
- Behavior in RAP (ObjectModel)
- Database characteristics

## Annotation Categories
| Category       | Prefix             | Purpose                                 |
| -------------- | ------------------ | --------------------------------------- |
| Catalog        | `@AbapCatalog.*`   | DB-level settings                       |
| UI             | `@UI.*`            | Fiori Elements rendering                |
| OData          | `@OData.*`         | OData service behavior                  |
| Object Model   | `@ObjectModel.*`   | RAP, associations, composition          |
| Access Control | `@AccessControl.*` | Authorization checks                    |
| Analytics      | `@Analytics.*`     | Analytical queries (embedded analytics) |
| End-user text  | `@EndUserText.*`   | Field/view descriptions                 |

## Most Important CDS Annotations
### 1. @AbapCatalog.sqlViewName
- Defines the DDIC technical view name.
- Mandatory for classic CDS (not for CDS view entities).
- Example
  ```abap
  @AbapCatalog.sqlViewName: 'ZV_PRODUCT'
  ```

### 2. @EndUserText.label
- Provides a human-readable description for the CDS object or field.
- Example
  ```abap
  @EndUserText.label: 'Product Master View'
  ```

### 3. @AccessControl.authorizationCheck
- Enables DCL-based authorization checks.
- Example:
  ```abap
  @AccessControl.authorizationCheck: #CHECK
  ```

| Value                              | Meaning        |
| ---------------------------------- | -------------- |
| `#NOT_REQUIRED`                    | No auth check  |
| `#CHECK`                           | Checks via DCL |
| `#CHECK_WITH_INHERITED_PRIVILEGES` | Used in RAP    |

### 4. @OData.publish: true
- Auto-generates OData service for the view.
- Only suitable for simple read-only services.
- Example
  ```abap
  @OData.publish: true
  ```

### 5. @UI. Annotations* (Fiori Elements)
- On the **Entity**:
  ```abap
  @UI.headerInfo: {
    typeName: 'Product',
    typeNamePlural: 'Products',
    title: { value: 'matnr' },
    description: { value: 'maktx' }
  }
  ```
- On **Fields**:
  ```abap
  @UI.lineItem: [{ position: 10 }]
  @UI.selectionField: [{ position: 20 }]
  @UI.identification: [{ position: 30 }]
  ```

| Purpose        | Annotation           |
| -------------- | -------------------- |
| List table     | `@UI.lineItem`       |
| Filter fields  | `@UI.selectionField` |
| Object page    | `@UI.identification` |
| Header section | `@UI.headerInfo`     |

### 6. @ObjectModel. Annotations*
- Used in RAP and complex object structures.

| Annotation                          | Use                         |
| ----------------------------------- | --------------------------- |
| `@ObjectModel.readOnly`             | Makes field/view read-only  |
| `@ObjectModel.composition`          | Marks deep entity structure |
| `@ObjectModel.association.type`     | Composition, aggregation    |
| `@ObjectModel.createEnabled: true`  | Allows create in OData/RAP  |
| `@ObjectModel.updateEnabled: false` | Disallows update            |

### 7. @Analytics. Annotations*
- Used for analytical CDS cubes/dimensions.
- Example:
  ```abap
  @Analytics.dataCategory: #CUBE
  @Analytics.query: true
  @Analytics.dataExtraction.enabled: true
  ```

### 8. @VDM. (Virtual Data Model)*
- SAP internal VDM guidelines. If you build views according to these conventions, you can indicate intent:
- Example:
  ```abap
  @VDM.viewType: #BASIC / #COMPOSITE / #CONSUMPTION
  ```

### 9. @Semantics. (optional)*
- Defines semantic roles like currency, unit, quantity.
- Example:
  ```abap
  @Semantics.currencyCode: true
  waers,
  @Semantics.amount.currencyCode: 'waers'
  netpr
  ```

## Example — Full View with Annotations
```abap
@AbapCatalog.sqlViewName: 'ZV_PRODUCT'
@EndUserText.label: 'Product View'
@AccessControl.authorizationCheck: #CHECK
@OData.publish: true
define view ZI_Product as select from mara
association [0..1] to makt as _Text on _Text.matnr = mara.matnr
{
  key matnr,
      mtart,
      matkl,
      @UI.lineItem: [{ position: 10 }]
      @UI.selectionField: [{ position: 10 }]
      @EndUserText.label: 'Material Type'
      mtart,
      
      @Semantics.currencyCode: true
      waers,
      
      @Semantics.amount.currencyCode: 'waers'
      netpr
}
```
