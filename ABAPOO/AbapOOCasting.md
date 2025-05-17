# Casting in ABAP OO (Up-casting & Down-casting)
- Casting is the process of converting a reference from one class/interface type to another in the class hierarchy.
- There are two main types:
  - Up-casting: Subclass → Superclass (safe, implicit)
  - Down-casting: Superclass → Subclass (explicit, risky if not type-checked)

## Up-Casting (Safe & Implicit)
- You use up-casting when you want to treat a specific object (subclass) as a generic type (superclass/interface).
- Example
  ```abap
  DATA(lo_dog) = NEW zcl_dog( ).
  DATA(lo_animal) TYPE REF TO zcl_animal.
  lo_animal = lo_dog. " Up-casting: OK
  ```
- Why?
  - You can store different subclass objects in a superclass reference
  - Enables polymorphism

## Down-Casting (Explicit & Risky)
- Use down-casting when you know that a superclass reference actually refers to a specific subclass — and you want to use subclass-specific methods or attributes.
- Syntax:
  ```abap
  DATA(lo_dog) = CAST zcl_dog( lo_animal ).
  ```
- CAST class( ref ) ensures explicit casting
- Use RTTI (RTTC), RTTI_IS_INSTANCE_OF, or CASE TYPE OF to be safe
- Dangerous Without Type Check

### Safe Down-Casting Techniques
#### 1. CASE TYPE OF (Recommended)
```abap
CASE lo_animal.
  WHEN TYPE zcl_dog.
    DATA(lo_dog) = CAST zcl_dog( lo_animal ).
    lo_dog->bark( ).
  WHEN TYPE zcl_cat.
    DATA(lo_cat) = CAST zcl_cat( lo_animal ).
    lo_cat->meow( ).
ENDCASE.
```

#### 2. RTTI Type Checking
```abap
IF lo_animal IS INSTANCE OF zcl_dog.
  DATA(lo_dog) = CAST zcl_dog( lo_animal ).
  lo_dog->bark( ).
ENDIF.
```

#### 3. Interfaces Work Similarly
```abap
DATA(lo_vehicle) TYPE REF TO if_vehicle.
lo_vehicle = NEW zcl_car( ).

IF lo_vehicle IS INSTANCE OF zcl_car.
  DATA(lo_car) = CAST zcl_car( lo_vehicle ).
  lo_car->start_engine( ).
ENDIF.
```

## Common Use Cases
- Factory patterns
- Generic handlers working with superclasses or interfaces
- Event handler classes where dynamic types are passed around
- Plug-in systems (casting to check concrete implementation)

## Best Practices
- Always check object type before down-casting
- Keep down-casting minimal — favor polymorphism or interfaces
- Use CASE TYPE or IS INSTANCE OF to avoid runtime errors 
