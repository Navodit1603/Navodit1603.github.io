| [Home](..) |[TPT Notes](.)| [Challenges](../cha) | [Test Prep Plans](../pln) |[Review Tickets](../rev)|

# Tech Talk Notes

## Tech Talk 2

Math Symbols:

* PEMDAS, each operator has its own precedence (priority)
* Add exponent ^ operator with priority 3
* Helper definition for supported operators

```
  private final Map<String, Integer> OPERATORS = new HashMap<>();
  {
  // Map<"token", precedence> 
  OPERATORS.put("*", 3);
  OPERATORS.put("/", 3);
  OPERATORS.put("%", 3);
  OPERATORS.put("+", 4);
  OPERATORS.put("-", 4);
  }
```
```
Math Original Expression (String):

2 + 2
4 * 6 + 3
5 + 1 * 8
(7 + 5) * 9
Tokenization (Array):

[2, +, 2]
[4, *, 6, +, 3]
[5, +, 1, *, 8]
[(, 7, +, 5, ), *, 9]
Reverse Polish Notation (Array, works well with Stack):

[2, 2, +]
[4, 6, *, 3, +]
[5, 1, 8, *, +]
[7, 5, +, 9, *]

```
## Tech Talk 1
### Generics
* We have to create duplicate code for differnet types without genrics.
* Can create objects with generics. Type has to be an object type. Ie: Integer, not int
* Can pass in as parameters. T var
* Good for code reusibility. 
### Linked List
* List which has address for previous values and next values.
* Multiple peices of data is stored in a node.
* Nodes can have the adress of the previous node, the address of the node after and the data that this node contains.
* Memory does not have to be linear.
* Slower to use than a regular list.


## Tech Talk 0
* A data structure is a method of organizing data.
* There are many algorithms for different purposes, and they interact with different data structures. Think of algorithms as dynamic underlying pieces that interact with data structures.
* Data Structures and Algorithms can be written using different paradigms.
* An imperative program consists of commands for the computer to perform to achieve a result. Imperative programming focuses on describing "how" a program code works.
* Object-Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects.
