---
layout: default
title: Coding with Java 1
parent: Programming
grand_parent: IB DP Core
nav_order: 4
---
Core
{: .label .label-blue }

# Coding with Java 1

## Structure of a Java Program

The following is the basic HelloWorld app.

```java
/**
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 * @author My name
 * @version v1.0
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

In this example the `main` method is in fact the class constructor as well, although usually a constructor the same name as the class. Many programmers say it is best practice to do as little as possible in the `main` method, and it is best to call another method or instantiate another object to proceed with the program. When learning to code it is often useful to just run code in the `main` for ease and convenience.

### A short word on Java keywords

There are about 50 reserved words, called keywords, that you are not allowed to use as variable names. These words include `public`, `class`, `static`, `void`, and `int`, which are used by the compiler to analyse the structure of the program.

You can find the complete list of keywords at the link below, but you don’t have to memorise them as most programming editors provide “syntax highlighting”, which makes different parts of the program appear in different colours, so you will see a word highlighted as a key word if you accidentally use it in the wrong context..

<span class="fs-2">
[List of Java Keywords](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html){: .btn .btn-outline }</span>

### Classes and constructors

To illustrate how classes are structured and used to create instances or objects based on that class, the code in the HelloWorldApp project is adapted to include a new class called `Output` that does the printing to the console. In its most basic form the new class is:

```java
/**
 * OutPut is a new class.
 * @author GF
 * @version v1.1
 */
public class Output {
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }
}
```

At this stage the class does nothing, so we need to add functionality. This would normally be done by putting the functionality in a _method_ or _function_. If we make this method public, then it can be called from any other class that has access to an object of type `Output`. The method would not return anything, so the `void` keyword is used.

```java
public class Output {
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }

    public void printMethod(){
        //Display the string
        System.out.println("Hello World!");
    }
}
```

Then in the `HelloWorldApp` class we would create a new instance of an Output object and use the print method in it. The new instance is given a variable name and then that name is used from then on. The object instance could then be used again for either printing or any other functionality that may be added with other methods. The default constructor is used to create the object.

```java
public class HelloWorldApp {
    public static void main(String[] args) {
        //create new Output object
        Output printObject = new Output();
        //call the print method in the object
        printObject.printMethod();
    }
}
```

Obviously as it stands this is inflexible and not particularly useful. It would be much more useful to be able to pass the text we want printed to the object instance as a `String`. There are 2 ways to pass parameters to objects, one via a constructor and one via the method. So we could have a second "parameterised" constructor.

```java
public class Output {
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }

    //Parametised constructor - takes in a String
    public Output(String text){
        //Does nothing at the moment
    }

    public void printMethod(){
        //Display the string
        System.out.println("Hello World!");
    }
}
```

The constructor could then call the method to print, but it would need to pass the String on to the method somehow. This could be done by having a variable in the class that the constructor sets to the text it is passed and then the method prints that variable:

```java
public class Output {
    //print string varaible
    String printString;

    //Default constructor
    public Output(){
        //Does nothing at the moment
    }
    //Parametised constructor - takes in a String
    public Output(String text){
        //Does nothing at the moment
    }
    //Method to print String
    public void printMethod(){
        //Display the string
        System.out.println(printString);
    }
}
```

This would then be instantiated and called by the main method like this as follows. The compiler automatically uses the constructor that takes in a `String`.

```java
        //create new Output object
        Output printObject = new Output("Hello World");
        //call the print method in the object
        printObject.printMethod();
```

This approach is useful in certain circumstances, for example when you want to store data in an object and use it over and over via the methods in the object.

However a much more practical and common approach is to use the method to pass the `String` over when you call the method. This uses a parameterised method as with the constructor:

```java
public class Output {
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }
    //Method to print String - takes in String
    public void printMethod(String text){
        //Display the string
        System.out.println(text);
    }
}
```

And this would be called from the main method:

```java
        //create new Output object
        Output printObject = new Output();
        //call the print method in the object passing a String
        printObject.printMethod("Hello World");
```

This offers additional flexibility in that the print method can be used repeatedly with different Strings:

```java
        //create new Output object
        Output printObject = new Output();
        //call the print method in the object passing a String
        printObject.printMethod("Hello World");
        printObject.printMethod("This is me speaking ...");
        printObject.printMethod("... how are things going?");
```
This output would be:

![Screenshot of console output of code.]({{site.baseurl}}/assets/images/4_ctps/output_helloworld1.png)

While we are here we will also use this example just to illustrate how methods can return parameters as well. The `printMethod()` could return a boolean flag to say that the print has been successful. The method declaration then has `boolean` as a return type instead of `void`, and the last line in the method must return a boolean.

```java
public class Output {
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }
    //Method to print String - takes in String
    public boolean printMethod(String text){
        //boolean flag
        boolean flag = true;
        //Display the string
        System.out.println(text);
        //return statement
        return flag;
    }
}
```

And when a method returns a parameter, it must be initialised to a variable of that type, so calling this method will have to like something like this:

This offers additional flexibility in that the print method can be used repeatedly with different Strings:

```java
        boolean printSuccess = printObject.printMethod("Hello World");
    }
}
```

Return types can be anything, and can be local variables so for example it could be used to return an `integer` as a counter.

```java
public class Output {
    //counter
    int lineCounter = 0;
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }
    //Method to print String - takes in String
    public int printMethod(String text){
        //Display the string
        System.out.println(text);
        //increment counter
        lineCounter ++;
        //return statement
        return lineCounter;
    }
}
```

And this could be output by the main method.

```java
public class HelloWorldApp {
    public static void main(String[] args) {
        //create new Output object
        Output printObject = new Output();
        //call the print method in the object passing a String
        System.out.println("# of lines printed: " + printObject.printMethod("Hello World"));
        System.out.println("# of lines printed: " + printObject.printMethod("This is me speaking ..."));
        System.out.println("# of lines printed: " + printObject.printMethod("... how are things going?"));
    }
}
```

![Screenshot of console output of code.]({{site.baseurl}}/assets/images/4_ctps/output_helloworld2.png)


### Reminders
* name of _.java_ file must match class name exactly - including case
* class name must begin with uppercase letter
* use CamelCase for class, constructor, method and variable names
* class name must begin with uppercase letter - variable and method names with lowercase
* constructor name must match class name exactly - including case
* default constructor - does not take in any parameters
* parametized constructor - takes in parameters
* methods can be `void` or return any types of object or data type
* `return` statement must be last line of method

### Comments
* MUST DO them!
* really help you keep track of your thoughts
* examiners require it

### Indentation
* not critical to syntax in Java as they are in Python but ...
* really help clarity of code

### Parentheses (brackets)
* not closing is common cause of errors - first check to make
* modern IDEs help by auto-closing

### Semi-colon at end of line
* not adding is very common cause of error

## Scope
Scope is used to describe whether one part of the programme has access to and can use another part of the program. This is important as the "visibility" (or lack thereof) of variables and methods is used to make sure variables are not changed in error.

To be accessible throughout a class, a variable must be declared at the top of the class - i.e. outside any methods and it will then any part of the code in the class will have scope on it. If a variable is declared within a method then its scope is confined to that method so it can only be used inside that method.

### Private vs. public
The `private` keyword on a variable or method means the "scope" is restricted to that class, so it can only be accessed or changed, in the case of variables, directly from within the class.

The `public` keyword means the variable or method can be accessed from outside that class and in the case of variables, changed from outside the class.

This is important in **encapsulation** where this feature is used to ensure that sections of code stand alone and are protected from change or disruption.

It is standard practice to use private for all "local" variables related to a class and to use public `set()` and `get()` methods to access or change the local variables. In our example `int lineCounter` would be declared private and then the get and set methods would be used to change it from outside the class.

```java
public class Output {
    //counter
    private int lineCounter = 0;
    //Default constructor
    public Output(){
        //Does nothing at the moment
    }
    //Method to print String - takes in String
    public int printMethod(String text){
        //Display the string
        System.out.println(text);
        //increment counter
        lineCounter ++;
        //return statement
        return lineCounter;
    }
    //get method
    public int getCounter(){
        return lineCounter;
    }
    //set method
    public void setCounter(int val){
        lineCounter = val;;
    }
}
```
