# Applied Computing Revision Notes
A set of notes on the topics that are going to be present on the exam.


___
# Diagrams

## Class Diagram

The class diagram shows the **relationships** between classes, the **attributes and methods**, and their **visibility**, of each class. The structure of the **packages** is introduced as well. That&#39;s part of **UML**, btw.

## Use Case

The use case diagram is a **UML** tool that shows how the **user interacts** with the system, with a list of use cases that fulfils the **functional and non-functional requirements**.

## Sequence Diagram

The sequence diagram is an **interaction** diagram part of the **UML** tools, that shows in what **order** the objects **cooperate** in function of **time**.

## Activity Diagram

The activity diagram is a **UML** tool to describe the logic flow between **activities**, that represents an operation of the system. Basically a **flowchart**, but don't say this around a UML fan.


___
# Objected Oriented Concepts

**RTFG**! Read the fucking glossary: [http://asch.org.uk/programming/oop/glossary.html](http://asch.org.uk/programming/oop/glossary.html)


___
# Relationships Between Objects

![relationships](https://upload.wikimedia.org/wikipedia/commons/9/93/Uml_classes_en.svg)

## Implementation

The implementation/realisation of an interface by an object. The arrow points the interface.

In case it is an external interface, the lollipop notation is used.

## Inheritance

Connects the sub-type to the super-type class, and reflects the _extends_ keyword in Java.

The arrow points the super-type.

## Dependency

A dependency represents a **unidirectional** relationship between two classes, implying that the change of functionality of one may cause **side effects** in the second.

## Association

An association represents the relationship between two objects of **equal magnitude**. It can be both **unidirectional** and **bidirectional** (in that case no arrowheads are used). An example of bidirectional association can be Flight – Plane.

## Aggregation

An aggregation represents the &quot;**has**&quot; relationship between two objects. It is a **stronger** relationship than the association. It is generally used for objects that are collection of others. An example is Crew -&gt; Pilot. It is to note that the Pilot **can exist without** being part of the Crew. The British Airline Pilots Association commends this statement.

## Composition

A composition is a relationship representing an object being strictly part of another, that cannot exist separately. This is used to represent real-life relationships between things that cannot be separated, like an Engine being part of only a Plane.


___
# Access Modifiers
Access modifiers let the developer chose the **scope** of **methods** and **attributes**.

## Private
Methods and attributes marked as _private_ can be seen **only** by implementations of the **same class**. It is useful to prevent uncontrolled access to class-specific methods and attributes. 

## Default / Package-Private
Methods and attributes that have no visibility modifiers explicitly declared, are treated as _package-private_, and they are visible only by classes in the **same package**. It can be used to share the access of methods and attributes only to a subsystem placed in a package.

## Protected
Methods and attributes marked as _protected_ are visible only by **subclasses** and classes in the **same package**. Why they are visible for classes in the same package remains a mystery to mankind. 

## Public
Methods and attributes marked as _public_ are **globally** visible. This access modifier should be used only for the **API** of your classes.


___
# Data Types

## Primitive vs Compound types
- **Primitive data types** are basic types that can be stored in a CPU register. _Integers_, _floats_ and _characters_ are examples of primitive data types.

- **Compound** or **Composite** data types are data types that can be constructed using primitive types and other compound types. _Arrays_, _Struct_ and _Classes_ are examples of compound data types.


## Primitive types (Java)

### Integers
| Type  | byte(s) |  bit(s) |
|------:|:-------:|:-------:|
| byte  | 1       | 8       |
| short | 2       | 16      |
| int   | 4       | 32      |
| long  | 8       | 64      |

### Floating Points
| Type   | byte(s) |  bit(s) |
|-------:|:-------:|:-------:|
| float  | 4       | 32      |
| double | 8       | 64      |

### Characters
| Type   | byte(s) |  bit(s) |
|-------:|:-------:|:-------:|
| char   | 2       | 16      |

### Boolean
The size of a Boolean is not defined, and is left to the implementation of the _Java Virtual Machine_. After some digging around, it seems that the JVM treats a boolean as an integer (`4 byte`), but is able to pack an array of booleans to use `1 byte` per element. 


___
# Abstract Data Structures
## Collections
A collection is an _Abstract Data Type_ that contains elements of the same type. The order in which the elements are returned is not guaranteed to be the same in which the collection was populated.

## Arrays
An array is a consecutive chunk of memory containing an **indexed** collection of objects of the same type. Nearly all programming languages offer native support for arrays. Their size is defined at  cannot change dynamically. 

## Lists
A list is an _Abstract Data Type_ that represents a countable collection of ordered elements of the same type. 

### Array Lists
An Array List is a data structure that is meant to work like a standard _array_, i.e. offering indexed access, but with dynamic allocation, removing the limitation of the fixed size. It offers very good performances when reading and appending, but removing an element or inserting mid-way requires all the other elements to be shuffled.
 
### Linked Lists
A linked list is an ordered data structure that has **no indexed access**, but every node has a reference to the next element. Reaching a given element in the linked linked requires to traverse the whole structure until that point, but removing and or adding an element is very quick, because only one pointer manipulation is required.

![Linked List](https://upload.wikimedia.org/wikipedia/commons/3/37/Singly_linked_list.png)


## Queues
A queue is an ordered data structure where it is only possible to add an element at the bottom of the structure (_**enqueue**_) and remove one from the top (_**dequeue**_). This makes the Queue a _**First-In-First-Out**_ (_**FIFO**_). Often a _peek_ operation is added to check the element on top without removing it.

![Queue](https://upload.wikimedia.org/wikipedia/commons/5/52/Data_Queue.svg)

## Stacks
A stack is an ordered data structure where it is only possible to add an element at the top of the structure (_**push**_) and removing one fro the top of the stack (_**pop**_). This makes the Stack a _**First-In-Last-Out**_ (_**FILO**_). Often a _peek_ operation is added to check the element on top without removing it.

![Stack](https://upload.wikimedia.org/wikipedia/commons/b/b4/Lifo_stack.png)

## Sets
A set is an _Abstract Data Type_ that can store unique value without a particular order. They represents the mathematical concept of a set, and as such have the following mathematical operations:

* **Union** - Joins two Sets.

![Union](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Venn0111.svg/330px-Venn0111.svg.png)
* **Intersection** - Returns the elements that are present in both Sets.

![Intersection](https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Venn0001.svg/330px-Venn0001.svg.png)
* **Difference** - Returns the elements in B that are not in A.
* **Subset** - A predicate that tests whether all the elements in A are in B.
