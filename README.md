# Lab 05 - Logical Garden

In this lab, you will work with a small gardening program to practice using logical operators and conditionals.

## Step 1: Compiling and Initial Runtime Errors
Run the main method in `GardenHelper.java`. Does your code compile? If so, great. Exit the program. Make sure that so far, your program is functioning as normal. If you have any trouble exiting your program, check your code, specifically the `go()` method in `GardenHelper.java` to see what might be causing an issue. (**Hint**: The promts on the screen are correct, those should not be changed.)

## Step 2: Self-Explanation
Take a look at `GardenHelper.java` and its methods `addRow()` and `addPlant()`. We have provided `addPlant()` for you, but it is important to determine what it is doing so you can implement `addRow()` properly. Use the code and the [javadoc](http://www.cs.colostate.edu/~cs163/javadoc/lab05/package-summary.html) to write a brief explanation of what `addPlant()` is doing and brainstorm what else you need to do for `addRow()`. Then, implement `addRow()`. We have provided two test cases for you in `GardenHelper.java`'s `main` method. For testing specific methods, run from `GardenHelper.java`'s `main` and only the tests you have uncommented will run. Running from `GardenMain.java`'s `main` will run the program in its entirety. Add more test cases to `GardenHelper.java`'s `main` make sure `addRow()` works properly before running the whole program too much.

## Step 3: Design
Take a look at the `canPlant()` method in the [javadoc](http://www.cs.colostate.edu/~cs163/javadoc/lab05/GardenHelper.html). Before you start coding, draw out the requirements and write pseudocode for how to implement this method. There are lots of variables to consider, as there are in industry. This is a crucial step in the coding process to save valuable time and headaches! Puzzle it out now, then the actual coding process will go much smoother. 

Not sure what pseudocode is? No problem! We're used to seeing fully functional code, such as
```java
if(fruit1.getName().equals("orange") || fruit1.getName().equals("banana")){
    //do something
}
```
but we can also use `pseudocode` to write what we want our program to do in a mix of plain english and code. Such as:
```
//if (fruit1's name is orange OR banana){
    //do something
//}

//else
    //do something else
```
There isn't a real ratio of how much code/english there is in pseudocode, just write something that will easily outline what you need to do when you get to coding, and that isn't only code. The focus is on solving the problem at hand, then later we can translate that plan into code. 

## Step 4: Implementation
Now that you have figured out how to go about making the `canPlant()` method work, it's time to do the actual coding. Remember to write tests!

## Step 5: Final Testing
Now the Logical Garden program should be complete! Even though you have tested each method inside the `main`s for each class, now it's time to test the program in its entirety. Run your program from the `GardenHelper.java` main, and run through the program a few times, trying different plants and row conditions. 

## Step 6: Turning In
1. Turn in your program files to Zybooks
2. Show your self-explanation, pseudocode, and tests to your TA (in-person) or submit it online

## Extra Practice (Optional)
You may have noticed in your testing that there are some things we just assume to be true. For example, that the user will enter row 1-3 and not some other number. For some extra practice, make a list of the methods that bugs could possibly be introduced, and make some test cases that break the code. 

# Additional Background Information

Something that will be **very** useful for this lab is understanding how to call methods from other methods. Each method has a return type, whether it be a simple getter or a complex method. We can use our knowledge of the return type as well as the functionality of a method to chain multiple methods together. 

For example, we have used the `.equals()` method before.
```java
str = "apples";
if(str.equals("oranges")){
    //do something
}
```
Now, instead of calling just one method, the `.equals()` method, we can call the `equals()` method **and** the `getName()` method. (This is assuming we have a Fruit object that has a name variable and associated getName() method)
```java
Fruit fruit1 = new Fruit("orange");
if(fruit1.getName().equals("orange")){
    //do something
}
```
Or even more complex:
```java
Fruit fruit1 = new Fruit("orange");
Fruit fruit2 = new Fruit("banana");
if(fruit1.getName().equals(fruit2.getName())){
    //do something
}
```

What's happening here is kind of like a relay race. The methods are executed one at a time, and the return value handed back to computer to use in the next method. 

A more complete breakdown of how the computer goes through the `if(fruit1.getName().equals(fruit2.getName()))` example:
1. Evaluate the `if` statement, which is the result of the `.equals()` statement. We need to know what we are comparing first, however.
2. Look at the first part of the `.equals()`. Execute `fruit1.getName()`, which returns "orange". A simplified version would look like: ```if("orange".equals(fruit2.getName()))```
4. Look at the second part of the `.equals()`. Execute `fruit2.getName()`, which returns "banana". A simplified version would look like: ```if("orange".equals("banana"))```
5. Finish evaluating the `if` statement, which is false.

Even though the initial `if` statement looks long and complicated, if you are careful about what methods you are calling and when, condensing your code like this is much better practice and will reduce the likelihood of bugs since you are directly calling your methods. 


To check if multiple conditions are true, `logical operators` and `nested if-statements` can be used. Each has their own benefits.

Logical Operator Examples:

```java
//if fruit1's name is orange OR banana, do something
if(fruit1.getName().equals("orange") || fruit1.getName().equals("banana")){
    //do something
}
```

```java
int a = 1;
int b = 2;
int c = 5;
//if a + b is 3 AND a OR b is less than c, do something
if( ((a + b) == 3) && ((a < c) || (b < c)) ){
    //do something
}
```
These `if` statements can get a bit lengthy, but are useful when there are multiple conditions that must be met for a particular outcome to happen.

Nested `if` Statement Example:

```java
if(plant1.isVegetable()){
    if(plant1.isBroccoli()){
        //ew! don't eat it
    }
    else(
        //eat it
    }
}
else{
    //don't eat it
}
```
While this could have been implemented with logical operators, some situations are more useful with logical operators and some with nested `if` statements. 

The final thing to mention for this lab is the dreaded `null pointer exception`. This "Billion Dollar Mistake" is important to consider if you get `NullPointerException` errors. Sometimes, like if you are searching for an object, if the computer doesn't find the object it will return null. If that return value is being called on by another method, there will be a null pointer exception. 

For example:
```java
int id = searchBook("Hamlet").getId();
//if searchBook("Hamlet") returns null, 
//null.getId() will result in a NullPointerException
```

To fix this, you can add a [variable] != null condition.

For example:
```java
if(searchBook("Hamlet") != null){
  int id = searchBook("Hamlet").getId();
}
```
or
```java
if(searchBook("Hamlet") != null && searchBook("Hamlet").getId() == 5){
    //do something
}
```
