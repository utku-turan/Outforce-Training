# Inheritance in ABAP OO
- Inheritance in Object-Oriented ABAP (OO ABAP) is a powerful feature that enables code reuse and polymorphic behavior by forming IS-A relationships between classes.
- Inheritance allows a class (subclass) to inherit the attributes and methods of another class (superclass).
- The subclass can:
  - Reuse the functionality of the superclass
  - Add new attributes/methods
  - Override inherited methods

## Syntax Overview
```abap
CLASS zcl_superclass DEFINITION.
  PUBLIC SECTION.
    METHODS: greet.
ENDCLASS.

CLASS zcl_superclass IMPLEMENTATION.
  METHOD greet.
    WRITE: / 'Hello from Superclass'.
  ENDMETHOD.
ENDCLASS.

CLASS zcl_subclass DEFINITION INHERITING FROM zcl_superclass.
  PUBLIC SECTION.
    METHODS: greet_sub.
ENDCLASS.

CLASS zcl_subclass IMPLEMENTATION.
  METHOD greet_sub.
    WRITE: / 'Hello from Subclass'.
  ENDMETHOD.
ENDCLASS.
```

Usage:
```abap
DATA(lo_child) = NEW zcl_subclass( ).
lo_child->greet( ).     " From superclass
lo_child->greet_sub( ). " From subclass
```

## Method Overriding
- Subclasses can override a method defined in the superclass using the REDEFINITION keyword.
  ```abap
  CLASS zcl_super DEFINITION.
    PUBLIC SECTION.
      METHODS: display.
  ENDCLASS.
  
  CLASS zcl_super IMPLEMENTATION.
    METHOD display.
      WRITE: / 'Message from Superclass'.
    ENDMETHOD.
  ENDCLASS.
  
  CLASS zcl_sub DEFINITION INHERITING FROM zcl_super.
    PUBLIC SECTION.
      METHODS: display REDEFINITION.
  ENDCLASS.
  
  CLASS zcl_sub IMPLEMENTATION.
    METHOD display.
      WRITE: / 'Message from Subclass'.
    ENDMETHOD.
  ENDCLASS.
  ```

> Now, calling display on zcl_sub will execute the subclass version.

## Using SUPER-> to Call Superclass Methods
- Sometimes, a subclass wants to extend — not completely replace — a method. Use SUPER->method_name( ).
  ```abap
  METHOD display.
    SUPER->display( ). " Call superclass first
    WRITE: / '...and then from Subclass'.
  ENDMETHOD.
  ```

## Best Practices
- Favor composition over inheritance unless there's a strong IS-A relationship.
- Keep superclass responsibilities generic.
- Avoid deep inheritance chains (max 2–3 levels).
- Use FINAL keyword to prevent further inheritance, if needed.
  ```abap
  CLASS zcl_base DEFINITION FINAL. " Can't be subclassed
  ```
