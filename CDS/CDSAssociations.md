# Associations and Path Expressions in CDS
## What is an Association?
- An **association is a declarative JOIN** between two data sources (CDS views or DB tables), defined with a specific cardinality and join condition.
- It's the recommended alternative to writing explicit JOINs in the FROM clause in CDS.

## Syntax Example:
```abap
association [0..1] to I_Customer as _Customer on _Customer.Customer = SalesOrder.Customer
```

> - `[0..1]` → cardinality: zero or one match expected
> - `_Customer` → name of the association (prefixed by convention)
> - `on ...` → join condition

## Why Use Associations?
- **Reusability** and cleaner code.
- Efficient data fetching (**lazy loading**).
- Seamless navigation in OData/Fiori/RAP.
- Better metadata exposure and annotations.

## Consuming Associations — Path Expressions
- You access fields of associated entities using **path expressions**:
- Example:
  ```abap
  _Customer.Name
  _Customer.Address.City
  ```
- Or include the whole structure:
  ```abap
  _Customer
  ```
- If you want to expose fields in the current view, you must explicitly expose them via path expressions.

## Example:
```abap
define view ZI_SalesOrder as select from I_SalesOrder as so
  association [0..1] to I_Customer as _Customer on _Customer.Customer = so.Customer
{
  key so.SalesOrder,
      so.Customer,
      _Customer.Name as CustomerName,
      _Customer.Address.City as CustomerCity
}
```

## Cardinalities
| Cardinality | Meaning                           |
| ----------- | --------------------------------- |
| `[1..1]`    | Exactly one match                 |
| `[0..1]`    | Optional, at most one match       |
| `[1..*]`    | One or more                       |
| `[0..*]`    | Zero or more (default if omitted) |

> Use the most restrictive cardinality possible to improve performance and clarity.

## Filtering Associated Data
- You can apply filters inline using association path expressions:
  ```abap
  where _Customer.Country = 'DE'
  ```
- Or filter exposed fields in the select:
  ```abap
  _Customer[Country = 'DE'].Name
  ```

## Important Notes
- Associations are **lazy-loaded** in OData — **only fetched when expanded or accessed**.
- Deep associations (e.g., _SalesOrder._Customer._Region) are supported.
- Use annotations like `@ObjectModel.association.type: [#COMPOSITION | #AGGREGATION]` in RAP models.
- Avoid deep nesting in performance-critical queries unless required.

## In RAP (Behavior Definition Context)
- Associations become even more powerful when paired with compositions and behavior definitions:
  ```abap
  define view entity ZI_Order with parameters ... as select from ...

  association [0..*] to ZI_Item as _Items
      on _Items.OrderID = OrderID
      and _Items.Client = Client

  @ObjectModel.composition: true
  _Items
  ```
> - This marks _Items as a child node in a RAP-managed composition tree.
> - CRUD operations can propagate automatically.
