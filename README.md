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

In case it is an external interface, the lollipop 🍭 notation is used.

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

A composition is a relationship representing an object being strictly part of another, that cannot exist separately. This is used to represent real-life relationships between things that cannot be separated, like an Engine being part of only a Plane. What's the matter with all these aeronautical examples? Did you want to be a pilot or something? Make up your mind, seriously.


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
| Type  | bytes   |  bits   |
|------:|:-------:|:-------:|
| byte  | 1       | 8       |
| short | 2       | 16      |
| int   | 4       | 32      |
| long  | 8       | 64      |

### Floating Points
| Type   | bytes   |  bits   |
|-------:|:-------:|:-------:|
| float  | 4       | 32      |
| double | 8       | 64      |

### Characters
| Type   | bytes   |  bits   |
|-------:|:-------:|:-------:|
| char   | 2       | 16      |

### Boolean
The size of a Boolean is not defined, and is left to the implementation of the _Java Virtual Machine_. After some digging around, it seems that the JVM treats a boolean as an integer (`4 byte`), because CPU are optimised for working with integers, but is able to pack an array of booleans to use `1 byte` per element. Smart, innit?

## Generics
In Java it possible to create classes and method that accepts a **generic type** instead of a specific one. For instance, a _Collection_ is designed to work with every type, so an instance of collection is able to store an arbitrary data type. 
The following example shows how a generic class is implemented in Java.

```java
/**
 * Generic Box class.
 * @param <T> the type of the value being boxed
 */
public class Box<T> {
    // T stands for "Type"
    private T t;

    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```

Note that it is not possible to store primitive data type as a generic, on the other hand you can to use one of the available [wrapper classes](#wrapper-classes).

## Wrapper Classes
Java offers a set of wrapper classes that contains primitives. They add a few utility methods as well.

| Primitive |  Wrapper  |
|:---------:|:---------:|
| boolean   | Boolean   |
| char      | Character |
| byte      | Byte      |
| short     | Short     |
| int       | Integer   |
| long      | Long      |
| float     | Float     |
| double    | Double    |

Additionally, Java compilers automatically _box_ the generic to the wrapper class, and vice versa (_unbox_).
  
For instance, thw following will compile successfully:
 
```java
class test {
  public static void main(String args[]){
     // Boxing
     int a = 42;
     Integer b = a;
     
     b = 40 + 2;
     
     // Unboxing
     int c = b;
     
     c = b - 2;
  }
}
```
  
Santa's elves could use some wrapper classes too! 🎁


___
# Abstract Data Structures
## Collections
A collection is an _Abstract Data Type_ that contains elements of the same type. The order in which the elements are returned is not guaranteed to be the same in which the collection was populated.

## Arrays
An array is a contiguous chunk of memory containing a directly **indexed** collection of objects of the same type. The position is memory is calculated multiplying the size of the element by the index and summed with the index of the first element in the array. Nearly all programming languages offer native support for arrays. Their size is defined at cannot change dynamically. On the other hand indexed access is very fast and does not depend on the size of the array. Adding an element mid-way or deleting an element causes the rest of the elements to be shuffled.

## Lists
A list is an _Abstract Data Type_ that represents a countable collection of ordered elements of the same type. 

### Array Lists
An Array List is a data structure that is meant to work like a standard _array_, i.e. offering indexed access, but with dynamic allocation, removing the limitation of the fixed size. It offers very good performances when reading and appending, but removing an element or inserting mid-way requires all the other elements to be shuffled.
 
### Linked Lists
A linked list is an ordered _Abstract Data Type_ that has **no indexed access**, but every node has a reference to the next element. A train basically, choo-choo!. The first element of the linked list is called _head_. The last element is called _tail_, and usually points to _null_ in most of the implementations. Reaching a given element in the linked linked requires to traverse the whole structure until that point, but removing and or adding an element is very quick, because only one pointer manipulation is required. They are generally less efficient than arrays on reading, but performs better if there are a lot of insertions and deletions.

![Linked List](https://upload.wikimedia.org/wikipedia/commons/3/37/Singly_linked_list.png)


## Queues
A queue is an ordered data structure where it is only possible to add an element at the bottom of the structure (_**enqueue**_) and remove one from the top (_**dequeue**_). This makes the Queue a _**First-In-First-Out**_ (_**FIFO**_). Often a _peek_ operation is added to check the element on top without removing it. More or less like when you queue to get on a bus. Unless you live in Italy, in that case is more like a traversing a tree or something.

![Queue](https://upload.wikimedia.org/wikipedia/commons/5/52/Data_Queue.svg)

## Stacks
A stack is an ordered data structure where it is only possible to add an element at the top of the structure (_**push**_) and removing one fro the top of the stack (_**pop**_). This makes the Stack a _**First-In-Last-Out**_ (_**FILO**_). Often a _peek_ operation is added to check the element on top without removing it. Basically a stack of pancakes 🥞.

![Stack](https://upload.wikimedia.org/wikipedia/commons/b/b4/Lifo_stack.png)

## Sets
A set is an _Abstract Data Type_ that can store unique value without a particular order. More or less like a set of cards 🃏. They represents the mathematical concept of a set, and as such have the following mathematical operations:

* **Union** - Joins two Sets.

![Union](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Venn0111.svg/330px-Venn0111.svg.png)
* **Intersection** - Returns the elements that are present in both Sets.

![Intersection](https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Venn0001.svg/330px-Venn0001.svg.png)
* **Difference** - Returns the elements in B that are not in A.
* **Subset** - A predicate that tests whether all the elements in A are in B.

## Trees

## Maps

# Search

# Sorting
## Bubble Sort
## Insertion Sort
## Selection Sort
## Merge Sort

# Memory Allocation
* Dynamic
* Automatic
* Static

# Encoding
* ASCII
* UNICODE

# Compression
* Lossy vs Lossless
* Image
* Audio
* Video

# Lifecycle Models
