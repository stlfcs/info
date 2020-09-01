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

Below is table from W3Resource giving the global popularity of the various languages according to the TIOBE Programming Community index, an indicator of the popularity of programming languages based on the number of skilled engineers world-wide, courses and third party vendors and popular search engine data.

![Table of top 15 most popular programming languages globally.]({{site.baseurl}}/assets/images/4_ctps/lang_popularity.png)
####TIOBE Language Popularity Index for August 2020
<span class="fs-2">
[Link to source](https://www.tiobe.com/tiobe-index/){: .btn .btn-outline }</span>

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
<br>
What makes systems easy to understand and use?
* the system interface matches user's mental model
* learnability
  * the system is easy to learn to use
  * easy for a user to come back to after a period of time
* robustness
  * it should be obvious to the user what the current state of the system is
  * they should be able to see their place in any process or task
  * the user should be able to recover easily from errors
  * the system should be responsive
* flexibility
  * the system enables users to work in different ways
  * allows a degree of customisation
  * copes with changing demands such as slightly different or new tasks

Hypertext and the WWW were originally thought to be a model of how the human brain works as an associative memory network. This is probably not accurate.

Programming languages that follow how we conceptualise and think are easier to learn and use. It generally helps if there is some abstraction away from the complexity of systems being coded for.

Multimodal systems are becoming the norm, running across devices, platforms and interaction types. Most of these systems are distributed, like cloud systems, where the whole system does not run on a single device or in a single location.

There are a number of different methods of designing and building systems. IB focuses on Object Orientated Design and we use Java to learn to code as it is object orientated and has strict typing - which means you have to declare data types and they don't change unless you do it deliberately.

### A last few definitions
<br>
<dl>
  <dt>Algorithm</dt>
  <dd>a self-contained sequence of actions to be performed by the program</dd>
  <dt>Procedural programming</dt>
  <dd>a program is based upon the concept of the procedure call, routines, subroutines, or functions that contain a series of computational steps to be carried out</dd>
  <dt>Imperative programming</dt>
  <dd> this uses statements that change the state of a program's state usually a list of commands for the computer to perform</dd>
</dl>
