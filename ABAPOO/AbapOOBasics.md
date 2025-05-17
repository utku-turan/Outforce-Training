# Basic OOABAP Concepts
## Class
- A class is a blueprint that defines attributes (data) and methods (behavior).
- Two parts:
  - CLASS ... DEFINITION. → defines structure
  - CLASS ... IMPLEMENTATION. → defines logic
- Example:
  ```abap
  CLASS zcl_vehicle DEFINITION.
    PUBLIC SECTION.
      METHODS: drive.
    PRIVATE SECTION.
      DATA: speed TYPE i.
  ENDCLASS.

  CLASS zcl_vehicle IMPLEMENTATION.
    METHOD drive.
      speed = 100.
      WRITE: 'Driving at', speed.
    ENDMETHOD.
  ENDCLASS.
  ```

## Object
- An object is an instance of a class — it occupies memory and can perform actions via methods.
- Example
  ```abap
  DATA(lo_vehicle) = NEW zcl_vehicle( ).
  lo_vehicle->drive( ).
  ```

## Attributes
- Represent the data/properties of an object.
- Declared in the data sections (PUBLIC, PROTECTED, PRIVATE).
- Attributes can be:
  - Instance attributes (unique to each object)
  - Static attributes (CLASS-DATA) shared across all instances 
- Example
  ```abap
  DATA: name TYPE string,
        speed TYPE i.
  ```

## Methods
- Methods are procedures/functions that belong to a class.
- Can access the object’s attributes.
- May include input/output parameters, exceptions, or returning values.
- Syntax
  ```abap
  METHODS: set_speed IMPORTING iv_speed TYPE i,
         get_speed RETURNING VALUE(rv_speed) TYPE i.
  ```

## Constructor
- A special method that is called automatically when an object is created.
- Used to initialize attributes.
- Example
  ```abap
  CLASS zcl_vehicle DEFINITION.
    PUBLIC SECTION.
      METHODS: constructor IMPORTING iv_name TYPE string.
    PRIVATE SECTION.
      DATA: name TYPE string.
  ENDCLASS.

  CLASS zcl_vehicle IMPLEMENTATION.
    METHOD constructor.
      name = iv_name.
    ENDMETHOD.
  ENDCLASS.
  ```
- Usage:
  ```abap
  DATA(lo_car) = NEW zcl_vehicle( 'BMW' ).
  ```

## Visibility Sections
- Control access to attributes and methods:

| Section     | Accessible by...                |
| ----------- | ------------------------------- |
| `PUBLIC`    | All programs and other classes  |
| `PROTECTED` | Subclasses and the class itself |
| `PRIVATE`   | Only within the defining class  |

- **Best Practice:** Keep data PRIVATE and expose access via PUBLIC getter/setter methods.

## Full Example
```abap
CLASS zcl_car DEFINITION.
  PUBLIC SECTION.
    METHODS: constructor IMPORTING iv_model TYPE string,
             get_model RETURNING VALUE(rv_model) TYPE string.
  PRIVATE SECTION.
    DATA: model TYPE string.
ENDCLASS.

CLASS zcl_car IMPLEMENTATION.
  METHOD constructor.
    model = iv_model.
  ENDMETHOD.

  METHOD get_model.
    rv_model = model.
  ENDMETHOD.
ENDCLASS.

START-OF-SELECTION.
  DATA(lo_car) = NEW zcl_car( 'BMW' ).
  WRITE: / lo_car->get_model( ).
```
