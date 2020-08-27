---
layout: default
title: Coding with Java 2
parent: Programming
grand_parent: IB DP Core
nav_order: 4
---
Core
{: .label .label-blue }

# Coding with Java 2

## Learning a coding language
<br>
When you start learning a language there are a number of ways to go, self taught from a book, self-taught online course, taught course or a combination of all of these. Usually books and online courses start by assuming you know no nothing and build up from there.

We will use a combination of taught and self-taught using online books, online tutorials and other resources. From the start you should get used to looking up how to do things in the language - or the "syntax". No book/course/teacher can cover everything you might possibly need, so the quicker you become familiar with the online resources available for the language the better.

You should make sure you rapidly become familiar with:
<br>

**Module java.base**
<br>

The official Oracle documentation of all Java the libraries you will be working with. Use these to see the different methods available for library classes and what parameters they take in and return.  

![Java logo.]({{site.baseurl}}/assets/images/4_ctps/logo_java.png)  
<span class="fs-2">
[Official Java Docs](https://docs.oracle.com/en/java/javase/14/docs/api/java.base/module-summary.html
){: .btn .btn-outline }</span>

**Google search "Java syntax ..."**
<br>

Search on Google or your favourite search engine for "Java syntax ..." with your requirement entered e.g. "Java syntax parse string" to find out how to take a single character at a time off the front of a string. As a coder - Google is your best friend!

Inevitable the top result - and a number of others - are for StackOverflow. StackOverflow is your second best friend and that friend that irritates the life out of you by having far too many opinions and expressing them with conviction even when they are wrong!

StackOverflow is a really valuable source of information as extremely knowledgeable and competent coders prowl it and you can ask for or find answers to most problems on there. Unfortunately by its nature it is practically unmoderated and therefore there are tons of really poor advice as well.

**NEVER** just take the first answer as correct - read all the subsequent answers and comments and judge what you think suits your purposes best, or try out a number of suggestions to see which one works best for you.

It is sometimes useful to cut and paste code examples from the answers as a starting point for your code. Be careful with this - it can sometimes hinder more than it can help. **ALWAYS** make a comment in your code with the URL of where you found the code so you can go back to that page if you need to - it is incredibly difficult to find some obscure StackOverflow pages again.

If you end up using the code substantially unchanged, then add an acknowledgement to the author "The following code is based on Joe Blogg's post: https://stackoverflow.com..." to your comment and leave the URL in the comment. The same applies for any code from books or tutorial you use - it is easy to forget where you found an example of code and often useful to be able to go back to it later.

It is always polite and appreciated - even if they never see it - to acknowledge other coders who help you with no expectation of reward.

![Stackoverflow logo.]({{site.baseurl}}/assets/images/4_ctps/logo_stackoverflow.png)  
<span class="fs-2">
[StackOverflow](https://stackoverflow.com){: .btn .btn-outline }</span>
<br>
### Books
<br>
This is a very good and useful free book - look at it first:

_Green Tea Think Java 2_

![Green Tea Press Think Java book logo.]({{site.baseurl}}/assets/images/4_ctps/logo_greentea_thinkjava.png)  

Use the interactive version hosted by Trinket

<span class="fs-2">
[Trinket - Green Tea Press Think Java](https://books.trinket.io/thinkjava2/){: .btn .btn-outline }</span>

or the PDF or online versions:

<span class="fs-2">
[Green Tea Press Think Java](https://greenteapress.com/wp/think-java-2e/){: .btn .btn-outline }</span>

There are plenty of other books out there - have a look at them and if one suits your style better feel free to use it.
<br>
### Tutorials
<br>
**Oracle**
<br>
I personally find Oracle's tutorials very difficult to follow. but they are extensive and helpful. Yes, the logo does look like it's sniffing illegal substances, and lots of it, and that may explain things somewhat.

![Oracle Java Tutorials logo.]({{site.baseurl}}/assets/images/4_ctps/logo_oracle_tutorials.png)

<span class="fs-2">
[Oracle Java Tutorials](https://docs.oracle.com/javase/tutorial/){: .btn .btn-outline }</span>
<br><br>

**Tutorialspoint**

These are good and easy to follow tutorials.

![tutorialspoint Java Tutorials logo.]({{site.baseurl}}/assets/images/4_ctps/logo_tutorialspoint.png)

<span class="fs-2">
[Tutorialspoint Java Tutorials](https://www.tutorialspoint.com/java/index.htm){: .btn .btn-outline }</span>
￼<br><br>

**W3Schools**

W3C provides a comprehensive reference site for HTML, CSS, Java, Javascript and some other languages. Their tutorials are nicely arranges and helpful with lots of example code.

![W3Schools logo.]({{site.baseurl}}/assets/images/4_ctps/logo_w3schools.png)

<span class="fs-2">
[W3Schools Java Tutorials](https://www.w3schools.com/java/default.asp){: .btn .btn-outline }</span>
<br><br>

**BlueJ Help and Tutorials**

Use the website to find all sorts of useful help, videos and tutorials.

![BlueJ logo.]({{site.baseurl}}/assets/images/4_ctps/logo_bluej.png)

<span class="fs-2">
[BlueJ Help and Tutorials](https://bluej.org/doc/documentation.html){: .btn .btn-outline }</span>
<br>

# Input and Output

## Getting input from the console

The most basic user interaction in most languages is using theterminal or console. In Java there are 3 ways to get user input from the console:

* basic
* scanner
* buffered reader

### 1. Basic
<br>
A `Console` object is created and then this is used to read the line of user input into a `String` variable.

```java
Console console = System.console();
String name = "";
System.out.print("What is your name?");
name = console.readLine();
System.out.print("Hello " + name);
```

There are a number of issues with the basic method which is really a hagover from Java's early days:

* it doesn't work with any IDE - only with the terminal
* it is inefficient

Basically - don't use it - no one does any more!

### 2. Scanner
<br>
This uses the `Scanner` class from the `java.util` library and is probably the most popular method to take input from the console. The main purpose is to parse primitive types and strings using regular expressions (Aside on Regular Expressions below). It can be used to read input from the user in the command line and using IDEs.

The advantages are:

* the class has convenient methods for parsing primitives from the tokenized input:  nextInt(), nextFloat(), etc,
* regular expressions can be used to find tokens

However it has some disadvantages:

* reading methods are not synchronized so multithreading is not supported
* there is a huge bug in the `Scanner` class:

> if you call the `nextLine()` method after any one of the 7 `nextXXX()` methods then the `nextLine()` does not read values from console and the cursor will not come into console so it will skip that step

Why this bug - which has been around for years - has not been fixed is quite beyond every Java coder.

Example of using the Scanner class:

```java
//Import the scanner library
import java.util.Scanner;

//Create new Scanner object passing it a system input object
Scanner in = new Scanner(System.in);

//Prompt user for input
System.out.println("What is your name?");

//Read the console input as a string using nextLine()
String name = in.nextLine();

//Print to console using the capture from the read line
System.out.println("Hello " + name + "!");
```

Output:

![Output from running Scanner code.]({{site.baseurl}}/assets/images/4_ctps/output_scanner.png)  

### 3. BufferedReader
<br>
This is the classical method to take input and do output both from the console and files (around from JDK 1.0). It is a bit complicated as you need to wrap the `System.in(standard input stream)` in an `InputStreamReader` which is wrapped in a `BufferedReader`. Then input from the user in the command line can be read.

The advantages of it are:

* input is buffered for efficient reading
* it is synchronised so can be used with multithreading
* it has a significantly larger buffer memory than Scanner:
  * BufferedReader - 8KB byte buffer
  * Scanner - 1KB char buffer
* BufferedReader is a bit faster as it simply reads sequence of characters while Scanner does parsing of input data

The disadvantages are:

* all the wrapping of code is hard to remember
* you need to import 3 libraries:
  * java.io.BufferedReader
  * java.io.IOException
  * java.io.InputStreamReader
* you have to remember that it throws an IOException which needs declaring and handling
* it only handles string input and does not support tokenisation

The same example using `BufferedReader`:

```java
//Import the 3 libraries
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

//Create new BufferReader object
BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

//Prompt user for input
System.out.println("What is your name?");

//Read in console input using readLine()
String name = reader.readLine();

//Print to console using the capture from the read line
System.out.println("Hello " + name + "!");  
```

To start with it can be less confusing to create the `BufferedReader` object in 2 steps:

```java
//Create new InputStreamReader object
InputStreamReader stream = new InputStreamReader(System.in);
//Create new BufferReader object
BufferedReader reader = new BufferedReader(stream);
```

## Control Statements

It is very common to want to do something - for example run an algorithm - either when certain conditions are met, or over and over again while a certain condition exists. We use conditional statements to see if conditions are true and then do one thing or another. This can be one-off or repeatedly until the condition changes - which is known as a loop.

Control statements and loops are at the heart of computing, and designing them well so that they work efficiently is often the key to the program working well.

### if

Form:

```java
if(condition) {
    action
}
```

* if condition true - will execute code within `if` brackets then move on
* if condition false - will skip all code within brackets

Example:

```java
int user = 17;

if(user < 18) {
  System.out.println("You cannot vote.");
}

if(user >= 18) {
  System.out.println("You can vote.");
}
```

This will output `You cannot vote`.

If `int user` was any value 18 or greater it would output `You can vote.`

### if else

Form:

```java
if(condition) {
  action
}
else {
  action2
}

```

* if condition true - will execute code within `if` brackets then move on
* if condition false - will execute code within `else` brackets then move on

Example:

```java
int user = 17;

if(user < 18) {
  System.out.println("You cannot vote.");
}
else {
  System.out.println("You can vote.");
}
```

This will output `You cannot vote`.

If `int user` was any value 18 or greater it would output `You can vote.`

Any expression that resolves to a boolean - true or false - can be used as a conditional. In its simplest form a boolean - for example:

```java
boolean user = true;

if(user){         //means if user == true = don't need the ==
  System.out.println("user is true.");
}
else {
  System.out.println("user is false.");
}
```

or

```java
boolean user = false;

if(!user){     //means if user is false
  System.out.println("user is false.");
}
else {
  System.out.println("user is true.");
}
```

You can string together as many `if` s and `elses` as you like - using `if` for first and `else if` for others with the final `else` to catch any others. For example:

```java
if(user < 18) {
  System.out.println("You cannot vote.");
}
else if(user == 18){
  System.out.println("You must register to vote.");
}
else {
  System.out.println("You can vote if registered.");
}
```

However this becomes clumsy very rapidly as the number of conditions increases, so a better way of doing that is to use a `switch` statement. This takes the form of:

```java
switch(testVariable){
case value1:
  action1
case value2:
  action2
default:
  action3
}
```

For example:

```java
int user = 17;

switch(user){
case 17:
  System.out.println("You cannot vote.");
  break;
case 18:
  System.out.println("You must register to vote.");
  break;
default:
  System.out.println("You can vote if registered.");
}
```

Advantages:
* much more readable
* can be used for any data or object type
* the `break` stops the execution of the switch statement, once the correct condition has been met. This makes it more efficient than `if-else` which continues to check every conditional statement even after the condition has been met.

Conditional statements can be nested, with as many levels as you like.

For example:

```java
//create new scanner object
Scanner scan = new Scanner(System.in);
System.out.println("Enter your age");
//assign the response to a variable
//Read in user input using nextLine method from scanner class
int user = scan.nextInt();
System.out.println("Have you registered y/n");
//assign the response to a variable
//Read in user input using nextLine method from scanner class
char reg = scan.next().charAt(0);

//use if-else statement to respond
if(user < 18) {
  System.out.println("You cannot vote.");
    if(reg == 'y'){
      System.out.println("Good you registered early!");
    }
    else{
      System.out.println("Don't forget to register!");
    }
}
else if(user == 18){
  System.out.println("You can vote from this year.");
    if(reg == 'y'){
      System.out.println("Good you can vote");
    }
    else{
      System.out.println("You must register to start voting!");
    }
}
else {
  if(reg == 'y'){
    System.out.println("You can vote!");
  }
  else{
    System.out.println("You should register!");
  }
}
//close scanner
scan.close();
```

Output:

![Output from running nested if else code.]({{site.baseurl}}/assets/images/4_ctps/output_nested.png)  
<br>
When doing nested logic code make doubly sure you get the design correct on paper first using flow diagrams and pseudocode. Errors in these nested logic algorithms are never easy to detect and resolve after they are coded.
