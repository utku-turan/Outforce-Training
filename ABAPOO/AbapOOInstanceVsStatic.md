# Instance vs Static Components in OOABAP
## Instance Components
- These belong to a specific object (instance) of a class.
- You need to create an object using **NEW** (or **CREATE OBJECT**) to access them.
- Characteristics:
  - Each object has its own copy of instance attributes.
  - Methods can access and modify that specific object's data.
  - Constructor (METHOD constructor) is always instance-based.
- Example:
  ```abap
  CLASS zcl_vehicle DEFINITION.
    PUBLIC SECTION.
      METHODS: set_speed IMPORTING iv_speed TYPE i,
               get_speed RETURNING VALUE(rv_speed) TYPE i.
    PRIVATE SECTION.
      DATA: speed TYPE i.
  ENDCLASS.

  CLASS zcl_vehicle IMPLEMENTATION.
    METHOD set_speed.
      speed = iv_speed.
    ENDMETHOD.

    METHOD get_speed.
      rv_speed = speed.
    ENDMETHOD.
  ENDCLASS.

  DATA(lo_car1) = NEW zcl_vehicle( ).
  lo_car1->set_speed(100).

  DATA(lo_car2) = NEW zcl_vehicle( ).
  lo_car2->set_speed(200).
  ```

> lo_car1 and lo_car2 hold different speed values — they don’t interfere with each other.

## Static Components
- These belong to the class itself, not to any instance.
- You can access them without creating an object.
- Defined using **CLASS-DATA**, **CLASS-METHODS**
- Characteristics:
  - Shared across all instances
  - Useful for counters, constants, singleton patterns, utilities
- Example:
  ```abap
  CLASS zcl_util DEFINITION.
    PUBLIC SECTION.
      CLASS-METHODS: add IMPORTING a TYPE i b TYPE i RETURNING VALUE(result) TYPE i.
  ENDCLASS.

  CLASS zcl_util IMPLEMENTATION.
    METHOD add.
      result = a + b.
    ENDMETHOD.
  ENDCLASS.

  WRITE: zcl_util=>add( 3, 5 ).  "Output: 8
  ```

> You didn’t need to do NEW zcl_util( ) — this is a static utility method.

## Mixing Static and Instance Components
- You can use both in the same class:
  ```abap
  CLASS zcl_counter DEFINITION.
    PUBLIC SECTION.
      METHODS: increment.
      CLASS-METHODS: get_count RETURNING VALUE(rv_count) TYPE i.
    PRIVATE SECTION.
      CLASS-DATA: gv_count TYPE i.
  ENDCLASS.
  
  CLASS zcl_counter IMPLEMENTATION.
    METHOD increment.
      gv_count = gv_count + 1.
    ENDMETHOD.
  
    METHOD get_count.
      rv_count = gv_count.
    ENDMETHOD.
  ENDCLASS.
  
  DATA(lo1) = NEW zcl_counter( ).
  DATA(lo2) = NEW zcl_counter( ).
  lo1->increment( ).
  lo2->increment( ).
  
  WRITE: / zcl_counter=>get_count( ).  "Output: 2
  ```

> Both lo1 and lo2 increased the shared static count.

## Practical Use Cases

| Static Components                                 | Instance Components               |
| ------------------------------------------------- | --------------------------------- |
| Utility/helper classes (`ZCL_DATE_HELPER`)        | Business entities (`ZCL_INVOICE`) |
| Shared config/counters                            | User-specific state               |
| Factory methods (`CLASS-METHODS create_instance`) | Data that varies per object       |
