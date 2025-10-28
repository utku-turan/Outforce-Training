# Object-Oriented ABAP (OOABAP): Core Concepts
- ABAP OO brings modern object-oriented principles to ABAP, aligning it with OOP languages like Java and C++.
- Fully integrated into SAP NetWeaver AS ABAP — supports encapsulation, inheritance, polymorphism, interfaces, and events.

## 0. Basics
- **Class:** Blueprint of an object. Can be global (SE24) or local.
- **Object:** Runtime instance of a class. Created with CREATE OBJECT or NEW.
- **Method:** Function/procedure within a class.
- **Attribute:** Data member (variable) of a class.
- **Constructor:** Special method for object initialization (CONSTRUCTOR).
- **Visibility:** Public, Protected, Private — controls access to members.
- For details, please check [**here**](/ABAPOO/AbapOOBasics.md).

## 1. Fundamental Principles
- [**Encapsulation:**](/ABAPOO/AbapOOEncapsulation.md) Use PRIVATE, PROTECTED, and PUBLIC visibility to safeguard internal object state.
- [**Abstraction:**](/ABAPOO/AbapOOAbstraction.md) Hide implementation details through abstract classes or interfaces.
- [**Inheritance:**](/ABAPOO/AbapOOInheritance.md) Reuse code by extending superclasses using INHERITING FROM.
- [**Polymorphism:**](/ABAPOO/AbapOOPolymorphism.md) Call subclass-specific behavior via superclass references (via METHOD REDEFINITION, interfaces).
- [**Casting:**](/ABAPOO/AbapOOCasting.md) Down-casting and up-casting between super/sub-classes or interfaces.
- [**Instance vs. Static:**](/ABAPOO/AbapOOInstanceVsStatic.md) fundamental for designing reusable and scalable classes.

## 2. Key Language Features
- CLASS ... DEFINITION/IMPLEMENTATION
- METHODS, CONSTRUCTOR, CLASS-METHODS, ALIAS, RAISING
- Visibility Sections: PUBLIC, PROTECTED, PRIVATE
- CREATE OBJECT
- [**Events: RAISE EVENT, SET HANDLER**](/ABAPOO/AbapOOEvents.md)
- Interfaces: INTERFACES, IF_..., multiple interface implementation
- Abstract and Final Classes
- Objects are referenced using TYPE REF TO.

## 3. Advanced Constructs
- [**Exception Handling & Exception Classes**](/ABAPOO/ABAPOOException.md) (CX_STATIC_CHECK, CX_NO_CHECK, CX_DYNAMIC_CHECK)
- [**Factory Pattern**](/ABAPOO/AbapOOFactory.md) for controlled object creation
- [**Singleton Pattern**](/ABAPOO/AbapOOSingleton.md) for shared instance
- [**Strategy Pattern**](/ABAPOO/AbapOOStrategy.md) for selecting algorithms or business rules dynamically at runtime
- [**Adapter Pattern**](/ABAPOO/AbapOOAdapter.md) for incompatible classes to work together by converting the interface
- [**Decorator Pattern**](/ABAPOO/AbapOODecorator.md) for adding additional behavior to an object dynamically by wrapping it with other objects
- Dependency Injection using interfaces (e.g., in unit testing or service facades)
- Test Classes integrated using FOR TESTING

## 4. OOABAP in Modern SAP Development
- RAP Framework: Fully OO-based (behavior classes, data models)
- Clean ABAP Guidelines: Promote encapsulation, interface use
- ABAP Cloud: Requires strict OO design, modular code
- Unit Testing: Strong reliance on classes/interfaces for testability

## 5. Tools and Aids
- ADT (Eclipse): Best OO support (navigation, refactoring)
- SE24 / SE80: Legacy class editing
- CL_ABAP_OBJECTDESCR, RTTS for runtime type analysis
- Class Builder, Interface Builder
- ABAP Unit Framework for OO testing

## 6. Important SAP Standard Classes & Interfaces
- CL_GUI_*: SAP GUI controls (Tree, ALV, etc.)
- IF_T100_MESSAGE: Message handling
- IF_BADI_INTERFACE, IF_EX_*: For BADIs
- IF_OO_ADT_CLASSRUN: Entry point for ADT classes
- CL_ABAP_TYPEDESCR, CL_ABAP_REF_DESC: Runtime type inspection

## 7. Clean Code Practices in OOABAP
- Small, focused classes/methods
- Favor composition over inheritance
- Avoid global state (DATA in global scope)
- Use interfaces for abstraction and testing
- Clear exception handling strategy (TRY...CATCH, meaningful messages)

## 8. Real-World Usage in SAP
- BOPF/RAP Frameworks
- ALV OO (CL_GUI_ALV_GRID)
- File handling (CL_GUI_FRONTEND_SERVICES)
- Dynamic programming (RTTS, CL_ABAP_TYPEDESCR)
- Data providers for Fiori or APIs

## 9. Transaction Codes
- **SE24** Global Class Builder
- **SE80** Repository Navigator
- **SE84** Object Navigator
- **SE18/SE19** BAdIs (based on OO)

## 10. Modern ABAP Features (Post 7.40)
- NEW, DATA(lo_obj) = NEW zcl_class( )
- -> for method calls
- Inline declarations
- Expressions inside methods
- Exception classes (RAISE EXCEPTION NEW zcx_error(...))

## 11. Best Practices
- Use interfaces for decoupling
- Prefer composition over inheritance
- Keep private attributes really private
- Avoid tightly coupled class design
- Always handle exceptions gracefully
- Use OO patterns (Factory, Strategy, etc.) where applicable
