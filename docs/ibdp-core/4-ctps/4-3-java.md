---
layout: default
title: Introduction to Java
parent: Programming
grand_parent: IB DP Core
nav_order: 3
---
Core
{: .label .label-blue }

# Java Basics

## How it works
Java code is written as plain text documents with a file ending of _.java_ which tells the compiler that the file contains Java code. The compiler will run through the _.java_ files and compile them to byte code which are saved as text files with the same names as the code files but _.class_ file endings - one _.class_ file for each _.java_ file. The _.class_ files are then interpreted by the JVM into binary code which is then run on the system. If desired the code can be packaged up as a stand-alone application, but this may require some other steps and processes, and is often platform dependent.

The most basic way to do this, and the recommended way for most people learning to code for the first time is using a plain text editor and the a command line interface (CLI) like the terminal on the Mac and Windows command line or other command line programmes. The current version Java Development Kit (JDK) Standard Edition (SE) for the platform needs to be downloaded and installed on the system first. When doing this follow the instructions for your specific platform and set path variables etc. as instructed.

![Java logo.]({{site.baseurl}}/assets/images/4_ctps/logo_java.png)  

<span class="fs-2">
[Oracle JDK SE Download](https://www.oracle.com/uk/java/technologies/javase-downloads.html){: .btn .btn-outline }</span>

<span class="fs-2">
[Java SE 14 Installation Guide](https://docs.oracle.com/en/java/javase/14/install/overview-jdk-installation.html?xd_co_f=27229c0d-25e3-478d-b22e-5910b8974ab8#GUID-8677A77F-231A-40F7-98B9-1FD0B48C346A){: .btn .btn-outline }</span>

![Screenshot of HellowWorld being run via the terminal.]({{site.baseurl}}/assets/images/4_ctps/terminal.png)
##### Typical set up using a text editor and terminal to code and run Java apps.
<br>
However once they understand how the writing, compiling and running of Java code works, most people move to using an integrated development environment (IDE) which usually enables organisation of files, has a built-in editor, it's own compiler, enhanced debugging capability, built-in run-time environment and lots of other development functionality. Popular examples used for Java are Eclipse, NetBeans and Visual Studio Code. However the complexities of these environments frequently get in the way and confuse novice coders.

There is a cross-platform IDE that has been specifically designed for learning to code Java using objects by the Imperial College CS Department, called BlueJ. You need to download and use this for class exercises so everyone is using the same IDE and it is practical to provide support. You still need to download and install the Java JDK as described above.

![BlueJ logo.]({{site.baseurl}}/assets/images/4_ctps/logo_bluej.png)  

<span class="fs-2">
[Download BlueJ](https://www.bluej.org){: .btn .btn-outline }</span>

BlueJ has an excellent user guide and tutorials available, including videos, to help you get started with using it.

## Structuring code
From the start be disciplined about how you write and structure code. You will be penalised in your IA if you fail to follow conventions and don't structure your code properly. This may not be what every coder does but you must.

**Strict dos:**

* each class must be in a separate file
* every _.java_ file must have a comment at the top that contains a description of the class, the author designation and a version number:

```java
/**
 * NEASolution contains the main method and controls the program.
 *
 * @author GF
 * @version 1.1
 */
```

The @ labels are used when parsing the code for automatic documentation
* use meaningful names for classes, variables and methods
* names cannot have spaces in them and they must use "camel case" where each word in the name begins with an uppercase letter and the rest of the word is lowercase
* class names must begin with uppercase letters and variable and method names with lowercase

```java
ClassName
variableName
methodName
```

* the name of the file must be an exact match to the name of the class it contains, including the cases of the letters
* code must be indented correctly - BlueJ helps with this as it has automatic code formatting and colour highlighting
* comment your code generously - this helps someone else understand the code and you to remember what you were doing and how you were thinking when you look back on code

## Features of Java

Java syntax is case sensitive - mistakes with case are common causes of errors and can be difficult to pick up when debugging.

Every line must end with a semi-colon:

```java
System.out.println("Hi World!");
```

### Data Types

Primitive data types in Java:
* byte
  - 8-bit signed integer
  - range: -128 - 127 (inclusive)
  - useful for saving memory in large arrays
  - used in place of _int_ where their limits help to clarify code

```java
byte small_number;
small_number = 10;
//or
byte small_number = 10;
```

* int
  - 32-bit signed integer
  - range: −2,147,483,648 to 2,147,483,647

```java
int a_number;
a_number = 187459;
//or
int a_number = 1874459;
```

* short
  - 16-bit signed integer
  - range: -32,768 - 32,767 (inclusive)
  - as with _byte_ - used to save memory in large arrays

```java
short medium_number;
medium_number = 2471;
//or
short medium_number = 2471;
```

* long
  - 64-bit signed integer
  - range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807


```java
long big_number;
big_number = 110726982471;
//or
long big_number = 110726982471;
```

* float
  - used for decimal numbers
  - single-precision 32-bit IEEE 754 floating point

```java
float a_decimal;
a_decimal = 3.492;
//or
float a_decimal = 3.492;
```

* double
  - double-precision 64-bit IEEE 754 floating point

* char
  - character
  - 16-bit
  - Unicode character
  - default = '\u0000'   (NULL)

```java
char a_letter;
a_letter = 'a';
//or
char a_letter = '\u0061';
```

* boolean
  - true or false
  - default = false

```java
boolean a_flag;
a_flag = true;
//or
boolean a_flag = true;
```

Other data objects
* String
    - not a primitive data type
    - object of type java.lang.String - hence the uppercase S
    - default = NULL

```java
String a_word;
a_word = "Hello World";
//or
String a_word = "Hello World";
```

Data structures
* arrays
  - data structure to hold primitive data types or objects
  - elements are indexed (and referred to) from 0, 1, 2, … n
  - always remember the indices start at 0
  - elements must all be the same type
  - size fixed at time of declaration - cannot be altered later

```java
int[] intArray = {24, 81, 35, 62};
String[] stringArray = {"Jane", "James", "Karen", "Joe"};
```

Java also has the following dynamic data structures:
* Vectors
* Dictionary
* Hashtable
* Stack
* collections

Dynamic data structures can vary the number of elements after they have been instantiated and most allow storage of different primitive or object data elements.

### Java Operators
<br>
**Arithmetic operators**

| Operator | Action                                                 |
|:---------|:-------------------------------------------------------|
| \+       | Additive operator (also used for String concatenation) |
| \-       | Subtraction operator                                   |
| \*       | Multiplication operator                                |
| \        | Division operator                                      |
| %        | Remainder operator                                     |

Below is an example of how the arithmetic operators work:

```java
int result = 20 + 3;
// result is now 23
result = result - 5;
// result is now 18
result = result * 2;
// result is now 36
result = result / 3;
// result is now 12
result = result % 7;
// result is now 5
System.out.println
  ("Final Result = " + result);
```

Output:

![Console output from operator example code.]({{site.baseurl}}/assets/images/4_ctps/output_operator.png)  

**Unary operators**

| Operator | Action                                                       |
|:---------|:-------------------------------------------------------------|
| \+       | Unary plus operator - indicates positive value (numbers positive by default)|
| \-       | Unary minus operator - negates an expression                 |
| \++      |Increment operator - increments a value by 1                  |
| \--      | Decrement operator - decrements a value by 1                 |
| !        | Logical complement operator - inverts the value of a boolean |

<br>

**Assignment**

| Operator | Action       |
|:---------|:-------------|
| =        | assign value |

<br>

**Equality/relation**

| Operator | Action                    |
|:---------|:--------------------------|
| ==       | equal to                  |
| !=       | not equal to              |
| \>       | greater than              |
| \>=      | greater than or equal to  |
| \<       | less than                 |
| \<=      | less than or equal to     |

<br>

Below is an example of how these are used:

```java
int v1 = 1;
int v2 = 2;
if(v1 == v2)
	System.out.println("v1 == v2");
if(v1 != v2)
	System.out.println("v1 != v2");
if(v1 > v2)
	System.out.println("v1 > v2");
if(v1 < v2)
	System.out.println("v1 < v2");
if(v1 <= v2)
	System.out.println("v1 <= v2");
```

Output:

![Console output from relationship example code.]({{site.baseurl}}/assets/images/4_ctps/output_relation.png)

<br><br>
**Conditional operators**

| Operator | Action                                         |
|:---------|:-----------------------------------------------|
| &&       | Conditional-AND                                |
| \|\|     | Conditional-OR                                 |
| ?:       | Ternary (shorthand for if-then-else statement) |

<br>
**Type comparison operator**

| Operator  | Action                                         |
|:----------|:-----------------------------------------------|
| instanceof| Compares an object to a specified type       |

<br>

### Data Structures
<br>
**Array**

The primative data type array is a single dimensional container object which holds a fixed number of values of a single type.

![Diagram showing elements in an array.]({{site.baseurl}}/assets/images/4_ctps/array_diagram.png)

Types of arrays

```java
int[] anArrayOfIntegers;
byte[] anArrayOfBytes;
long[] anArrayOfLongs;
float[] anArrayOfFloats;
double[] anArrayOfDoubles;
boolean[] anArrayOfBooleans;
char[] anArrayOfChars;
String[] anArrayOfStrings;
Object[] anArrayOfObjects
```

The java.util.Arrays class contains various static methods for sorting and searching arrays, comparing arrays, and filling array elements.

These methods are overloaded for all primitive types.

There are 2 ways to create arrays

Declare the array and then fill it

```java
String[] myStringArray = new String[4];
myStringArray[0] = "Zoe";
myStringArray[1] = "Mike";
myStringArray[2] = "Mary";
myStringArray[3] = "Luke";
```

Declare and fill it all in one go

```java
String[] myStringArray = {"Zoe", "Mike", "Mary", "Luke"};
```

When the array is created the memory for it is allocated.

```java
String[] myStringArray = new String[4];
```

When the array is declared, spare memory slots of appropriate size are allocated to be used for the elements.

![Diagram showing how elements in an array are held in memory part 1.]({{site.baseurl}}/assets/images/4_ctps/array_memory_1.png)

When the elements are filled with data that data is stored in the corresponding memory slot.

![Diagram showing how elements in an array are held in memory part 2.]({{site.baseurl}}/assets/images/4_ctps/array_memory_2.png)

When the element is subsequently called, a pointer to the memory slot identifies the appropriate data and this is returned as the array element.

![Diagram showing how elements in an array are held in memory part 3.]({{site.baseurl}}/assets/images/4_ctps/array_memory_3.png)

Arrays are usually used for looping through data series.

```java
//declare and create the array
String[] myStringArray = {"Zoe", "Mike", "Mary", "Luke"};
String name = "";

//loop through the array
for (int i = 0; i < myStringArray.length; i++) {
//get each element in turn and do something with it
       name = myStringArray[i];
       System.out.println("Name in element " + i + " is " + name);
}
```

Output would be:

![Screenshot of console output of code.]({{site.baseurl}}/assets/images/4_ctps/output_array.png)

## Structure of a Java Program

The following is the basic HelloWorld app.

```java
/* The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 * @author My name
 */
public class HelloWorldApp {
    public static void main(String[] args) {
        //Display the string
        System.out.println("Hello World!");
    }
}
```

This creates a class called `HelloWorldApp`. When that class is instantiated when the program is run, an object of type `HelloWorldApp` is created and all the variables and methods in the object can be used.

Good practice dictates you should always have a header comment with a description of what the class does and the author name in it. Mutli-line comments are started with `/*` and ended with `*/`.

The class name needs to be declared as `public` so it can be accessed from outside the class to create objects from it, and also needs the `class` declaration in it.

The body of the class is contained with curly braces `{` and `}`. Not closing bracket pairs is a common source of error. BlueJ will help avoid this or identify it when it happens.

The main class of a program contains the `main` method which initiates the program. This must be declared with the `public`, `static` and `void` keywords. Again `public` allows access from outside the class, in this case the operating system. _Static_ is a keyword in Java known as an _access modifier_ that is used to define the class member that can be used independently of any object of that class. Used in the `main` method, it means that this method can be run before any instance of that class object has been instantiated - allowing the program to start running in the first place.



### A short recap on keywords

But there are about 50 reserved words, called keywords, that you are not allowed to use as variable names. These words include public, class, static, void, and int, which are used by the compiler to analyse the structure of the program.

You can find the complete list of keywords at the link below, but you don’t have to memorise them as most programming editors provide “syntax highlighting”, which makes different parts of the program appear in different colours.

<span class="fs-2">
[List of Java Keywords](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html){: .btn .btn-outline }</span>
