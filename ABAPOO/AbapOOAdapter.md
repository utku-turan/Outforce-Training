# Adapter Design Pattern
- Adapter Pattern is especially useful in enterprise ABAP when **integrating with legacy systems**, external APIs, or standard SAP interfaces that don’t match your custom application's expected format.
- The Adapter Pattern allows **incompatible classes to work together by converting the interface** of one class into another interface the client expects.
- Think of it like a **plug adapter**: it doesn’t change the device or socket — it just makes them compatible.
- It enables reuse of legacy or third-party code without modifying its source.

## When to Use in ABAP
- You’re integrating with legacy classes or external APIs that don’t match your internal interface.
- You want to expose a standard interface to the rest of your app while internally using a different format.
- You need to standardize access to different data sources/services.

## Adapter Pattern Variants
| Type               | Description                                                               |
| ------------------ | ------------------------------------------------------------------------- |
| **Object Adapter** | Uses composition (like below, preferred in ABAP)                          |
| **Class Adapter**  | Uses inheritance (less common, ABAP doesn't support multiple inheritance) |

## Benefits
| Benefit              | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| 🧼 Clean Integration | Allows reuse of incompatible classes                         |
| 🔄 Swappable         | Replace adapter class without touching consumer code         |
| 🧪 Testable          | Easy to mock adapter for testing                             |
| 🧱 Decoupled         | Keeps core logic independent from legacy or external classes |

## ABAP Use Cases
- Wrapping 3rd-party connector libraries
- Bridging between old procedural logic and modern OO APIs
- Making legacy modules fit into modern interfaces or RAP logic


## Real-World Scenario: Legacy Payment System Adapter
- Your modern ABAP system expects a payment handler that implements IF_PAYMENT, but the legacy system has a rigid class ZCL_LEGACY_PAY that doesn’t implement this interface.

### 1. Target Interface (expected by the system)
```abap
INTERFACE if_payment.
  METHODS: make_payment IMPORTING iv_amount TYPE p DECIMALS 2.
ENDINTERFACE.
```

### 2. Legacy Class (you can't modify it)
```abap
CLASS zcl_legacy_pay DEFINITION.
  PUBLIC SECTION.
    METHODS: execute_payment IMPORTING value TYPE p DECIMALS 2.
ENDCLASS.

CLASS zcl_legacy_pay IMPLEMENTATION.
  METHOD execute_payment.
    WRITE: / 'Legacy payment executed:', value.
  ENDMETHOD.
ENDCLASS.
```

### 3. Adapter Class
```abap
CLASS zcl_payment_adapter DEFINITION.
  PUBLIC SECTION.
    INTERFACES if_payment.
  PRIVATE SECTION.
    DATA: mo_legacy TYPE REF TO zcl_legacy_pay.
ENDCLASS.

CLASS zcl_payment_adapter IMPLEMENTATION.

  METHOD if_payment~make_payment.
    IF mo_legacy IS INITIAL.
      mo_legacy = NEW zcl_legacy_pay( ).
    ENDIF.
    mo_legacy->execute_payment( iv_amount ).
  ENDMETHOD.

ENDCLASS.
```

### 4. Usage in Client Code
```abap
DATA(lo_payment) TYPE REF TO if_payment.

lo_payment = NEW zcl_payment_adapter( ).
lo_payment->make_payment( 123.45 ).
```
