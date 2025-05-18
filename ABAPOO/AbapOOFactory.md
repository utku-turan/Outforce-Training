# Factory Pattern in ABAP OO
- A foundational pattern that helps you create objects without exposing the instantiation logic directly to the caller.
- It's highly relevant for decoupling, testability, and extensibility.
- The Factory Pattern provides an interface for creating objects, but lets subclasses or methods decide which class to instantiate.
- Helps to avoid CREATE OBJECT all over the code.
- Promotes abstraction, centralized object creation, and dynamic instantiation.

## Core Elements
| Component                  | Description                                                  |
| -------------------------- | ------------------------------------------------------------ |
| **Factory Class**          | Contains methods to create and return objects                |
| **Interface / Superclass** | Used for return types to support abstraction                 |
| **Consumers**              | Code that uses the factory instead of instantiating directly |

## When to Use
- You want to encapsulate object creation
- You have multiple subclasses and object creation depends on runtime conditions
- For unit testing / mocking (return test doubles)
- For plug-in architectures

## Basic Example
### Step 1: Define Interface (or Abstract Class)
```abap
INTERFACE if_vehicle.
  METHODS drive.
ENDINTERFACE.
```

### Step 2: Define Concrete Classes
```abap
CLASS zcl_car DEFINITION.
  PUBLIC SECTION.
    INTERFACES if_vehicle.
ENDCLASS.

CLASS zcl_car IMPLEMENTATION.
  METHOD if_vehicle~drive.
    WRITE: / 'Driving a car'.
  ENDMETHOD.
ENDCLASS.

CLASS zcl_bike DEFINITION.
  PUBLIC SECTION.
    INTERFACES if_vehicle.
ENDCLASS.

CLASS zcl_bike IMPLEMENTATION.
  METHOD if_vehicle~drive.
    WRITE: / 'Riding a bike'.
  ENDMETHOD.
ENDCLASS.
```

### Step 3: Create Factory Class
```abap
CLASS zcl_vehicle_factory DEFINITION.
  PUBLIC SECTION.
    CLASS-METHODS:
      get_vehicle
        IMPORTING type TYPE string
        RETURNING VALUE(ro_vehicle) TYPE REF TO if_vehicle.
ENDCLASS.

CLASS zcl_vehicle_factory IMPLEMENTATION.
  METHOD get_vehicle.
    CASE type.
      WHEN 'CAR'.
        ro_vehicle = NEW zcl_car( ).
      WHEN 'BIKE'.
        ro_vehicle = NEW zcl_bike( ).
      WHEN OTHERS.
        ro_vehicle = NEW zcl_car( ). " default
    ENDCASE.
  ENDMETHOD.
ENDCLASS.
```

### Step 4: Consume Factory
```abap
DATA(lo_vehicle) = zcl_vehicle_factory=>get_vehicle( type = 'BIKE' ).
lo_vehicle->drive( ).
```

> Output: Riding a bike

## Variations
- Simple Factory (like above)
- Abstract Factory (creates families of related objects)
- Factory Method Pattern (lets subclasses override the creation method)

## Real-World Use Cases
| Use Case              | Description                                             |
| --------------------- | ------------------------------------------------------- |
| Business Rules Engine | Return rule evaluator classes dynamically               |
| Persistence Layer     | Factory returns object handlers for entity types        |
| UI Plugin System      | Return dynamic screen logic implementations             |
| Mocking in Unit Tests | Return test doubles for interface implementations       |
| Adapter Layer         | Return correct 3rd-party connector (e.g., REST vs SOAP) |

## Best Practices
- Always return interface references, not concrete classes
- Keep factory classes stateless
- Useful when combined with Dependency Injection

## Real-life Factory Pattern Scenario
- Invoice Processor selecting a handler dynamically based on invoice type (e.g., Customer Invoice vs Vendor Invoice).
- This demonstrates polymorphism, abstraction, and clean extensibility.

### Scenario: Invoice Processing Factory
Your system must process different types of invoices. Each invoice type (customer, vendor, credit memo, etc.) requires its own logic. Instead of using conditionals (CASE / IF) everywhere, use the Factory Pattern to return the correct processor class.

### 1. Define Common Interface: IF_INVOICE_PROCESSOR
```abap
INTERFACE if_invoice_processor.
  METHODS:
    process_invoice IMPORTING is_invoice TYPE zinvoice,
    get_type RETURNING VALUE(rv_type) TYPE string.
ENDINTERFACE.
```

### 2. Concrete Classes: ZCL_CUST_INVOICE, ZCL_VEND_INVOICE
```abap
CLASS zcl_cust_invoice DEFINITION.
  PUBLIC SECTION.
    INTERFACES if_invoice_processor.
ENDCLASS.

CLASS zcl_cust_invoice IMPLEMENTATION.
  METHOD if_invoice_processor~process_invoice.
    WRITE: / 'Processing customer invoice:', is_invoice-id.
  ENDMETHOD.

  METHOD if_invoice_processor~get_type.
    rv_type = 'CUST'.
  ENDMETHOD.
ENDCLASS.
```
```abap
CLASS zcl_vend_invoice DEFINITION.
  PUBLIC SECTION.
    INTERFACES if_invoice_processor.
ENDCLASS.

CLASS zcl_vend_invoice IMPLEMENTATION.
  METHOD if_invoice_processor~process_invoice.
    WRITE: / 'Processing vendor invoice:', is_invoice-id.
  ENDMETHOD.

  METHOD if_invoice_processor~get_type.
    rv_type = 'VEND'.
  ENDMETHOD.
ENDCLASS.
```

### 3. Factory Class: ZCL_INVOICE_FACTORY
```abap
CLASS zcl_invoice_factory DEFINITION.
  PUBLIC SECTION.
    CLASS-METHODS get_processor
      IMPORTING iv_type TYPE string
      RETURNING VALUE(ro_processor) TYPE REF TO if_invoice_processor.
ENDCLASS.

CLASS zcl_invoice_factory IMPLEMENTATION.
  METHOD get_processor.
    CASE iv_type.
      WHEN 'CUST'.
        ro_processor = NEW zcl_cust_invoice( ).
      WHEN 'VEND'.
        ro_processor = NEW zcl_vend_invoice( ).
      WHEN OTHERS.
        ro_processor = NEW zcl_cust_invoice( ). " Default fallback
    ENDCASE.
  ENDMETHOD.
ENDCLASS.
```

### 4. Data Object: ZINVOICE Structure
```abap
TYPES: BEGIN OF zinvoice,
         id   TYPE char10,
         type TYPE char4,  " e.g., 'CUST', 'VEND'
       END OF zinvoice.
```

### 5. Caller Code (Using the Factory)
```abap
DATA(ls_invoice) = VALUE zinvoice( id = 'INV123' type = 'VEND' ).

DATA(lo_processor) = zcl_invoice_factory=>get_processor( iv_type = ls_invoice-type ).
lo_processor->process_invoice( is_invoice = ls_invoice ).
```

### Output:
```yaml
Processing vendor invoice: INV123
```

### Benefits in This Scenario
| Benefit              | Description                                     |
| -------------------- | ----------------------------------------------- |
| 🔁 Easily Extendable | Just add new processor class and adjust factory |
| 🧼 Decoupled Logic   | Client code doesn’t care which class is used    |
| 🧪 Testable          | Factory can return mocks/stubs during tests     |
| 🧩 Plug-and-Play     | Supports plugin-like dynamic selection          |
