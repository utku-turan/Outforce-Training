# Abstraction in ABAP OO
- Abstraction in Object-Oriented ABAP is a foundational concept in OO design, allowing you to define essential structures without committing to concrete implementations.
- Abstraction is the concept of exposing only relevant information and hiding the internal implementation details.
- In ABAP OO, this is primarily achieved via:
  - **Abstract classes**
  - **Interfaces**
- They act as contracts — defining what a class must do, not how it does it.

## Abstract Classes
- An abstract class is a class that cannot be instantiated directly.
- used as a base class for subclasses.
- can contain:
  - Abstract methods (must be implemented by subclasses)
  - Concrete methods (optional)
- Example
  ```abap
  CLASS zcl_vehicle DEFINITION ABSTRACT.
    PUBLIC SECTION.
      METHODS: start_engine ABSTRACT,
               brake. " concrete
  ENDCLASS.

  CLASS zcl_vehicle IMPLEMENTATION.
    METHOD brake.
      WRITE: / 'Braking...'.
    ENDMETHOD.
  ENDCLASS.
  ```
- Subclass
  ```abap
  CLASS zcl_car DEFINITION INHERITING FROM zcl_vehicle.
    PUBLIC SECTION.
      METHODS: start_engine REDEFINITION.
  ENDCLASS.

  CLASS zcl_car IMPLEMENTATION.
    METHOD start_engine.
      WRITE: / 'Car engine started'.
    ENDMETHOD.
  ENDCLASS.
  ```
  
  ```abap
  DATA(lo_car) = NEW zcl_car( ).
  lo_car->start_engine( ).
  lo_car->brake( ).
  ```

> You must implement all abstract methods in non-abstract subclasses.

## Interfaces
- An interface defines method signatures only.
- A class that implements the interface must provide implementation for all interface methods.
- supports multiple inheritance.
- Example
  ```abap
  INTERFACE if_loggable.
    METHODS: log_event.
  ENDINTERFACE.

  CLASS zcl_app_logger DEFINITION.
    PUBLIC SECTION.
      INTERFACES: if_loggable.
  ENDCLASS.

  CLASS zcl_app_logger IMPLEMENTATION.
    METHOD if_loggable~log_event.
      WRITE: / 'Event logged'.
    ENDMETHOD.
  ENDCLASS.
  ```
- Usage
  ```abap
  DATA(lo_logger) = NEW zcl_app_logger( ).
  lo_logger->if_loggable~log_event( ).
  ```

## Abstract Class vs Interface
| Feature                 | Abstract Class             | Interface               |
| ----------------------- | -------------------------- | ---------------------   |
| Can have implementation | ✅ Yes                     | ❌ No                  |
| Can define attributes   | ✅ Yes                     | ❌ No (constants only) |
| Multiple inheritance    | ❌ No                      | ✅ Yes                 |
| Instantiable            | ❌ No                      | ❌ No                  |
| Use case                | Share structure + behavior | Define contract only    |

## When to Use Which?
- Use abstract classes when:
  - You need shared implementation or common base behavior
  - There’s a clear IS-A relationship (e.g., Vehicle -> Car)
- Use interfaces when:
  - You need pure abstraction
  - You want to decouple functionality
  - You need multiple behavior types (e.g., ILog, ISerializable, IDisplayable)

## Design Patterns that Use Abstraction
- Factory Pattern (abstract factory, interface-based factory)
- Strategy Pattern (interfaces for interchangeable logic)
- Template Method Pattern (abstract class with fixed workflow and overridable steps)
