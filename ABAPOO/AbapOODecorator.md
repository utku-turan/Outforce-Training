# Decorator Pattern
- powerful for adding flexible, reusable **enhancements to objects** without altering their structure.
- allows you to add **additional behavior** to an object dynamically by wrapping it with other objects — decorators — that implement the same interface.
- It promotes composition over inheritance.
- Think of it as wrapping a gift box: each layer adds something (e.g., ribbon, label), but the core box remains the same.
- Unlike subclassing, this keeps behavior modular and pluggable.

## When to Use in ABAP
- You want to **add features to an object without modifying its code**.
- You want to **avoid deep inheritance** hierarchies.
- You need flexible layering of logic (e.g., logging, validation, caching).

## Benefits
| Benefit                  | Description                                     |
| ------------------------ | ----------------------------------------------- |
| 🔄 Flexible Enhancements | Add or remove behaviors at runtime              |
| 🧼 Clean Design          | Avoids class explosion from multiple subclasses |
| 📦 Reusable Wrappers     | Logging, caching, validation can be reused      |
| 🧪 Easy to Test          | Each layer can be unit-tested separately        |

## ABAP Use Cases
- Adding logging/auditing to services
- Wrapping database access with cache or retry logic
- Enriching messages before sending to APIs
- RAP action/behavior decorators (via delegation)

## Real-World Scenario: Logging Decorator for a Notification Service
- Suppose you have a notification service (IF_NOTIFIER) that sends alerts.
- You want to add logging or auditing functionality without touching the original logic.

### 1. Component Interface
```abap
INTERFACE if_notifier.
  METHODS: notify IMPORTING iv_message TYPE string.
ENDINTERFACE.
```

### 2. Concrete Component
```abap
CLASS zcl_email_notifier DEFINITION.
  PUBLIC SECTION.
    INTERFACES if_notifier.
ENDCLASS.

CLASS zcl_email_notifier IMPLEMENTATION.
  METHOD if_notifier~notify.
    WRITE: / 'Sending email:', iv_message.
  ENDMETHOD.
ENDCLASS.
```

### 3. Decorator Abstract Class
```abap
CLASS zcl_notifier_decorator DEFINITION ABSTRACT.
  PUBLIC SECTION.
    INTERFACES if_notifier.
    METHODS: constructor IMPORTING io_wrappee TYPE REF TO if_notifier.
  PROTECTED SECTION.
    DATA: mo_wrappee TYPE REF TO if_notifier.
ENDCLASS.

CLASS zcl_notifier_decorator IMPLEMENTATION.
  METHOD constructor.
    mo_wrappee = io_wrappee.
  ENDMETHOD.
ENDCLASS.
```

### 4. Logging Decorator
```abap
CLASS zcl_logging_notifier DEFINITION INHERITING FROM zcl_notifier_decorator.
  PUBLIC SECTION.
    INTERFACES if_notifier.
ENDCLASS.

CLASS zcl_logging_notifier IMPLEMENTATION.
  METHOD if_notifier~notify.
    WRITE: / 'LOG: Notification sent with message:', iv_message.
    mo_wrappee->notify( iv_message ).
  ENDMETHOD.
ENDCLASS.
```

### 5. Client Code (Applying the Decorator)
```abap
DATA(lo_email_notifier) = NEW zcl_email_notifier( ).
DATA(lo_logged_notifier) = NEW zcl_logging_notifier( lo_email_notifier ).

lo_logged_notifier->notify( 'System will restart at 10 PM.' ).
```

> Output
> LOG: Notification sent with message: System will restart at 10 PM.
> Sending email: System will restart at 10 PM.
