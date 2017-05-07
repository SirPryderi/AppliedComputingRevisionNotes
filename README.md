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

## Default / Packaged-Private
Methods and attributes that have no visibility modifiers explicitly declared, are treated as _package-private_, and they are visible only by classes in the **same package**. It can be used to share the access of methods and attributes only to a subsystem placed in a package.

## Protected
Methods and attributes marked as _protected_ are visible only by **subclasses** and classes in the **same package**. Why they are visible for classes in the same package remains a mystery to mankind. 

## Public
Methods and attributes marked as _public_ are **globally** visible. This access modifier should be used only for the **API** of your classes.