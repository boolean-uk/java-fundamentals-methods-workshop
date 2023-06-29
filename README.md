# Java Methods Workshop

## Learning Objectives
- Understand how to define and use methods in Java Classes

## Methods

So far (apart from the special `main()` method) we've just looked at adding member variables to classes, but one of the strengths of Object-Oriented Programming is that when we define our objects as classes, not only do we describe the data they contain but also the behaviour they can exhibit by defining the Methods that act upon that data.

In more general terms a **Method** is just a special name for a function which is defined as part of a class (in Java everything is pretty much part of a class).

As we said already `main()` is an example of a method which we've already seen, but we're going to create a new class and add some methods to that class.

Either in this project or in a new project add a new Java Class to the `com.booleanuk` package called Example. Add two variables to the definition a String called name with your name in it and an int called score which is set to 0.

Add in a `main()` method to output the name and score in a nicely readable format, which should give you something like the following code:

```java
package com.booleanuk;

public class Example {
    String name = "Dave Ames";
    int score = 0;

    public static void main(String[] args) {
        Example ourExample = new Example();

        System.out.println("Name: " + ourExample.name);
        System.out.println("Score: " + ourExample.score);
    }
}
```

Now we're going to add a method called create greeting which will return a modified version of the name when it gets called, find the two closing `}` at the end, after the first one but before the second hit enter a couple of times and then add in a new method definition that looks like this:

```
public String returnGreeting() {
    
        }
```

This says we're creating a `public` method (more on this when we get to Encapsulation) that returns a `String` it is called `returnGreeting` and takes no parameters (as there is nothing between the brackets). The body of the method (ie the code that will run when it is called) will be between the two curly brackets `{` and `}`.

We want the method to use the variable we created called name and to return a String that will look like this: `Hi Dave Ames. How are you?` given that the name variable is set to `Dave Ames`.

One way would be to create a new String inside the Method, manipulate the `name` attribute and the other strings to create the greeting and then return that.

```
public String returnGreeting() {
    String greeting = "Hello " + this.name + ". How are you?";
    return greeting;
}
```

If we wanted to add in a method to increase the score by a value that is passed as an argument each time then we can do that too.

```
public int updateScore(int points) {
    this.score = this.score + points;
    return this.score;
}
```

Our whole code might then look like:

```java
package com.booleanuk;

public class Example {
    String name = "Dave Ames";
    int score = 0;

    public static void main(String[] args) {
        Example ourExample = new Example();

        System.out.println("Name: " + ourExample.name);
        System.out.println("Score: " + ourExample.score);

        System.out.println(ourExample.returnGreeting());
        int previousScore = ourExample.updateScore(5);
        System.out.println("The score after adding 5 was: " + previousScore);
        ourExample.updateScore(10);
        System.out.println("The new score is: " + ourExample.score);
    }

    public String returnGreeting() {
        String greeting = "Hello " + this.name + ". How are you?";
        return greeting;
    }

    public int updateScore(int points) {
        this.score = this.score + points;
        return this.score;
    }
}
```

Add some more member variables, methods to manipulate them and code in `main()` to run them all.

Can you create a Main class in the same package and use a `main()` method in there to instantiate and run your class? Delete the `main()` method in the `Example` clas in the process.

## Scope

Scope refers to which variables and methods can be seen where in your code. Can you predict when and where your variables and methods can be seen? Do you know when and how to access them?

## Set up instructions
- Fork this repository and clone the forked version to your machine
- Open the root directory of the project in IntelliJ
- Implement the requirements listed in comments in the `./src/main/java/com.booleanuk/core/Exercise.java` file
- When ready to test your solution, open the `./src/test/java/com.booleanuk/core/ExerciseTest.java` file and click a "Run Test" button. You can either run the entire test suite via figure 1 in the screenshot below, or run a specific test via figure 2.

![](./assets/run-a-test.PNG)

## Test Output

When you run a test, it's either going to pass or fail. When it fails, you'll be presented with a big red stream of text. This is called a stack trace and, though intimidating, does contain some useful information.

One of the core skills of a developer is debugging stack traces like this. The stack trace details in which classes & files the failure happened, and gives you a line number at the end. Most of the lines in the stack trace are irrelevant most of the time, you want to try and identify the files that you're actually working with.

In the sample screenshot below, we've tried to complete the first step of the exercise but provided an invalid value. Then we run the test associated with it, and we see a big red stack trace, a test failure.

At the top, we see `expected: <32> but was: <33>`. This means the test expected the value to be 32, but the value the student provided was 33. We can see this in the code snippets at the top of the screenshot.

In the stack trace itself, we see this line: `at app//com.booleanuk.core.ExerciseTest.shouldBeAged32(ExerciseTest.java:20)`. This is helpful! This tells us the exact line in the ExerciseTest.java file (line 20) where the failure happened, as well as the method name (shouldBeAged32), helping us to identify where the issue began. This is the kind of thing you need to look for; a relevant file name, method name, class name and line number to give you a good starting point for debugging.

![](./assets/test-failure.PNG)
