---
layout: default
title: Intro to Programming
parent: Programming
grand_parent: IB DP Core
nav_order: 2
---
Core
{: .label .label-blue }

# Introduction to Programming

## Objectives
* nature of programming languages
* operations of a computer - fundamental, compound operations of a computer
* computer languages - essential features, higher level, translation from language to machine code
* use of programming languages
* defining the terms and operators
* use of variables, constants and operators in algorithms
* algorithms using loops, branching
* collections - characteristics, applications, access methods
* sub-programmes, collections and algorithms

### Computation and programming
Computation is not the same as programming - we as humans compute all the time when we interact with our environment.

We go through a process of translation when encapsulating computation in programming which includes:

* design:
  * conceptual
  * functional
  * dialog
* prototyping
* implementation

<br>
**Problems and Solutions**  
<br><br>
![Image showing problem and solution or application.]({{site.baseurl}}/assets/images/4_ctps/problem_solution.png)
<br><br>
How do we get from a problem we need to solve, to a computer programme that provides a solution to the problem?  

**1944**

![Image of Harvard Mark I Computer]({{site.baseurl}}/assets/images/4_ctps/ibm_mark_i.png)
##### IBM Automatic Sequence Controlled Calculator (ASCC) or Harvard Mark I Computer. (IBM Archives)  
Used by von Neumann at the Manhatttan Project to calculate whether implosion was a viable choice to detonate the atomic bomb and to calculate and print mathematical tables, which is what Charles Babbage's analytical engine was intended for.

<span class="fs-2">
[Wikipedia Page](https://en.wikipedia.org/wiki/Harvard_Mark_I){: .btn .btn-outline }</span>

**2020**

![]({{site.baseurl}}/assets/images/4_ctps/2020_systems.png)

We have a whole lot of different systems we can provide solutions on today.  

### Languages
To create solutions we need to be able to instruct the computer on what to do - from doing calculations (running algorithms) to taking in and putting out data (input-output). Computer programming languages are generally described as generations: 1st generation to 3rd (or 5th) generation.  

**Ist Generation Languages (1GL)**

These are machine level languages, and are usually very specific for the CPU they run on (poor portability). They are executed directly by CPU, making them very fast and efficient. They are however very difficult to use and debug, but are still used directly for drivers and interfaces.

If you write a programme in a higher-level language, it needs to be compiled into machine code in order to be run by a CPU. This is usually done with with native code compilers, meaning they compile to code that can be run directly on specific CPUs/platforms without the need for an interpreter. This usually results in better execution/load speed and  security, but limits deployment to a single platform, rather than cross-platform.

![Image of a machine code monitorr.]({{site.baseurl}}/assets/images/4_ctps/machine_code_monitor.jpg)
##### Machine language monitor in a W65C816S single-board computer, displaying code disassembly, as well as processor register and memory dumps. (Wikipedia)  
<span class="fs-2">
[Wikipedia Page](https://en.wikipedia.org/wiki/Machine_code){: .btn .btn-outline }</span>

**2nd Generation Languages (2GL)**

These are known as assembly languages and are also specific for platform/environment. They are any low-level programming language in which there is a very strong correspondence between the instructions in the language and the architecture's machine code instructions. Previously used in all kernels and device drivers, but now are mainly in used in demanding processes such as games, video editing and graphics. Writing assembly language is tedious as each operation must be performed at a very basic level. A

Assembly code is converted into executable machine code by a utility program referred to as an assembler. Code written in higher level languages can use assembly code as a first step, with the code compiled to assembly language then optimised by hand and then assembled into machine code.

![Image of an assembly language listing for a Motorola 6800 8-bit microprocessor.]({{site.baseurl}}/assets/images/4_ctps/assembly_language.png)
##### An assembly language listing for a Motorola 6800 8-bit microprocessor. (Wikipedia)  

<span class="fs-2">
[Wikipedia Page](https://en.wikipedia.org/wiki/Assembly_language){: .btn .btn-outline }</span>

**3rd Generation Languages (3GL)**

These are also known as high level languages and are usually more platform/machine independent. Early examples were Fortran and COBOL, and more modern examples are Java, C#, Python and many other familiar languages. The languages are more abstracted and hide the detail of the CPU operations. The also use hooks or frameworks in the operating systems to provide standard components like windows and menus and give access to lower level functionality.

Higher level languages support structured programming, including object orientated programming, have lots of built-in functionality like data structures, conditional statements and methods. The syntax is more natural language, making it easier to read, write, maintain and reuse. The code still needs to be compiled, and sometimes cross-compiled for different platforms/operating systems.

```java
public class ReadFile{
    private String path;
    //constructor takes in file path
    public ReadFile(String file_path){
        path = file_path;
    }
    //file open method
    public String[] openFile() throws IOException {
        FileReader fr = new FileReader(path);
        BufferedReader textReader = new BufferedReader(fr);
        int numberOfLines = 4;
        //int numberOfLines = readLines( );
        String[] textData = new String[numberOfLines];
        int i;
        for (i=0; i < numberOfLines; i++) {
            textData[i] = textReader.readLine();
        }
        textReader.close( );
        return textData;
    }
    //read lines method
    int readLines() throws IOException {
        FileReader file_to_read = new FileReader(path);
        BufferedReader br = new BufferedReader(file_to_read);
        String aLine;
        int numberOfLines = 0;
        //loop through and read each line
        while((aLine = br.readLine()) != null){
            numberOfLines++;
        }
        br.close();
        return numberOfLines;
    }
}
```
##### Example of Java code
<br>  
**4th and 5th Generation**
Some people divide 3GL into further categories:  
4th generation - consist of statements similar to statements in a human language
commonly used in database programming and scripts e.g. Perl, PHP, Python, Ruby, SQL.
5th generation - contain visual tools to help develop a program e.g. Mercury, OPS5, and Prolog.

### Compiled and Interpreted Code

When using high-level languages, you still need to convert the code into machine code so it can run on the CPU. There are two ways to translate high-level languages into low-level languages:

**Interpreter**  
An interpreter reads the high-level program and executes it, processes the program a little at a time, alternately reading lines and performing computations.  

**Compiler**  
A compiler reads the entire program's code and translates it completely before the program starts running.  
* high-level program = source code  
* translated program = object code or executable  
Once a program is compiled, it executes repeatedly without further translation.
Compiled programs usually run faster than interpreted programs.

Java is both compiled and interpreted. It does not translate programs directly into machine language, but the Java compiler generates _byte_ code, which is similar to machine language. The byte code is easy and fast to interpret, portable as you can compile a Java program on one machine, transfer the byte code to another machine and run the byte code. The interpreter that runs the byte is called a Java Virtual Machine (JVM) and is platform-specific, producing binary code for each platform/operating system.
<br/>
<br/>
![Diagram of Java two-step running process.]({{site.baseurl}}/assets/images/4_ctps/jvm.png)
##### The two-step process compiling, running and interpreting Java code.
<br/>

Java uses a multi-pass compiler, which does an initial run through to evaluate the code and then does subsequent passes to optimise the code. Each pass takes the result of the previous pass as the input, and creates an intermediate output. In this way, the code is improved with each pass, until the final pass produces the final code. This helps with optimisation of memory usage and sequence of execution of instructions.

The Java Runtime Environment (JRE) is a software package that contains every thing required to run a Java program:
* JVM implementation
* Java Class Library implementation

Oracle distributes a JRE with their Java Virtual Machine called HotSpot
Java Development Kit (JDK) - superset of a JRE and contains tools for Java programmers including a _javac_ compiler. There are other versions of JREs available.
<br><br>
![Example of Java byte code.]({{site.baseurl}}/assets/images/4_ctps/byte_code.png)
##### An example of Java byte code after the first step - compiling.
<br>

### Essential Features of a Programming Language  
<br>
* fixed vocabulary
* unambiguous meaning
* consistent grammar
* consistent syntax
* provide a way to define basic data types and operations on those types
* ability to write functions and procedures
* provide input and output handling
* provide some kind of loop that can be stopped
* conditional statements
* branching (conditional and unconditional branching)
* syntax for basic arithmetic and logical
* variables that reference computer memory
* operations on those memory locations
* it has to run on or be able to be processed by a computer i.e. it must have a compiler and/or interpreter

### Title: Taking a step back - a broad view

What makes systems easy to understand and use?
* system interface matches user's mental model
* learnability
* robustness
* flexibility

Hypertext and the WWW were originally thought to be a model of how the human brain works as an associative memory network. This is probably not accurate.

Programming languages that follow how we conceptualise and think are easier to learn and use. It generally helps if there is some abstraction away from the complexity of systems being coded for.

Multimodal systems are becoming the norm, running across devices, platforms and interaction types. Most of these systems are distributed, like cloud systems, where the whole system does not run on a single device or in a single location.

There are a number of different methods of designing and building systems. IB focuses on Object Orientated Design and we use Java to learn to code as it is object orientated and has strict typing - which means you have to declare data types and they don't change unless you do it deliberately.

## Java Basics

### How it works
Java code is written as plain text documents with a file ending of _.java_ which tells the compiler that the file contains Java code. The compiler will run through the _.java_ files and compile them to byte code which are saved as text files with the same names as the code files but _.class_ file endings - one _.class_ file for each _.java_ file. The _.class_ files are then interpreted by the JVM into binary code which is then run on the system. If desired the code can be packaged up as a stand-alone application, but this may require some other steps and processes, and is often platform dependent.

The most basic way to do this, and the recommended way for most people learning to code for the first time is using a plain text editor and the a command line interface (CLI) like the terminal on the Mac and Windows command line or other command line programmes. The current version Java Development Kit (JDK) Standard Edition (SE) for the platform needs to be downloaded and installed on the system first. When doing this follow the instructions for your specific platform and set path variables etc. as instructed.

![Java logo.]({{site.baseurl}}/assets/images/4_ctps/java_logo.png)  

<span class="fs-2">
[Oracle JDK SE Download](https://www.oracle.com/uk/java/technologies/javase-downloads.html){: .btn .btn-outline }</span>

<span class="fs-2">
[Java SE 14 Installation Guide](https://docs.oracle.com/en/java/javase/14/install/overview-jdk-installation.html?xd_co_f=27229c0d-25e3-478d-b22e-5910b8974ab8#GUID-8677A77F-231A-40F7-98B9-1FD0B48C346A){: .btn .btn-outline }</span>

![Screenshot of HellowWorld being run via the terminal.]({{site.baseurl}}/assets/images/4_ctps/terminal.png)
##### Typical set up using a text editor and terminal to code and run Java apps.
<br>
However once they understand how the writing, compiling and running of Java code works, most people move to using an integrated development environment (IDE) which usually enables organisation of files, has a built-in editor, it's own compiler, enhanced debugging capability, built-in run-time environment and lots of other development functionality. Popular examples used for Java are Eclipse, NetBeans and Visual Studio Code. However the complexities of these environments frequently get in the way and confuse novice coders.

There is a cross-platform IDE that has been specifically designed for learning to code Java using objects by theImperial College CS Department, called BlueJ. You need to download and use this for class exercises so everyone is using the same IDE and it is practical to provide support. You still need to download and install the Java JDK as described above.

![BlueJ logo.]({{site.baseurl}}/assets/images/4_ctps/bluej_logo.png)  

<span class="fs-2">
[Download BlueJ](https://www.bluej.org){: .btn .btn-outline }</span>

BlueJ has an excellent user guide and tutorials available, including videos, to help you get started with using it.

### Structuring code
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

![Console output from operator example code.]({{site.baseurl}}/assets/images/4_ctps/operator_output.png)  

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

![Console output from relationship example code.]({{site.baseurl}}/assets/images/4_ctps/relation_output.png)

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

![Screenshot of console output of code.]({{site.baseurl}}/assets/images/4_ctps/array_output.png)




## Slide 31
### Title: Operators
constructor - method same name as class
## Slide 32
### Title: Assignment and Equality/Relational
constructor - method same name as class
## Slide 33
### Title: Operators
constructor - method same name as class
## Slide 34
### Title: Data Structures
constructor - method same name as class
## Slide 35
### Title: Data Structures
constructor - method same name as class
## Slide 36
### Title: Coding
constructor - method same name as class
## Slide 37
### Title: Java Coding
Algorithm:
a self-contained sequence of actions to be performed
Procedural programming:
based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out
Imperative programming:
uses statements that change the state of a program's state usually a list of commands for the computer to perform
## Slide 38
### Title: Java Coding
Algorithm:
a self-contained sequence of actions to be performed
Procedural programming:
based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out
Imperative programming:
uses statements that change the state of a program's state usually a list of commands for the computer to perform
## Slide 39
### Title: Java Coding
Algorithm:
a self-contained sequence of actions to be performed
Procedural programming:
based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out
Imperative programming:
uses statements that change the state of a program's state usually a list of commands for the computer to perform
## Slide 40
### Title: Java Coding
Algorithm:
a self-contained sequence of actions to be performed
Procedural programming:
based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out
Imperative programming:
uses statements that change the state of a program's state usually a list of commands for the computer to perform
## Slide 41
### Title: Java Coding
Algorithm:
a self-contained sequence of actions to be performed
Procedural programming:
based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out
Imperative programming:
uses statements that change the state of a program's state usually a list of commands for the computer to perform
## Slide 42
### Title: Java Coding
Algorithm:
a self-contained sequence of actions to be performed
Procedural programming:
based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out
Imperative programming:
uses statements that change the state of a program's state usually a list of commands for the computer to perform
## Slide 43
### Title: Java Coding
create a new class called OutPut - save as OutPut.java
when instantiated this will create an “OutPut” object
## Slide 44
### Title: Java Coding
default constructor - does not take in any parameters
parametized constructor - takes in parameters
## Slide 45
### Title: Java Coding
default constructor - does not take in any parameters
parametized constructor - takes in parameters
## Slide 46
### Title: Java Coding
constructor - method same name as class
## Slide 47
### Title: Java Coding
constructor - method same name as class
## Slide 48
### Title: Java Coding
constructor - method same name as class
## Slide 49
### Title: Java Coding
comments
MUST DO IT!
really help you keep track of your thoughts
examiners require it
indentation
not critical to syntax in Java as they are in Python but ...
really help clarity of code
parentheses
not closing is common cause of errors - first check to make
modern IDEs help by auto-closing
semi-colon at end of line
not adding is very common cause of error
## Slide 50
### Title: Java Coding
private and public
private - "scope" restricted to that class
public - can be accessed from outside that class
void
method does not return anything
return type stated in method declaration
  public String printTextConfirm(String text)
will return a String
static
constant - i.e. won’t be able to change it elsewhere in the code
public static variable in a class is created and can be used even if object is never instantiated
## Slide 51
### Title: Java Coding
array data type
group of objects - elements indexed from 0, … n.
int array - [34, 65, 23, 9, 18, 27]
String array - [“Joe”, “Mike”, “Pete”, “Luke” ]
need to make array required size when creating it
size cannot be changed after created
String[] myStringArray = new String[4];
String[] myStringArray = new String[“Joe”, “Mike”,
                                    “Pete”, “Luke” ];
## Slide 52
### Title: Java Coding
adapt your HelloWorldApp to PuppyApp
make a Puppy class
make it so you can instantiate a new Puppy with variables for name, colour and age
have methods so you can find out the Puppy’s name, colour or age and print these out to screen
create 3 Puppy objects with various values and show that the correct values print out
