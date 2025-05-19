# Strategy Design Pattern
- perfect for selecting algorithms or business rules dynamically at runtime.
- It enables dynamic selection of behavior (algorithm, rule, logic) at runtime.
- You define a family of algorithms (via interface) and encapsulate them into separate classes.
- The client delegates the behavior to the selected strategy.

## When to Use It in ABAP
- You have multiple ways to perform a task and want to switch between them.
- Avoid CASE or IF chains based on logic type.
- For pluggable business rules, pricing, discount, validation, etc.

## ABAP Use Cases
- Tax or pricing calculation rules
- Custom validation or field control
- Campaign, loyalty, or scoring logic
- Workflow step selection or email templates

## Key Benefits
| Benefit                 | Description                                          |
| ----------------------- | ---------------------------------------------------- |
| 💡 Open/Closed          | Easy to add new strategy classes without changes     |
| 🧼 Clean Design         | No `IF`, `CASE`, or duplicated logic blocks          |
| 🔁 Swappable at Runtime | Change behavior dynamically — ideal for config rules |
| 🧪 Testable             | Strategies are independent and easy to test          |

## Real-World Use Case: Dynamic Discount Strategy
Let’s say we want to apply a discount for sales orders, but the rule depends on customer type, campaign, etc.

### 1. Define the Strategy Interface: IF_DISCOUNT_STRATEGY
```abap
INTERFACE if_discount_strategy.
  METHODS:
    calculate_discount
      IMPORTING iv_amount TYPE netwr
      RETURNING VALUE(rv_discount) TYPE netwr.
ENDINTERFACE.
```

### 2. Concrete Strategies
- Percentage Discount Strategy
  ```abap
  CLASS zcl_pct_discount DEFINITION.
    PUBLIC SECTION.
      INTERFACES if_discount_strategy.
  ENDCLASS.
  
  CLASS zcl_pct_discount IMPLEMENTATION.
    METHOD if_discount_strategy~calculate_discount.
      rv_discount = iv_amount * 0.10.
    ENDMETHOD.
  ENDCLASS.
  ```

- Flat Discount Strategy
  ```abap
  CLASS zcl_flat_discount DEFINITION.
    PUBLIC SECTION.
      INTERFACES if_discount_strategy.
  ENDCLASS.
  
  CLASS zcl_flat_discount IMPLEMENTATION.
    METHOD if_discount_strategy~calculate_discount.
      rv_discount = 50. " Flat 50 off
    ENDMETHOD.
  ENDCLASS.
  ```

### 3. Context Class That Uses the Strategy
```abap
CLASS zcl_discount_context DEFINITION.
  PUBLIC SECTION.
    METHODS:
      set_strategy IMPORTING io_strategy TYPE REF TO if_discount_strategy,
      get_discount IMPORTING iv_amount TYPE netwr RETURNING VALUE(rv_discount) TYPE netwr.
  PRIVATE SECTION.
    DATA: mo_strategy TYPE REF TO if_discount_strategy.
ENDCLASS.
```

```abap
CLASS zcl_discount_context IMPLEMENTATION.
  METHOD set_strategy.
    mo_strategy = io_strategy.
  ENDMETHOD.

  METHOD get_discount.
    IF mo_strategy IS BOUND.
      rv_discount = mo_strategy->calculate_discount( iv_amount ).
    ELSE.
      rv_discount = 0.
    ENDIF.
  ENDMETHOD.
ENDCLASS.
```

### 4. Client Code
```abap
DATA(lo_context) = NEW zcl_discount_context( ).
DATA(lo_strategy) = NEW zcl_pct_discount( ). " or zcl_flat_discount( )

lo_context->set_strategy( lo_strategy ).

DATA(lv_discount) = lo_context->get_discount( iv_amount = 1000 ).
WRITE: / 'Discount:', lv_discount.
```

> Output
> - If using percentage → Discount: 100
> - If using flat → Discount: 50
