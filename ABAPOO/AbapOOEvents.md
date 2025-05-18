# Events in ABAP Objects
- allow for loose coupling and asynchronous communication between objects, following the publisher-subscriber (observer) pattern.
- Events allow one object to notify others when something happens — like a button click, status change, etc.
- **RAISE EVENT** = Trigger an event
- **SET HANDLER** = Register a method as an event handler

## Basic Components
- **Event Definition** — EVENTS <event_name>
- **Event Trigger** — RAISE EVENT <event_name>
- **Event Handler Method** — METHODS <method> FOR EVENT <event> OF <class>
- **Handler Registration** — SET HANDLER handler_method FOR object_ref

## Example: Basic Event Handling
### 1. Define an Event in Publisher Class
```abap
CLASS lcl_publisher DEFINITION.
  PUBLIC SECTION.
    EVENTS: status_changed.
    METHODS: change_status.
ENDCLASS.

CLASS lcl_publisher IMPLEMENTATION.
  METHOD change_status.
    WRITE: / 'Status changed in publisher'.
    RAISE EVENT status_changed.
  ENDMETHOD.
ENDCLASS.
```
### 2. Create Handler Class (Subscriber)
```abap
CLASS lcl_subscriber DEFINITION.
  PUBLIC SECTION.
    METHODS: on_status_changed FOR EVENT status_changed OF lcl_publisher.
ENDCLASS.

CLASS lcl_subscriber IMPLEMENTATION.
  METHOD on_status_changed.
    WRITE: / 'Subscriber received the status_changed event'.
  ENDMETHOD.
ENDCLASS.
```
### 3. Register the Event Handler
```abap
START-OF-SELECTION.
  DATA(lo_pub) = NEW lcl_publisher( ).
  DATA(lo_sub) = NEW lcl_subscriber( ).

  SET HANDLER lo_sub->on_status_changed FOR lo_pub.

  lo_pub->change_status( ).
```
### Output:
```text
Status changed in publisher
Subscriber received the status_changed event
```

## Key Points
- Events are instance-specific unless declared with CLASS-EVENTS.
- Use SET HANDLER ... FOR ALL INSTANCES to catch events from any instance.
- Can pass parameters with the event using EXPORTING in RAISE EVENT.

## Event with Parameters
```abap
EVENTS data_changed EXPORTING VALUE(new_value) TYPE string.

RAISE EVENT data_changed EXPORTING new_value = 'ABC'.

METHODS on_data_changed FOR EVENT data_changed OF lcl_publisher
  IMPORTING new_value.

WRITE: / 'New value:', new_value.
```

## Static (Class) Events
- Use CLASS-EVENTS and CLASS-METHODS instead.
  ```abap
  CLASS-EVENTS: status_changed.
  CLASS-METHODS: raise_event.
  
  RAISE EVENT status_changed.
  SET HANDLER class_name=>method FOR ALL INSTANCES.
  ```

## Use Cases
- UI updates on model change
- Background job notification
- Modular system communications (plug-ins)
- Logging/auditing triggers

## Best Practices
- Prefer interfaces for handler registration in reusable designs
- Keep event naming clear and specific
- Avoid unnecessary event chaining to reduce complexity
