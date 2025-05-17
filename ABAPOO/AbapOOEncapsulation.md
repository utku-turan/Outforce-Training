# Encapsulation in OO ABAP
- Encapsulation is one of the four pillars of object-oriented programming (OOP) and a critical concept in OO ABAP. (Encapsulation, Abstraction, Inheritance, Polymorphism)
- It's all about hiding internal data and implementation details, and exposing only what's necessary.
- Encapsulation means restricting direct access to class internals (data/logic) and exposing a controlled interface.
- It protects internal state from unintended changes.
- Achieved using visibility sections (PRIVATE, PROTECTED, PUBLIC) and getter/setter methods.

## Visibility Levels
| Section     | Accessible By             | Use for                   |
| ----------- | ------------------------- | ------------------------- |
| `PRIVATE`   | The class itself          | Internal implementation   |
| `PROTECTED` | Class itself + Subclasses | Controlled reuse/override |
| `PUBLIC`    | Any caller                | External interface        |

## Example: Encapsulation with Getter/Setter
```abap
CLASS zcl_employee DEFINITION.
  PUBLIC SECTION.
    METHODS: constructor IMPORTING iv_name TYPE string,
             get_name RETURNING VALUE(rv_name) TYPE string.
  PRIVATE SECTION.
    DATA: name TYPE string.
ENDCLASS.

CLASS zcl_employee IMPLEMENTATION.
  METHOD constructor.
    name = iv_name.
  ENDMETHOD.

  METHOD get_name.
    rv_name = name.
  ENDMETHOD.
ENDCLASS.

START-OF-SELECTION.
  DATA(lo_emp) = NEW zcl_employee( 'Utku' ).
  WRITE: lo_emp->get_name( ).  " Output: Utku
```

> name is hidden (PRIVATE), so it can't be accessed directly. It’s only accessible via the get_name method.

## Best Practices
- Avoid Public Attributes
- Make data PRIVATE or PROTECTED
- Expose via methods (e.g., GET_, SET_)
- Apply logic inside setters (validation, formatting, etc.)

## Benefits of Encapsulation
- Data integrity: Prevent unintended modifications
- Control: You can validate, log, or transform in getter/setter
- Flexibility: Internal structure can change without affecting callers
- Abstraction: Users don’t need to know internal details

## Encapsulation Tips
- Use private attributes unless you have a clear reason to expose them.
- Use protected attributes for subclass interaction — but keep it minimal.
- Make methods public only if they’re part of your class’s API.
- Avoid public attributes in ABAP Cloud (Clean Core violation).
