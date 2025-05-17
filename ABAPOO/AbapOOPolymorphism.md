# Polymorphism in ABAP OO
- Polymorphism is a key OO concept and works hand-in-hand with inheritance and interfaces in ABAP OO. 
- It allows you to write flexible and extensible code that can work with different types of objects through a common interface or superclass.
- Polymorphism means "many forms".
- In ABAP, it allows you to:
  - Use a parent class reference (or interface) to point to different subclass objects
  - Call methods dynamically based on the actual object type at runtime
- This leads to more flexible, scalable code.

## Types of Polymorphism in ABAP
| Type                  | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| **Inheritance-based** | Using a superclass reference to handle subclass objects              |
| **Interface-based**   | Using an interface reference for objects implementing that interface |

## Inheritance-Based Polymorphism
Example:
```abap
CLASS zcl_animal DEFINITION.
  PUBLIC SECTION.
    METHODS: make_sound.
ENDCLASS.

CLASS zcl_animal IMPLEMENTATION.
  METHOD make_sound.
    WRITE: / 'Some animal sound'.
  ENDMETHOD.
ENDCLASS.

CLASS zcl_dog DEFINITION INHERITING FROM zcl_animal.
  PUBLIC SECTION.
    METHODS: make_sound REDEFINITION.
ENDCLASS.

CLASS zcl_dog IMPLEMENTATION.
  METHOD make_sound.
    WRITE: / 'Woof!'.
  ENDMETHOD.
ENDCLASS.

CLASS zcl_cat DEFINITION INHERITING FROM zcl_animal.
  PUBLIC SECTION.
    METHODS: make_sound REDEFINITION.
ENDCLASS.

CLASS zcl_cat IMPLEMENTATION.
  METHOD make_sound.
    WRITE: / 'Meow!'.
  ENDMETHOD.
ENDCLASS.
```

Usage:
```abap
DATA: lo_animal TYPE REF TO zcl_animal.

lo_animal = NEW zcl_dog( ).
lo_animal->make_sound( ).  " Woof!

lo_animal = NEW zcl_cat( ).
lo_animal->make_sound( ).  " Meow!
```

> Although the reference type is zcl_animal, the correct subclass method is called at runtime — that’s runtime polymorphism.

## Interface-Based Polymorphism
Example:
```abap
INTERFACE if_vehicle.
  METHODS: move.
ENDINTERFACE.

CLASS zcl_car DEFINITION.
  PUBLIC SECTION.
    INTERFACES: if_vehicle.
ENDCLASS.

CLASS zcl_car IMPLEMENTATION.
  METHOD if_vehicle~move.
    WRITE: / 'Car is moving'.
  ENDMETHOD.
ENDCLASS.

CLASS zcl_bike DEFINITION.
  PUBLIC SECTION.
    INTERFACES: if_vehicle.
ENDCLASS.

CLASS zcl_bike IMPLEMENTATION.
  METHOD if_vehicle~move.
    WRITE: / 'Bike is moving'.
  ENDMETHOD.
ENDCLASS.
```

Usage:
```abap
DATA: lo_vehicle TYPE REF TO if_vehicle.

lo_vehicle = NEW zcl_car( ).
lo_vehicle->move( ).  " Car is moving

lo_vehicle = NEW zcl_bike( ).
lo_vehicle->move( ).  " Bike is moving
```

> This allows dynamic binding and interchangeability of different classes that implement the same interface.

## Why Use Polymorphism?
- Promotes flexibility and reusability
- Enables loosely-coupled design
- Reduces IF...ELSE or CASE statements
- Key for factory patterns, plug-in architectures, event handlers

## Example Use Case: Generic Handler
```abap
CLASS zcl_animal_handler DEFINITION.
  PUBLIC SECTION.
    METHODS: handle IMPORTING io_animal TYPE REF TO zcl_animal.
ENDCLASS.

CLASS zcl_animal_handler IMPLEMENTATION.
  METHOD handle.
    io_animal->make_sound( ).
  ENDMETHOD.
ENDCLASS.
```

> You can pass any animal subclass, and the correct behavior is executed.

