# Exception Handling in ABAP OO
- Exceptions in ABAP help you handle errors gracefully without breaking program flow.
- You wrap risky operations in TRY...CATCH...ENDTRY blocks.
- ABAP distinguishes between:
  - Class-based exceptions (preferred in OO ABAP)
  - Classic exceptions (still used in some function modules)

## Syntax Overview
```abap
TRY.
    " Risky code here
  CATCH cx_root INTO DATA(lx_root).
    " Exception handling logic
ENDTRY.
```

## Exception Class Hierarchy
| Class              | Description                         |
| ------------------ | ----------------------------------- |
| `CX_ROOT`          | Root class for all exceptions       |
| `CX_STATIC_CHECK`  | Must be declared in RAISING clause  |
| `CX_DYNAMIC_CHECK` | Doesn’t require RAISING clause      |
| `CX_NO_CHECK`      | Runtime exception, always catchable |

## Example: TRY...CATCH with Built-in Exceptions
```abap
TRY.
    DATA(lv_num) = 'ABC'.
    DATA(lv_int) = lv_num + 1. " Runtime error
  CATCH cx_sy_conversion_no_number INTO DATA(lx_conv).
    WRITE: / 'Conversion failed:', lx_conv->get_text( ).
ENDTRY.
```

## Defining Custom Exception Classes
### 1. Create an Exception Class
- You can do this in ADT (Eclipse) or SE24.
- Inherit from CX_STATIC_CHECK (recommended for predictable exception handling).
- Define custom attributes if needed (e.g., error code, details).

```abap
CLASS zcx_invalid_order DEFINITION
  INHERITING FROM cx_static_check
  CREATE PUBLIC.

  PUBLIC SECTION.
    METHODS: constructor IMPORTING iv_msg TYPE string.
ENDCLASS.
```

### 2. Implement the Constructor
```abap
CLASS zcx_invalid_order IMPLEMENTATION.
  METHOD constructor.
    super->constructor( iv_msg ).
  ENDMETHOD.
ENDCLASS.
```

### 3. Raising Custom Exceptions
```abap
METHOD validate_order.
  IF iv_order_id IS INITIAL.
    RAISE EXCEPTION NEW zcx_invalid_order( iv_msg = 'Order ID is missing' ).
  ENDIF.
ENDMETHOD.
```

### 4. Catching Custom Exceptions
```abap
TRY.
    lo_order_validator->validate_order( iv_order_id = '' ).
  CATCH zcx_invalid_order INTO DATA(lx_order).
    MESSAGE lx_order->get_text( ) TYPE 'E'.
ENDTRY.
```

## Best Practices
| Practice                               | Why It Matters                                |
| -------------------------------------- | --------------------------------------------- |
| Prefer class-based exceptions          | More flexible, testable, and modern           |
| Catch the **specific exception**       | Don’t use generic `CX_ROOT` unless necessary  |
| Keep messages **in exception classes** | Centralizes error info, keeps logic clean     |
| Use `RAISING` in method signature      | For `CX_STATIC_CHECK` exceptions              |
| Avoid `MESSAGE TYPE 'E'.` directly     | Use exceptions to raise and handle gracefully |

## Tools/Features in ADT
- You can auto-generate exception classes in ADT (Eclipse).
- Quick fixes (Ctrl+1) can convert MESSAGE to proper exception handling.
- Exception breakpoints: Debugger → Break on class-based exceptions.

## Real-Life Use Cases
- Invalid input validation in RAP or BOPF
- Business rule violations (e.g., limit exceeded)
- API or web service failures
- File not found or authorization errors
