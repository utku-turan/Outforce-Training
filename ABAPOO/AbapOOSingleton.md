# Singleton Design Pattern
- ensures that only one instance of a class exists in the system during runtime and provides global access to that instance.
- A singleton is a class that:
  - Can only be instantiated once
  - Provides a global point of access
  - Controls access to shared resources or configurations

## When to Use It
- Central configuration managers
- Logging classes
- Shared caches or state containers
- Global business context or session management

## Core Implementation Structure
| Component           | Role                                  |
| ------------------- | ------------------------------------- |
| Static attribute    | Stores the single instance            |
| Static method       | Provides access and instantiates once |
| Private constructor | Prevents external instantiation       |

## Basic Singleton Example
```abap
CLASS zcl_singleton DEFINITION CREATE PRIVATE.
  PUBLIC SECTION.
    CLASS-METHODS:
      get_instance RETURNING VALUE(ro_instance) TYPE REF TO zcl_singleton.
    METHODS:
      say_hello.
  PRIVATE SECTION.
    CLASS-DATA:
      so_instance TYPE REF TO zcl_singleton.
ENDCLASS.
```

```abap
CLASS zcl_singleton IMPLEMENTATION.
  METHOD get_instance.
    IF so_instance IS INITIAL.
      so_instance = NEW zcl_singleton( ).
    ENDIF.
    ro_instance = so_instance.
  ENDMETHOD.

  METHOD say_hello.
    WRITE: / 'Hello from the singleton'.
  ENDMETHOD.
ENDCLASS.
```

```abap
DATA(lo_singleton) = zcl_singleton=>get_instance( ).
lo_singleton->say_hello( ).
```

> Output: Hello from the singleton

## Key Concepts
| Concept          | Explanation                                            |
| ---------------- | ------------------------------------------------------ |
| `CREATE PRIVATE` | Prevents external `NEW` or `CREATE OBJECT`             |
| `CLASS-DATA`     | Static instance holder                                 |
| `get_instance`   | Lazy-instantiates the class and returns the single ref |

## Real-World Use Cases in ABAP
| Use Case                | Description                              |
| ----------------------- | ---------------------------------------- |
| Logging Utility         | One logger writes to log table or spool  |
| Message Collector       | Accumulates messages during process      |
| Session Context Manager | Keeps user/session-wide data             |
| Configuration Reader    | Loads data from DB/customizing only once |
| Shared Cache Manager    | Centralized cache across components      |

## Best Practices
- Avoid using Singletons for business logic — use only for infrastructure-related responsibilities.
- Make the constructor private or protected
- Combine with interfaces for unit testing flexibility
- Not thread-safe by default — for multi-threaded scenarios (e.g., in BTP), take extra care


## Real-World Use Case: Global Message Handler (Singleton)
- a Global Message Handler is a classic and practical Singleton use case in ABAP.
- It’s widely used to collect, centralize, and display messages (errors, warnings, success, etc.) across a process without tightly coupling all the classes to message logic.

### Scenario
- You have a complex process (e.g., sales order validation) involving multiple classes.
- Each class may raise messages — instead of each one handling message display or persistence, they delegate to a singleton Message Handler.

### Step-by-Step Implementation
#### 1. Define the Message Handler Class (Singleton)
```abap
CLASS zcl_msg_handler DEFINITION CREATE PRIVATE.
  PUBLIC SECTION.
    TYPES: ty_message TYPE bapiret2.

    CLASS-METHODS:
      get_instance RETURNING VALUE(ro_instance) TYPE REF TO zcl_msg_handler.

    METHODS:
      add_message IMPORTING is_msg TYPE ty_message,
      get_messages RETURNING VALUE(rt_msgs) TYPE STANDARD TABLE OF ty_message,
      clear_messages.

  PRIVATE SECTION.
    CLASS-DATA: so_instance TYPE REF TO zcl_msg_handler.
    DATA: mt_messages TYPE STANDARD TABLE OF ty_message.
ENDCLASS.
```

#### 2. Implementation
```abap
CLASS zcl_msg_handler IMPLEMENTATION.
  METHOD get_instance.
    IF so_instance IS INITIAL.
      so_instance = NEW zcl_msg_handler( ).
    ENDIF.
    ro_instance = so_instance.
  ENDMETHOD.

  METHOD add_message.
    APPEND is_msg TO mt_messages.
  ENDMETHOD.

  METHOD get_messages.
    rt_msgs = mt_messages.
  ENDMETHOD.

  METHOD clear_messages.
    CLEAR mt_messages.
  ENDMETHOD.
ENDCLASS.
```

#### 3. Using the Singleton in Other Classes
```abap
DATA(lo_msg_handler) = zcl_msg_handler=>get_instance( ).

lo_msg_handler->add_message( VALUE #( type = 'E' id = 'ZMYMSG' number = '001' message = 'Invalid material number.' ) ).
```

#### 4. At the End of the Process — Retrieve and Show Messages
```abap
DATA: lt_msgs TYPE STANDARD TABLE OF bapiret2.

lt_msgs = zcl_msg_handler=>get_instance( )->get_messages( ).

LOOP AT lt_msgs INTO DATA(ls_msg).
  MESSAGE ls_msg TYPE ls_msg-type.
ENDLOOP.
```

### Best Practices
- Optionally use IF_MESSAGE_HANDLER interface for test mocking
- Implement log persistence if required (e.g., write to a DB table)
- Support message grouping or context-based filtering if needed
