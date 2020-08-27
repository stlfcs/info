---
layout: default
title: Coding with Java 3
parent: Programming
grand_parent: IB DP Core
nav_order: 5
---
Core
{: .label .label-blue }

# Coding with Java 3

## Control Statements ... continued

## Conditional or Control Loops
<br>

## For loop

This is the most basic loop which takes the form:

```java
for(start_value; end_value; increment_value){
  action
}
```

For example:

```java
int i;
int stop_value = 5;

for(i=0; i < stop_value; i++){
  System.out.println("This is loop no. " + i);
}
```

This will output:

![Output from running for loop.]({{site.baseurl}}/assets/images/4_ctps/output_for1.png)  

It is conventional to use `int i` for counting in loops. If you need to count in another loop within the same scope then use `int j`, `int k` ... etc.

It is usual to just declare the integer within the brackets of the `for()` as well:

```java
for(start_value; end_value; increment_value){
  action
}
```

For example:

```java
for(int i=0; i < stop_value; i++){
  System.out.println("This is loop no. " + i);
}
```

Occassionally it is also useful to start at the end of a range and loop backwards through it by decrementing `i` using `i--`.

For example:

```java
int start_value = 5;

for(int i=start_value; i > -1; i--){
  System.out.println("This is loop no. " + i);
}
```

Which would output:

![Output from running for loop backwards.]({{site.baseurl}}/assets/images/4_ctps/output_for2.png)  

Be careful with the stop value in decrementing loops - it must remain true untii desired stop reached.

## While loop
<br>
A while loop continues to carry out the action as long as the condition is true. It takes the form:

```java
while(condition){
  action
}
```

A simple example:

```java
int i = 0;

while(i < 5){
  System.out.println("This is loop no. " + i);
  i++;
}
```

Which would output:

![Output from running for loop backwards.]({{site.baseurl}}/assets/images/4_ctps/output_while1.png)  
<br>
Note that the incrementing is done inside the while loop **after** the action has been executed.

As with `for` loops, downward `while` loops can be run by decrementing the counter.

A very common use of `for` and `while` loops are for looping through elements of a data structure such as an array and doing something with each element.

For example adding together all the elements of an integer array.

```java
//declare and create the array
int[] myIntArray = {14, 3, 9, 17, 11};
int sum = 0;

//loop through the array
for (int i = 0; i < myIntArray.length; i++) {
  //get each element in turn and add the element to the sum
  sum = sum + myIntArray[i];
  System.out.println("Element " + i + " is " + myIntArray[i] + " - sum is " + sum);
}
```

Which would output:

![Output from running for loop backwards.]({{site.baseurl}}/assets/images/4_ctps/output_int_arrayloop.png)  
<br>
Note that the end point can be obtained using the `array.length` method.

# Reading from and writing to files
<br>
Fundamental to storing and retrieving user data is writing it to file and then reading it from the file again - anything from plain text documents such as `.java` files through to image, word processor, spreadsheet and other custom file types.

Many of the custom file types require extensive parsing and formatting before display, but they all start with reading the unicode or ascii characters in the file.

In Java the basic file reading and writing is done using our friend `BufferedReader`, `FileReader` and `FileWriter` library classes. Again we have to deal with IOExceptions, as dealing with file has it's own hazards like the file not being where the code says it should be, or the file being unreadable, or not having the right permissions.

For any class that is reading or writing to file or calling a method in another class which is reading or writing to file, remember to:

```java
import java.io.IOException;
```

Then if reading from file:

```java
import java.io.FileReader;
import java.io.BufferedReader;
```

or writing to file:

```java
import java.io.FileWriter;
import java.io.PrintWriter;
```

Both also require a _file path_ to the appropriate file. This is usually kept as a variable and can be hard-coded in or the user can be prompted for it via a command line or graphical user interface (GUI). The code can use a relative path, so if the project folder looks like this with the text file at the same level as the code:

![Relative file path in finder with file at same level.]({{site.baseurl}}/assets/images/4_ctps/relative_file_path1.png)  

then the relative file path variable would be:

```java
String filePath = "text.txt";
```

If the project was structured with the files in a sub-folder:

![Relative file path in finder with file in sub-folder.]({{site.baseurl}}/assets/images/4_ctps/relative_file_path2.png)  

then the relative file path variable would be:

```java
String filePath = "data/text.txt";
```

This should work on both Windows and Mac, but when you use absolute file paths then you have to take the slashes/back-slashes difference into account.

Hence always store your files locally in the project folder and use relative file paths if you can.
