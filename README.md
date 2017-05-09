# Applied Computing Revision Notes
A set of notes on the topics that are going to be present on the exam.

**WARNING**: May contain **humor**, **profanities** and **palm oil**. For allergens see ingredients in **bold**.  

# Table of Contents
<!-- TOC start -->
* [Diagrams](#diagrams)
  * [Class Diagram](#class-diagram)
  * [Use Case](#use-case)
  * [Sequence Diagram](#sequence-diagram)
  * [Activity Diagram](#activity-diagram)
* [Objected Oriented Concepts](#objected-oriented-concepts)
* [Relationships Between Objects](#relationships-between-objects)
  * [Implementation](#implementation)
  * [Inheritance](#inheritance)
  * [Dependency](#dependency)
  * [Association](#association)
  * [Aggregation](#aggregation)
  * [Composition](#composition)
* [Access Modifiers](#access-modifiers)
  * [Private](#private)
  * [Default / Package-Private](#default-/-package-private)
  * [Protected](#protected)
  * [Public](#public)
* [Data Types](#data-types)
  * [Primitive vs Compound types](#primitive-vs-compound-types)
  * [Primitive types (Java)](#primitive-types-(java))
    * [Integers](#integers)
    * [Floating Points](#floating-points)
    * [Characters](#characters)
    * [Boolean](#boolean)
  * [Generics](#generics)
  * [Wrapper Classes](#wrapper-classes)
* [Abstract Data Structures](#abstract-data-structures)
  * [Collections](#collections)
  * [Arrays](#arrays)
  * [Lists](#lists)
    * [Array Lists](#array-lists)
    * [Linked Lists](#linked-lists)
  * [Queues](#queues)
  * [Stacks](#stacks)
  * [Sets](#sets)
  * [Trees](#trees)
    * [Binary Search Trees](#binary-search-trees)
  * [Maps](#maps)
    * [Hash Maps](#hash-maps)
    * [Hash Function](#hash-function)
* [Search](#search)
  * [Linear Search](#linear-search)
  * [Binary Search](#binary-search)
* [Sorting](#sorting)
  * [Bubble Sort](#bubble-sort)
  * [Insertion Sort](#insertion-sort)
  * [Selection Sort](#selection-sort)
  * [Shell Sort](#shell-sort)
  * [Quick Sort](#quick-sort)
  * [Merge Sort](#merge-sort)
* [Memory Allocation](#memory-allocation)
* [Characters Encoding](#characters-encoding)
  * [ASCII](#ascii)
  * [Unicode](#unicode)
* [Compression](#compression)
* [Lifecycle Models](#lifecycle-models)
<!-- TOC end -->

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

**RTFG**! Read the fucking glossary: <http://asch.org.uk/programming/oop/glossary.html>.

And while you're there happily clicking links, you can have a read at this too: <http://datastruct.hnd-computing.info>. 


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
A set is an _Abstract Data Type_ that can store unique value without a particular order. More or less like a set of cards 🃏. They represent the mathematical concept of a set, and as such have the following mathematical operations:

* **Union** - Joins two Sets.

![Union](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Venn0111.svg/330px-Venn0111.svg.png)
* **Intersection** - Returns the elements that are present in both Sets.

![Intersection](https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Venn0001.svg/330px-Venn0001.svg.png)
* **Difference** - Returns the elements in B that are not in A.
* **Subset** - A predicate that tests whether all the elements in A are in B.

## Trees
A tree is an _Abstract Data Type_ somewhat similar to a linked list, but has more than one _node_ element and they are called _children_. The starting element is called _root_. A node with no children is called _leaf_. Not sure whether we're talking about computer science or botany. Each node can have just one parent. 

![tree](https://upload.wikimedia.org/wikipedia/commons/f/f7/Binary_tree.svg)

They are particularly useful for storing hierarchic structures.

### Binary Search Trees
A _Binary Search Tree_ (BST) is a specific tree structure used to store sorted data. The node to the **left** contains a **smaller** value than the current node, and the one on the **right** a **bigger** one. For such reason BST can only contain *comparable* values, and no duplicates. They are very efficient in searching, because they are designed to work well with the [binary search](binary-search).

A BST might not be **balanced**, i.e. having most of the values on one side, and that degenerates the search performances down to linear search (a [linked list](#linked-lists) can be thought as a degenerated tree). For such reason it's important to **rebalance** the BST to maximise the benefits. A _**Red-black tree**_, not only comes very handy for Christmas, but also self-balances itself when a new item is added to keep search always efficient. The _red-black_ tree is not the only kind of self-balancing binary tree, but it's the only with a fancy name easy to remember.

## Maps
A map, also known as _associative array_, _symbol table_ or _dictionary_, is an _Abstract Data Type_ composed of a collection of (key, values) pairs. Instead of using a numeric index, like an array, you can access the value using a key of generic type.

### Hash Maps
An Hash Map is an implementation of a Map that uses an **hash algorithm** to convert the key into a numerical index to be used in an array, that will ultimately store the data. Each element of the array contains a an array of _buckets_, because the hash function may produce _collisions_.

![hash map](https://upload.wikimedia.org/wikipedia/commons/5/58/Hash_table_4_1_1_0_0_1_0_LL.svg)

### Hash Function
An hash function is a function capable of converting data of arbitrary size to a data of fixed size. One of the most famous hashing function is md5. These are some examples of strings and their md5 hash.

    Hello World     b10a8db164e0754105b7a99be72e3fe5
    Hello World!    ed076287532e86365e841e92bfc50d8c 
    Hillu Wirld!    ab14b509ca8337b71a17e5d8a41b92da 
    42              a1d0c6e83f027327d8461063f4ac58a6
    
As you can see, very similar strings have totally different hashes and that all the hashes have the same length, regardless of the original string.

Small note: md5 is not cryptographically secure. Do not use it for storing passwords or other sensitive information. Seriously, don't. Don't come cryin' to me if you do.


___
# Search
The strategy to find an element in a data set depends on whether the collection is **sorted** or not. If the collection is not sorted, the **linear search** is the only option.
If the data is sorted, __linear search__ is still viable, but **binary search** is way more efficient. 

## Linear Search
Linear search is an algorithm to find an element in a set, iterating throughout all the elements until the wanted element is found.

![linear-search](https://www.tutorialspoint.com/data_structures_algorithms/images/linear_search.gif)

## Binary Search
Binary search is an optimised search algorithm for sorted data. It starts the process at the middle of the set, and then splits the set in half guessing in what half the value would be, and repeats the process till the element is found (or not).
Binary search is extremely efficient to work with **[binary search tree](#binary-search-trees)**, where the middle point is be the **root** of the tree, making it one of the most search-efficient data structure, reason why it is at the core of most database systems.
 
The classical example for binary search is looking for a name in the phone-book. You can either start looking from the first page until you find it, in that case you would using _linear search_ (and you probably are the village idiot), or you can open the book at the middle, and assuming you know the alphabet, evaluate whether the name is in the right or in the left side. Then split the block again in half and chose the right or the left and so on until you find the right page. It's indeed a shame nobody is using actual phone-books anymore, and this example will soon be meaningless.

![binary-search-vs-linear-search](https://blog.penjee.com/wp-content/uploads/2015/04/binary-and-linear-search-animations.gif)


___
# Sorting
As discussed when talking about [search](#search), having a sorted set of values, can dramatically improve **search performances**. Finding the most efficient sorting algorithm is still an open field in computing, mainly because different algorithm performs differently with **sorted**, **almost-sorted**, **reverse-sorted**, **duplicate** and **random** data, and because of the accidental deaths caused by alcohol-driven arguments between computer scientists. Some algorithms (notably the [merge sort](#merge-sort)) are **stable**, i.e. elements with the same key retain the same relative order, while others (most) are **unstable**.

Consider this list of words that needs to be sorted _lexicographically_ (read _alphabetically_ if you don't know what lexo-thing means) based on their first letter.

    peach
    straw
    apple
    spork
    
This would be a stable sorting (note `straw` **before** `spork`):

    apple
    peach
    straw
    spork
    
... while this would not: (note `straw` **after** `spork`)

    apple
    peach
    spork
    straw
    
Both cases are sorted according to the their first letter, in the stable sorting the relative order between elements with the same letter is retained. I still don't know why you'd want that so desperately, but who am I to disagree? I travel the world an the seven seas. Sorting dreams are made of this... ♫ 

## Bubble Sort
Accounted among one the worse banes of humanity sent by the flying-spaghetti-monster, the _bubble sort_ is a very inefficient sorting algorithm that sorts two adjacent elements of the set at a time (_bubble_) until there are no more bubble swaps. Despite being very inefficient, is quicker than other more sophisticated algorithm when sorting almost-ordered sets. Now, do humanity a favor, and forget it exists, thank you.

![bubble-sort](https://upload.wikimedia.org/wikipedia/commons/5/54/Sorting_bubblesort_anim.gif)

## Insertion Sort
Insertion sort is a sorting algorithm that sorts a collection placing (_inserting_) the value in its final position. It involves a lot swaps in the array, because it's constantly pushing most of the elements to insert the current one in the correct position. It is similar to the way most of people sort playing cards in their hand, pick every card from left to right, and place it where it should be.

![insertion-sort](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)

## Selection Sort
Selection sort is an _in-place_ sorting algorithm that divides the array in two portion, a part already sorted and one still to sort.
The algorithm finds the smallest number (hence _selection_) in the array and places it a the beginning, then shrinks the array by one (because the leftmost first value is already sorted) and does the same on smaller portion recursively until the section to sort is just one element. It reduces the number of swaps, it is easy to implement, but in general is not a very efficient sorting algorithm.  

![selection-sort](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

## Shell Sort
Shell sort seems to be a very stupid idea. With that in mind, the Shell sort is a sorting algorithm that claims to be an improvement of the [bubble sort](#bubble-sort), that instead of comparing adjacent elements it compare element at a given _gap_ and swaps them, then reducing the size of the _gap_, till it converges to a normal [bubble-sort](#bubble-sort) (`gap = 1`). It seems to have decent performances on semi-sorted data.

![shell-sort](https://upload.wikimedia.org/wikipedia/commons/d/d8/Sorting_shellsort_anim.gif)

## Quick Sort
Quick sort is an optimised general-purpose sorting algorithm. It works in 3 steps:

1. It chooses an element called _pivot_.
2. Reorders the array so that all the elements smaller than the pivot are on one side (_partition_).
3. Recursively applies the steps above in the two partitions.

When efficiently implemented it is one of the fastest sorting algorithm.

![Quick-Sort](https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)

## Merge Sort
Merge sort is a sorting algorithm that:
 
1. Splits the collection into sub-lists containing just one element;
2. Merges the sub-lists in order;
3. Recursively merges the sorted sub-lists until there is only one sorted list. 

The merge sort if very efficient, but takes a lot of memory, because it needs to create a lot of sub-lists. On the other hand, it is very easy to parallelize, hence it makes full use of modern computer's multithreading capabilities.  
    
![merge-sort](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)


___
# Memory Allocation
* **Static** - Static allocation prepares the memory for your variables when the program starts. The size is **fixed** when the program is created. It applies to global variables, file scope variables, and variables qualified with static defined inside functions.
* **Automatic** - Automatic allocation occurs for (_non-static_) variables defined inside functions, and is usually stored on the _**stack**_. You do not have to reserve extra memory using them, but on the other hand, have also limited control over the lifetime of this memory. E.g: automatic variables in a function are only there until the function finishes.
* **Dynamic** - These variables are dynamically stored in the _**heap**_. You control the exact size and the lifetime of these memory locations, in languages without _garbage collection_ (like C), and if you don't free it, you'll run into _memory leaks_, which may cause your application to crash, since at some point, it cannot allocate more memory. In Java you need to be careful not to leave any references that could interfere with the _garbage collection_, making it assume that you are still using them, and causing more _memory leaks_. Basically, you'll always create memory leaks. That's what stack overflow is for.


___
# Characters Encoding
In computer science, there are two main ways of encoding a binary digit into an visual character: **ASCII** and **Unicode**. 

## ASCII
The **ASCII**, abbreviation for _American Standard Code for Information Interchange_, is a character encoding standard, defined in 1963 (!) by the ANSI (_American National Standards Institute_). Is anybody sensing an elevate rate of America patriotism here, or is it just me? Anyways, it uses `7 bits` than it can encode `128` characters:

* Digits from 0 to 9
* Lowercase and uppercase Latin letters
* Basic punctuation symbols
* A space
* Various non-printable characters and control symbols

Despite being still very widespread, this encoding is slowly being abandoned for the lack characters used in other languages. 

## Unicode
Unicode is a character encoding standard, dated to 1987, that aims to encode all the languages scripts in the world. Now that they are pretty much done with that, even the historical ones, they just keep on adding new useless emojis. 🛴 
The Unicode itself does not specify how many bytes it needs, although its current range can fit in `4 bytes`, and it's left to the implementation specifications. In all Unicode implementations, the first `128` characters are the [ASCII](#ascii) characters for retrocompatiblity reasons.

The most common Unicode encoding is `UTF-8`, that uses just `1 byte` (`8 bits`, hence UTF-**8**) for characters in the range of ASCII, and is so widespread because it has the same size of a plain ol' ASCII character. It can expand up to `4 bytes` in succession, to handle Asian characters and emojis. Keep that in mind next time you'll use an emoji. `UTF-8` is the standard encoding for the _World Wide Web_, and is used for HTML/XML, emails, communication protocols and so on.

Java internally uses `UTF-16`, a `2 bytes` encoding of the Unicode standard. `UTF-16` can expand itself to have other `2 bytes` in succession to represents all the other less-used characters in the Unicode range.

There is also a `UTF-32` encoding, that uses `4 bytes`, and differently from the other versions, it's a fixed length encoding. The main disadvantage is that it takes four times more space than `UTF-8` with no difference in encoded range.

It's important to note that all the encodings above support the whole range (expanding when necessary), the only difference is in their minimum size.

At the time of writing, the Unicode v9.0 contains `128,237` characters. 


___
# Compression
_Coming soon..._
* Lossy vs Lossless
* Image
* Audio
* Video


___
# Lifecycle Models
_Coming soon..._