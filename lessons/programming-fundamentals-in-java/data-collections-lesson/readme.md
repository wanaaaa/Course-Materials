---
title: Storing Data in Collections
duration: "1:30"
creator:
    name: Kristen Tonga
    city: NYC
---

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Storing Data in Arrays and  Collections

### LEARNING OBJECTIVES
*After this lesson, you will be able to:*
- Create and manipulate arrays and Lists
- Access specific values in arrays and lists using `for loops` to iterate over them


### STUDENT PRE-WORK
*Before this lesson, you should already be able to:*
- Work with basic data types and assign variables
- Create basic functions

---

<a name="opening"></a>

## Opening (5 mins)

So far, we have stored all of the information for our apps in individual variables. That works for a small amount of information, but what if we had to manage larger sets of data? For instance, what if we were a store and needed to print out a receipt of all the items a customer has purchased? Would we create a variable for every item? How would we know how many items the customer is purchasing before they even came in?

>  Write a few examples of where storing our data in a collection would be beneficial (data situations or real world examples). Write them down on the desk. (1-2 minutes)

<a name="introduction"></a>
## Introduction: Basic Arrays (5 mins)

Remember the box analogy I gave you? Data types are boxes that you put data in and variables are the labels for each box.

>Check: How do I declare and initialize/instantiate variables?
> If I wanted to do that for 10 variables?

```java
int var1 = 1;
int var2 = 2;
int var3 = 3;
int var4 = 4;
int var5 = 5;
int var6 = 6;
int var7 = 7;
int var8 = 8;
int var9 = 9;
int var10 = 10;
  ```

What if I had 200 `int` values? Would I have to create 200 variables? That's crazy. We can use an array to hold all these values.

An array is a container that holds a **fixed** number of values of **a single data type**. You've already seen an example in the `main` method.

>Check: What do I mean by fixed?

An important concept to understand is an array is not necessarily a data type, it just holds data types in a structured way. This is also referred to a data structure. In a nutshell, a data structure manages how we interact with larger amounts of data. Java provides us data structures as `Objects`, so we don't need to worry too much about how they work, just yet.

Each item in an array is called an *element*, and each element can be accessed by it's *index*. We covered index in yesterday's class. Remember, the index of elements starts at 0. That means visually that:

  INDEX  | 0 | 1 | 2 | 3 | 4
  -------|---|---|---|---|---
 ELEMENT| x | x | x | x | x

## Demo: Creating Arrays (10 mins)

Let's create an Array together:

Data Type | Brackets | Variable name | Assign Value To | Instantiation
:---: | :---: | :---: | :---: | :---:
int | [] | anIntArray | = | new int[]
double | [] | aDoubleArray | = | new double[]
String | [] | aStringArray | = | new String[]
boolean | [] | aBooleanArray | = | new boolean[]

```java
  class ArrayDemo {
    public static void main(String[] args) {
      //declares an array of integers

       // note datatype, followed by [] indicating array.
      int[] anArray;

      //allocates memory for 10 integers
      //note the need for the 'new' keyword and the need for a 'size'
      anArray = new int[10];

      //assign elements

      /*
      So how do we put values inside this array?
      Similar to how we access values inside the array.
      > Important to note that arrayName[index] is the syntax we need to open
      that specific box.
      */
      anArray[0] = 111;
      anArray[1] = 222;
      anArray[2] = 123;

      //What about if i wanted to put the value 12345 in the 8th box?
      //How would I do that?


      //Lets print out the values that we just put in.
      //access elements
      System.out.println("Element at index 0: "+ anArray[0]);
      System.out.println("Element at index 1: "+ anArray[1]);
      System.out.println("Element at index 1: "+ anArray[2]);

      //What happens when I try to print out the value in the 5th position.

      System.out.println("Element at index 1: "+ anArray[7]);
      System.out.println("The array has a size of " + anArray.length);
    }
  }
```

> Check: If I didn't know the number of the last element of an array, what could I use to find the index of the last element?

> Check: What are the three parts of creating an array? (expect: declare array variable, allocate memory, initialize/assign values)

#### Manipulating Basic Arrays

Let's take a look at some basic things you can do with an array.

You guys have already seen me do some of these things. We'll discuss them during class, make sure to participate.

## Independent Practice: Creating Arrays (10 mins)

**Now you:** Create a String array of *three* of your favorite things. Print the result to the command line.

```Java
class Main {
  public static void main(String[] args){
    String[] favoriteThings = new String[3];

    favoriteThings[0] = "Rain drops on roses";
    favoriteThings[1] = "Bright copper kettles";
    favoriteThings[2] = "Warm woolen mittens";

    System.out.println(favoriteThings[0]);
    System.out.println(favoriteThings[1]);
    System.out.println(favoriteThings[2]);

  }
}
```

####Searching
What if we wanted to search if an array had a specific value?
We'd have to loop through it and check each value to see if it's the value we want.
We'll learn more about this a little later.

#### Out of bounds
Say we have an array `myArray`, of size 10 of any data type, let's use `int` in this example.
The values 1-10 have already been assigned in each of the positions of the array.
What will I get if I wrote, `myArray[10]`? Write down your response, we'll discuss.

We get an exception called `OutOfBoundsException`

An Exception is thrown when the computer is asked to do something it can't do, like accessing index -1 or 4 in a 4-element array.
Remember in Java, we start from 0. Exceptions bubble up, and unless caught (which we will talk about in a later lesson) can cause the program to quit.

It is important to know how to read and handle these exceptions when they arise. (You'll learn more about this later)

## Demo: Problems with Arrays (10 min)

But what if I decide that actually, I want this list to include 4 things instead of 3? For example, let's go back to our favoriteList; I decide I really like "whiskers on kittens" and want it to be the second favorite thing, and just move everything
down one position.
```java
class Main{

  public static void main(String[] args){

    String[] favoriteThings = new String[3];
    System.out.println(favoriteThings[0]);
    System.out.println(favoriteThings[1]);
    System.out.println(favoriteThings[2]);

    //I want to change the size of my array to hold 4 things, but I already set it to hold 3 things.

    String[] tempArray = new String[4];
    tempArray[0] = favoriteThings[0];
    tempArray[1] = "whiskers on kittens"
    tempArray[2] = favoriteThings[2];
    tempArray[3] = favoriteThings[3];

    //What's another way to do it?
    for(int i = 0; i < favoriteThings.length; i++){
      if(i == 1){
        tempArray[i] = "whiskers on kittens";
        continue; //what does this do?
      }
      else{
      tempArray[i] = favoriteThings[i];
      }
    }
    tempArray[4] = "bright copper kettles";

    //But that's not our favoriteThings array, its a tempArray.
    favoriteThings = tempArray;

  }

}

```

Luckily, Java has provided something that does the hard work for us: collections.

## Demo: Collections (15 mins)

Collections will not only provide us with convenience methods, allowing us to do more things with the data we have, but will also *automatically increase the size* if we need!

There are many different collection classes that we use just like data types, each of which provides some distinct functionality, but for today, we're going to focus on just one of them.

#### ArrayList

Let's take the array we made of favorite things and convert it into an `ArrayList`.

```java
  public static void main(String[] args) {
    // initialize ArrayList
      List<String> favoriteThings = new ArrayList<>();
    // add items
      favoriteThings.add("bright copper kettles");
      favoriteThings.add("warm woolen mittens");
      favoriteThings.add("brown paper packages tied up with strings");
  }
```

Note, the data type of each element is defined in angle brackets `<>`. This data type could be any object type. So, if you'd created a `Person` object, as you may have in the pre-work, you could create an ArrayList of Persons! (i.e. an `ArrayList<Person>`)

If you want to make an ArrayList of a primitive type, you need to use a "boxed" version of that type as the thing in the angle brackets. For example, if you want to store a bunch of `int`s, you would use an `ArrayList<Integer>`.

#### Manipulating a ArrayList

An ArrayList is an object, with methods, which makes it much easier to manipulate than a simple array. Check out the following methods.

```java
  //to print. No need to explicitly convert it to a string first!
  //(because ArrayList has a toString() method, which automatically
  //gets called here)
    System.out.println("favoriteThings = " + favoriteThings);

  //add(item) -- adds to the end of the list
    favoriteThings.add("chocolate");
    System.out.println("favoriteThings = " + favoriteThings);

  //add(index, item) -- adds to the list at specified index and moves all other entries over. Think: what you would have to do with a simple array to do that?
    favoriteThings.add(1, "warm woolen mittens");
    System.out.println("favoriteThings = " + favoriteThings);

  //set(index, item) -- replace the item at the given index with a new one
    favoriteThings.set(0, "tarnished copper kettles");
    System.out.println("favoriteThings = " + favoriteThings);

  //to search for an entry
    int indexOfIceCream = favoriteThings.indexOf("icecream");
    if(indexOfIceCream != -1) {
      String ic = favoriteThings.get(indexOfIceCream);
      System.out.println("ic = " + ic);
    }
    else {
      System.out.println("icecream not found");
    }

 //here's another good one: get number of things in the ArrayList
    favoriteThings.size();
```

> Instructor Note: Add other convenience methods as needed.

> Check: What are advantages of using an ArrayList over an array? Expect students to include: automatic resizing, convenience methods.


## Guided Practice: Iterating Through a List with For Loops (15 mins)
One more thing before we start talking about lists in Android: How do you iterate through a list?

#### Using the For Loop with Lists and arrays
Do you remember the syntax used in a for loop? We used it in the Control Flow lesson to print something to the command line a set number of times.

The for loop is also commonly used with arrays and collections to iterate through each of the elements and do something with each entry.

For example, let's create a list of 5 movies and iterate through it, printing each one to the command line.

```java
  public static void main(String[] args) {

    //initialize String array
    String[] favoriteMoviesArray = new String[5];

    //add items
    favoriteMoviesArray[0] = "Finding Nemo";
    favoriteMoviesArray[1] = "The Theory of Everything";
    favoriteMoviesArray[2] = "Eternal Sunshine of A Spotless Mind";
    favoriteMoviesArray[3] = "Crash";
    favoriteMoviesArray[4] = "Ip Man";

    //Loop through array
    for(int i = 0; i < favoriteMoviesArray.length; i++){
      System.out.println(favoriteMoviesArray[i]);
    }

    // initialize ArrayList
      List<String> favoriteMoviesList = new ArrayList<>();

    // add items
      favoriteMoviesList.add("Finding Nemo");
      favoriteMoviesList.add("The Theory of Everything");
      favoriteMoviesList.add("Eternal Sunshine of A Spotless Mind");
      favoriteMoviesList.add("Crash");
      favoriteMoviesList.add("Ip Man");

      //Loop through List
      for(int i = 0; i < favoriteMovies.size(); i++){
        System.out.println(favoriteMovies.get(i));
      }

  }
```

## Independent Practice (15 mins)

Complete as many of the following challenges as you can in the next 15 minutes. Each challenge should be completed in its own method.

1. Find the size:
  a. Create an array of ints.
  b. Print the length of the array to the command line.

2. Concrete Jungle
  a. Create a ArrayList of New York City wildlife.
  b. Create a function that, given an List of Strings, prints for each element: "Today, I spotted a /*Thing here*/ in the concrete jungle!"

3. Create a method that, given an array of ints, return the sum of the first 2 elements in the array. If the array length is 1, just return the single element, and return 0 if the array is empty (has length 0).

*Bonus*
4. Create an method that, given an List of words (Strings), turns each word into Pig Latin. The rules of Pig Latin are as follows:
  a. The first consonant is moved it to the end of the word and suffixed with an `ay`.
  b. If a word begins with a vowel you just add `way` to the end.

For example, `pig` becomes `igpay`, `banana` becomes `ananabay`, `twig` becomes `wigtay`, and `aadvark` becomes `aadvarkway`.


<a name="conclusion"></a>
## Conclusion (5 mins)

Quick review:
- List some differences between arrays and Array lists

Arrays and Lists are fundamental tools needed by anything that wants to store and manipulate collections of data. Now that you know how to use them, we can start creating apps that use those collections. Excited?



### ADDITIONAL RESOURCES
- [Oracle Java Docs - Arrays](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html)
- [Android Docs - ArrayList](http://developer.android.com/reference/java/util/ArrayList.html)
- [Oracle Java Docs - The for Statement](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/for.html)
- [CodingBat - Array-1 examples](http://codingbat.com/java/Array-1)
- [Android Docs - Building Layouts with an Adapter](http://developer.android.com/guide/topics/ui/declaring-layout.html#AdapterViews)
- [Android Docs - Adapter](http://developer.android.com/reference/android/widget/Adapter.html)
