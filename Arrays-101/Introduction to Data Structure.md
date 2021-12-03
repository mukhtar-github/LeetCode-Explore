# Introduction to Data Structure

## Arrays 101

## Overview (Introduction)

Arrays are a simple data structure for storing lots of similar items. They exist in all programming languages, and are used as the basis for most other data structures. On their own, Arrays can be used to solve many interesting problems. Arrays come up very often in interview problems, and so being a guru with them is a must!

In this Explore Card, we'll introduce Arrays and solve some cool problems with them. This Card is beginner friendly, and we've provided lots of code snippets in Java to help you understand. Each topic begins with informative articles, followed by real interview problems for you to practice on.

In addition, the problems have hints which will help you in building up ideas on how to solve them. These hints will be subtle enough to set you on a particular path for reaching the optimized solution, without giving away the answer too easily.

After completing this Explore Card on Arrays, you will understand:

* What an Array is.
* Basic properties of Arrays.
* Implementing basic Array operations.
* Simple programming techniques with Arrays.

## 1-Introduction

In this chapter, we'll begin by looking at what an Array is, and what it's used for. We'll start by comparing Arrays to a real-world problem: storing lots of DVDs in an organized way. After that, we'll look at how to create and work with Arrays in Java.

### Array - A DVD box?

Suppose you had a bunch of DVDs at home that you wanted to arrange neatly. What would be the ideal choice for storing such a thing? You could find a cardboard box (or some other box) big enough to arrange all of the DVDs neatly, right? It's as simple as that. However, you might want to add a new DVD to the box, or you might want to get rid of the old ones that you've watched a million times over in the past. An important consideration for this box would be that you would only place DVDs in it and nothing else; you wouldn't place your clothes in it, for example. The box would contain multiple items, but all of them would be of the same type. In this case, that type is DVD. Items of the same type share properties. For DVDs, those properties include:

* All the DVDs would be inside a plastic cover.
* The cover would have the name of the movie, the cast, and all sorts of other details.
* All the covers would be of exactly the same size and would contain just one, and only one, DVD.

You might not actually name the DVD box, but when you want your sister to fetch a DVD, you'd tell her that the DVD is inside your "DVD box", and she would instantly know where to find the box. This is a very simple yet realistic scenario that is easy to understand and relate to. So, now let us move over to the world of computers and port this example to programming.

Suppose you were told that you needed to build some software to keep track of all the DVDs in an inventory. This is the exact same scenario that we just described above, but on a much larger scale. So let's imagine the DVD box as a virtual DVD library. For each DVD, you would have certain properties that would be specific attributes of the movies themselves.

In addition to the properties of a DVD, you're also told the maximum number of DVDs that can be stored in the inventory. Obviously, you wouldn't want to store ancient movies from the 1900s unless they were popular ones, right? Say you were told that the requirement is to maintain a maximum inventory of just 100 DVDs. This is an important piece of information because, without this, you wouldn't be able to find the perfectly sized box to fit all the DVDs easily. How could we find a box of a particular size that would be able to fit a maximum of 100 DVDs? Well, lucky for us, we don't need to physically find a cardboard box or anything—there's a programming construct for this purpose. That programming construct is known as an *Array*.

### What Is an Array?

> An Array is a collection of items. The items could be integers, strings, DVDs, games, books—anything really. The items are stored in neighboring (contiguous) memory locations. Because they're stored together, checking through the entire collection of items is straightforward.

So, how can we relate this back to the physical DVDs? Well, do you keep your DVDs all around the house in multiple locations? Hopefully not! Most people keep all of their DVDs right next to one another inside one gigantic box, or perhaps on a bookshelf. We do this so that if we need to find a particular DVD, we can quickly search through all of them without running from room to room.

#### Creating an Array

On a computer, Arrays can hold up to N items. The value of N is decided by you, the programmer, at the time you create the Array. This is the same as when we found a big enough cardboard box for the DVDs. Additionally, you also need to specify the type of item that will be going into the Array.

In Java, we use the following code to create an Array to hold up to 15 DVDs. Note that we've also included a simple definition of a DVD for clarity.

```java
// The actual code for creating an Array to hold DVD's.
DVD[] dvdCollection = new DVD[15];

// A simple definition for a DVD.
public class DVD {
    public String name;
    public int releaseYear;
    public String director;

    public DVD(String name, int releaseYear, String director) {
        this.name = name;
        this.releaseYear = releaseYear;
        this.director = director;
    }

    public String toString() {
        System.out.println(
            this.name + ", directed by " + this.director + ", released in " + this.releaseYear));
    }
}
```

#### Out Sourced Notes - Start 1

### Creating an Array in JavaScript

There are two ways to create an array in JavaScript:

* The array literal, which uses square brackets.
* The array constructor, which uses the new keyword.

Let’s demonstrate how to create an array of shark species using the array literal, which is initialized with *[]*.

```javascript
// Initialize array of shark species with array literal
let sharks = [
    "Hammerhead",
    "Great White",
    "Tiger",
];
```

Now here is the same data created with the array constructor, which is initialized with *new Array()*.

```javascript
// Initialize array of shark species with array constructor
let sharks = new Array(
    "Hammerhead",
    "Great White",
    "Tiger",
);

var foo = new Array(45); // create an empty array with length 45

// then when you want to use it... (un-optimized, just for example)
for(var i = 0; i < foo.length; i++){
  document.write('Item: ' + (i + 1) + ' of ' + foo.length + '<br/>'); 
}
```

Both methods will create an array. However, the array literal (square brackets) method is much more common and preferred, as the *new Array()* constructor method may have inconsistencies and unexpected results. It’s useful to be aware of the array constructor in case you encounter it down the line.

#### Out Sourced Notes - End 1

After running the above code, we now have an Array called dvdCollection, with 15 places in it. Each place can hold one DVD. At the start, there are no DVD's in the Array; we'll have to actually put them in.

The Array can only hold up to 15 DVDs. If we get a 16th DVD, we'll need to make a new Array. We'll look at how we deal with running out of space, in the next chapter.

Before we move onto actually putting some DVDs into the Array, though, one thing you might be wondering is why we'd make an Array with only 15 places. Why not just make it hold 1000000 DVDs so that we know for sure we'll always have enough space?

Well, the reason is the same as it is for the physical box of DVDs. Do you really want to find a box that could hold 1000000 DVDs when you currently only have 15 DVDs and, in fact, never expect to own more than 100 of them? Is it even worth getting a box that could hold 100 DVDs right now, when you only expect to get a few new ones each year? It will take up a lot more space in your home in the meantime.

It's exactly the same with the Array, where the space in your home is analogous to memory on the computer. If you make an Array with 1000000 spaces, the computer will reserve memory to hold 1000000 DVDs, even if you only put 15 DVDs into it. That memory can't be used for anything else in the meantime—just like the space in your house that has been taken over by that huge cardboard box!

### Accessing Elements in Arrays

> The two most primitive Array operations are writing elements into them, and reading elements from them. All other Array operations are built on top of these two primitive operations.

#### Writing Items into an Array

To put a DVD into the Array, we need to decide which of the 15 places we'd like it to go in. Each of the places is identified using a number in the range of *0 to N - 1*. The 1st place is 0, the 2nd place is 1, the 3rd place is 2... all the way up to the 15th place, which is 14. We call these numbers that identify each place **indexes**.

Let's put the DVD for The Avengers into the eighth place of the Array we created above.

```java
// Firstly, we need to actually create a DVD object for The Avengers.
DVD avengersDVD = new DVD("The Avengers", 2012, "Joss Whedon");

// Next, we'll put it into the 8th place of the Array. Remember, because we
// started numbering from 0, the index we want is 7.
dvdCollection[7] = avengersDVD;
```

#### Out Sourced Notes - Start 2

### Add Items and Objects to an Array Using the Assignment Operator in JavaScript

To add items and objects to an array, you can use the assignment operator in JavaScript. You have to use the index to define the position inside the array where you want to put the item or object. If an existing item already occupies the defined index, the item will be replaced with the new item or object. For example, let’s create an array with three values and add an item at the end of the array using the assignment operator. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
myArray[3] = 'four';
console.log(myArray)
// Output:
["one", "two", "three", "four"]
```

In the above code, we added the item *four* at index 3 of the *myArray*. You can also replace the items present in the array using their index. Now let’s add an object to an array. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
var myArray2 = ['four', 'five']
myArray[3] = myArray2;
console.log(myArray)
// Output:
["one", "two", "three", Array(2)]
```

In the above code, we added an array object *myArray2* to an array *myArray* at index 3. You can add objects of any data type to an array using the assignment operator.

### Add Items and Objects to an Array Using the push() Function in JavaScript

To add items and objects to an array, you can use the *push()* function in JavaScript. The *push()* function adds an item or object at the end of an array. For example, let’s create an array with three values and add an item at the end of the array using the *push()* function. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
myArray.push('four');
console.log(myArray)
// Output:
["one", "two", "three", "four"]
```

In the above code, we added the item *four* at the end of the *myArray*. Now let’s add an object to an array using the *push()* function. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
var myArray2 = ['four', 'five']
myArray.push(myArray2);
console.log(myArray)
// Output:
["one", "two", "three", Array(2)]
```

In the above code, we added an array object *myArray2* to an array *myArray* at the end. You can add objects of any data type to an array using the *push()* function. You can also add multiple values to an array by adding them in the *push()* function separated by a comma. To add the items or objects at the beginning of the array, we can use the *unshift()* function. For example, let’s add the item *four* at the beginning of the array *myArray*. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
myArray.unshift('four');
console.log(myArray)
// Output:
["four", "one", "two", "three"]
```

As you can see in the output, the item *four* is added at the beginning of the array. Instead of adding an array object, you can add all of its items using the *push.apply()* function. For example, let’s add the items present in one array to the other array. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
var myArray2 = ['four', 'five']
myArray.push.apply(myArray, myArray2);
console.log(myArray)
// Output:
["one", "two", "three", "four", "five"]
```

As you can see in the output, the two items present in the *myArray2* have been added to the *myArray*. You can also concatenate two arrays to make another array using the *concat()* function. For example, let’s create an array by concatenating two existing arrays using the *concat()* function. See the code below.

```javascript
var myArray = ['one', 'two', 'three'];
var myArray2 = ['four', 'five']
var myArray3 = myArray.concat(myArray2);
console.log(myArray3)
// Output:
["four", "five", "one", "two", "three"]
```

You can change the order of the items present in the *myArray3* by changing the order of concatenation.

#### Out Sourced Notes - End 2

### Writing Items into an Array - Continue

And that's it. We've put the DVD for The Avengers into our Array! Let's put a few more DVD's in.

```java
DVD incrediblesDVD = new DVD("The Incredibles", 2004, "Brad Bird");
DVD findingDoryDVD = new DVD("Finding Dory", 2016, "Andrew Stanton");
DVD lionKingDVD = new DVD("The Lion King", 2019, "Jon Favreau");

// Put "The Incredibles" into the 4th place: index 3.
dvdCollection[3] = incrediblesDVD;

// Put "Finding Dory" into the 10th place: index 9.
dvdCollection[9] = findingDoryDVD;

// Put "The Lion King" into the 3rd place: index 2.
dvdCollection[2] = lionKingDVD;
```

Notice that we put The Incredibles into the Array at index *3*. What happens if we now run this next piece of code?

```java
DVD starWarsDVD = new DVD("Star Wars", 1977, "George Lucas");
dvdCollection[3] = starWarsDVD;
```

Because we just put Star Wars into the Array at index *3*, The Incredibles is no longer in the Array. It has been overwritten! If we still have the *incrediblesDVD* variable in scope, then the DVD still exists in the computer's memory. If not though, it's totally gone!

#### Reading Items from an Array

We can check what's at a particular Array index.

```java
// Print out what's in indexes 7, 10, and 3.
System.out.println(dvdCollection[7]);
System.out.println(dvdCollection[10]);
System.out.println(dvdCollection[3]);

// Will print:

// The Avengers, directed by Joss Whedon, released in 2012
// null
// Star Wars, directed by George Lucas, released in 1977
```

Notice that because we haven't yet put anything at index 10, the value it contains is *null*. In other languages, such as *C*, the Array slot could contain completely random data. Java always initializes empty Array slots to *null* if the Array contains objects, or to default values if it contains primitive types. For example, the array *int [ ]* would contain the default value of *0* for each element, *float[ ]* would contain default values of *0.0*, and *bool[ ]* would contain default values of *false*.

#### Out Sourced Notes - Start 3

### Indexing Arrays

Arrays do not have name/value pairs. Instead, they are indexed with integer values beginning with *0*. Here is an example array, assigned to *seaCreatures*.

```javascript
let seaCreatures = [
    "octopus",
    "squid",
    "shark",
    "seahorse",
    "starfish",
];
```

Here is a breakdown of how each item in the *seaCreatures* array is indexed.

| octopus | squid | shark | seahorse | starfish |
|---------|-------|-------|----------|----------|
|    0    |   1   |   2   |     3    |     4    |

The first item in the array is *octopus*, which is indexed at *0*. The last item is *starfish*, which is indexed at *4*. Counting starts with *0* in indices, which goes against our natural intuition to start counting at 1, so special care must be taken to remember this until it becomes natural.

We can find out how many items are in an array with the *length* property.

```javascript
seaCreatures.length;

Output
5
```

Although the indices of *seaCreatures* consist of *0 to 4*, the *length* property will output the actual amount of items in the array, starting with 1.

If we want to find out the index number of a specific item in an array, such as *seahorse*, we can use the *indexOf()* method.

```javascript
seaCreatures.indexOf("seahorse");

Output
3

//If an index number is not found, such as for a value that does not exist, the console will return -1.
seaCreatures.indexOf("cuttlefish");

Output
-1
```

With index numbers that correspond to items within an array, we’re able to access each item discretely in order to work with those items.

#### Out Sourced Notes - End 3

#### Writing Items into an Array with a Loop

We commonly use a loop to put lots of values into an Array. To illustrate this, let's go to another example. This time, we're going to create an Array of *int*s and put the first *10* square numbers into it.

```java
int[] squareNumbers = new int[10];

// Go through each of the Array indexes, from 0 to 9.
for (int i = 0; i < 10; i++) {
    // We need to be careful with the 0-indexing. The next square number
    // is given by (i + 1) * (i + 1).
    // Calculate it and insert it into the Array at index i.
    int square = (i + 1) * (i + 1);
    squareNumbers[i] = square;
}
```

#### Reading Items from an Array with a Loop

We can also use a loop to print out everything that's in the Array.

```java
// Go through each of the Array indexes, from 0 to 9.
for (int i = 0; i < 10; i++) {
    // Access and print what's at the i'th index.
    System.out.println(squareNumbers[i]);
}

// Will print:
// 1
// 4
// 9
// 16
// 25
// 36
// 49
// 64
// 81
// 100
```

One last thing worth knowing now is that there's a more elegant way of printing out the values of an Array — a variant of the *for* loop, commonly referred to as a "for each" loop.

```java
// For each VALUE in the Array.
for (int square : squareNumbers) {
    // Print the current value of square.
    System.out.println(square);
}
// Prints exactly the same as the previous example.
```

You'll probably agree that this code is a lot simpler to read. We can use it whenever we don't need the index values. For actually writing the squares into the Array, it wouldn't have worked because we needed to work with the actual index numbers. You don't have to use a "for each" loop when you're starting out, but we recommend you become comfortable with it before interviews. Simple, elegant code is good code!

#### Out Sourced Notes - Start 4

### Accessing Items in an Array

An item in a JavaScript array is accessed by referring to the index number of the item in square brackets.

```javascript
seaCreatures[1];

//Output
squid
```

We know *0* will always output the first item in an array. We can also find the last item in an array by performing an operation on the *length* property and applying that as the new index number.

```javascript
const lastIndex = seaCreatures.length - 1;

seaCreatures[lastIndex];

//Output
starfish

// Attempting to access an item that doesn’t exist will return undefined.
seaCreatures[10];

//Output
undefined
```

In order to access items in a nested array, you would add another index number to correspond to the inner array.

```javascript
let nestedArray = [
    [
        "salmon",
        "halibut",
    ],
    [
        "coral",
        "reef",
    ]
];

nestedArray[1][0];

//Output
coral
```

In the above example, we accessed the array at position *1* of the *nestedArray* variable, then the item at position *0* in the inner array.

#### Adding an Item to an Array

In our *seaCreatures* variable we had five items, which consisted of the indices from *0 to 4*. If we want to add a new item to the array, we can assign a value to the next index.

```javascript
seaCreatures[5] = "whale";

seaCreatures;

//Output
[ 'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale' ]

// If we add an item and accidentally skip an index, it will create an undefined item in the array.
seaCreatures[7] = "pufferfish";

seaCreatures;

//Output
[ 'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    ,
    'pufferfish' ]

// Attempting to access the extra array item will return undefined.
seaCreatures[6]

//Output
undefined
```

Issues like that can be avoided by using the *push()* method, which adds an item to the end of an array.

```javascript
// Append lobster to the end of the seaCreatures array
seaCreatures.push("lobster");

seaCreatures;

//Output
[ 'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    ,
    'whale',
    'pufferfish',
    'lobster' ]
```

On the other end of the spectrum, the *unshift()* method will add an item to the beginning of an array.

```javascript
// Append dragonfish to the beginning of the seaCreatures array
seaCreatures.unshift("dragonfish");

seaCreatures;

//Output
[ 'dragonfish',
    'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    ,
    'pufferfish',
    'lobster' ]
```

Between *push() and unshift()* you will be able to apend items to the beginning and end of an array.

#### Removing an Item from an Array

When we want to remove a specific item from an array, we use the *splice()* method. In the *seaCreatures* array, we accidentally created an undefined array item earlier, so let’s remove that now.

```javascript
seaCreatures.splice(7, 1);

seaCreatures;

//Output
[ 'dragonfish',
    'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    'pufferfish',
    'lobster' ]
```

In the *splice()* method, the first parameter stands for the index number to be removed (in this case, *7*), and the second parameter is how many items should be removed. We put *1*, signifying that only one item will be removed.

The *splice()* method will change the original variable. If you would like the original variable to remain unchanged, use *slice()* and assign the result to a new variable. Here we will assign two variables, one that uses *slice()* to store the *seaCreatures* array from the first element until *whale*, and a second variable to store the elements *pufferfish* and *lobster*. To join the two arrays, we’ll use the *concat()* method to return the new array.

```javascript
let firstArray = seaCreatures.slice(0, 7);
let secondArray = seaCreatures.slice(8, 10);

firstArray.concat(secondArray);

//Output
[ 'dragonfish',
    'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    'pufferfish',
    'lobster' ]
```

Notice that when calling the *seaCreatures* variable, the items in the array remain unchanged.

```javascript
seaCreatures;

//Output
[ 'dragonfish',
    'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    ,
    'pufferfish',
    'lobster' ]
```

The *pop()* method will remove the last item in an array.

```javascript
// Remove the last item from the seaCreatures array
seaCreatures.pop();

seaCreatures;

//Output
[ 'dragonfish',
    'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    'pufferfish' ]
```

*lobster* has been removed as the last item of the array. In order to remove the first item of the array, we will use the *shift()* method.

```javascript
// Remove the first item from the seaCreatures array
seaCreatures.shift();

seaCreatures;

//Output
[ 'octopus',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    'pufferfish' ]
```

By using *pop() and shift()*, we can remove items from the beginning and the end of arrays. Using *pop()* is preferred wherever possible, as the rest of the items in the array retain their original index numbers.

### Modifying Items in Arrays

We can overwrite any value in an array by assigning a new value using the assignment operator, just like we would with a regular variable.

```javascript
// Assign manatee to the first item in the seaCreatures array
seaCreatures[0] = "manatee";

seaCreatures;

//Output
[ 'manatee',
    'squid',
    'shark',
    'seahorse',
    'starfish',
    'whale',
    'pufferfish' ]
```

Another way to modify a value is using the *splice()* method with a new parameter. If we wanted to change the value of *seahorse*, which is the item at index *3*, we could remove it and add a new item in its place.

```javascript
// Replace seahorse with sea lion using splice method
seaCreatures.splice(3, 1, "sea lion");

seaCreatures();

//Output
[ 'manatee',
    'squid',
    'shark',
    'sea lion',
    'starfish',
    'whale',
    'pufferfish' ]
```

In the above example, we removed *seahorse* from the array, and pushed a new value into index *3*.

### Looping Through an Array

We can loop through the entirety of the array with the *for* keyword, taking advantage of the *length* property. In this example, we can create an array of *shellfish* and print out each index number as well as each value to the console.

```javascript
// Create an array of shellfish species
let shellfish = [
    "oyster",
    "shrimp",
    "clam",
    "mussel",
];

// Loop through the length of the array
for (let i = 0; i < shellfish.length; i++) {
  console.log(i, shellfish[i]);
}

//Output
0 'oyster'
1 'shrimp'
2 'clam'
3 'mussel'
```

We can also use the *for...of* loop, a newer feature of JavaScript.

```javascript
// Create an array of aquatic mammals
let mammals = [
    "dolphin",
    "whale",
    "manatee",
];

// Loop through each mammal
for (let mammal of mammals) {
    console.log(mammal);
}

//Output
dolphin
whale
manatee
```

The *for...of* loop does not retrieve the index number of the elements in the array, but it is generally a simpler, more concise way to loop through an array.

Using loops is extremely useful for printing out the whole value of an array, such as when displaying the items from a database on a website.

### Conclusion

Arrays are an extremely versatile and fundamental part of programming in JavaScript. In this tutorial, we learned how to create an array, how arrays are indexed, and some of the most common tasks of working in arrays, such as creating, removing, and modifying items. We also learned two methods of looping through arrays, which is used as a common method to display data.

#### Out Sourced Notes - End 4

### Array Capacity VS Length

> If somebody asks you how long the DVD Array is, what what would your answer be?

There are two different answers you might have given.

1. The number of DVDs the box could hold, if it was full, or
2. The number of DVDs currently in the box.

Both answers are correct, and both have very different meanings! It's important to understand the difference between them, and use them correctly. We call the first one the *capacity* of the Array, and the second one the *length* of the Array.

#### Array Capacity

Let's say we've created a new Array like this.

```java
DVD[] array = new DVD[6]
```

Is it a valid operation to insert an element at *array[6]*? What about at *array[10]*? Nope, neither of these are valid. When we created the Array, we specified that it can hold up to *6* DVD's. This is the Array's **capacity**.

Remembering that indexing starts at *0*, we can only insert items at *array[0], array[1], array[2], array[3], array[4], and array[5]*. Trying to put an element anywhere else, such as *array[-3], array[6], or array[100]* will cause your code to crash with an *ArrayIndexOutOfBoundsException*!

The Array's capacity must be decided when the Array is created. The capacity cannot be changed later. Going back to our DVD's-in-a-cardboard-box-analogy, changing the capacity of an Array would be akin to trying to make a cardboard box bigger. Trying to make a fixed-size cardboard box bigger is impractical, and it's the same as an Array on a computer!

So, what do we do if we get a 7th DVD and we'd like all our DVD's in the same Array? Well, unfortunately it's the same as it is with our cardboard box. We'll need to go get a larger one, and then move all the existing DVD's into it, along with the new one.

The **capacity** of an Array in Java can be checked by looking at the value of its *length* attribute. This is done using the code *arr.length*, where *arr* is the name of the Array. Different programming languages have different ways of checking the length of an Array.

```java
int capacity = array.length;
System.out.println("The Array has a capacity of " + capacity);
```

Running this code will give the following output:
> The Array has a capacity of 6

Yup, it's a bit confusing that you need to access the capacity of an Array by using *.length*. Unfortunately, this is just something you'll need to get used to.

#### Array Length

The other definition of **length** is the number of DVDs, or other items, currently in the Array. This is something you'll need to keep track of yourself, and you won't get any errors if you overwrite an existing DVD, or if you leave a gap in the Array.

You might have noticed that we've been using a *length* variable in our previous examples, to keep track of the next empty index.

```java
// Create a new array with a capacity of 6.
int[] array = new int[6];

// Current length is 0, because it has 0 elements.
int length = 0;

// Add 3 items into it.
for (int i = 0; i < 3; i++) {
    array[i] = i * i;
    // Each time we add an element, the length goes up by one.
    length++;
}

System.out.println("The Array has a capacity of " + array.length);
System.out.println("The Array has a length of " + length);
```

Running this code will give the following output:
> The Array has a capacity of 6
The Array has a length of 3

#### Handling Array Parameters

Most Array questions on LeetCode have an Array passed in as a parameter, with no "length" or "capacity" parameter. What do we mean by this? Well, let's look at an example. Here is the description for the first problem you'll be asked to solve.
> Given a binary array, find the maximum number of consecutive 1s in this array.

And here is the code template you're given.

The only parameter is *nums*; an Array. You couldn't possibly solve this question without knowing how long *nums* is. Well, luckily it's straightforward. When an Array is given as a parameter, without any additional information, you can safely assume that **length == capacity**. That is, the Array is the exact right size to hold all of it's data. We can, therefore, use *.length*.

Be careful though, Array's are 0-indexed. The *capacity/ length* is a number of items, not a highest index. The highest index is *.length - 1*. Therefore, to iterate over all items in the Array, we can do the following.

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        // Hint: Initialise and declare a variable here to 
        // keep track of how many 1's you've seen in a row.
        for (int i = 0; i < nums.length; i++) {
            // Do something with element nums[i].
        }
    }
}
```

And that is the basics of Arrays that you'll need to get started! In the next chapter, we'll look at some of the fundamental techniques we use to work with Arrays.

Before that though, we have a few introductory Array problems for you to play around with, starting with the one we briefly looked at above. Enjoy!

### 485. Max Consecutive Ones

Given a binary array nums, return the maximum number of consecutive 1's in the array.

Example 1:

Input: nums = [1,1,0,1,1,1]

Output: 3

Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3

Example 2:

Input: nums = [1,0,1,1,0,1]

Output: 2

Constraints:

* 1 <= nums.length <= 10^5
* nums[i] is either 0 or 1.

Hint #1

You need to think about two things as far as any window is concerned. One is the starting point for the window. How do you detect that a new window of 1s has started? The next part is detecting the ending point for this window. How do you detect the ending point for an existing window? If you figure these two things out, you will be able to detect the windows of consecutive ones. All that remains afterward is to find the longest such window and return the size.

### Answer 1

```javascript
const findMaxConsecutiveOnes = (nums) => {
  let max = 0;
  let cur = 0;
  for (const num of nums) {
    num ? ++cur > max && (max = cur) : (cur = 0);
  }
  return max;
};

// Your input
[1,1,0,1,1,1]
//Output
3
// Expected
3
```

### 1295. Find Numbers with Even Number of Digits

Given an array nums of integers, return how many of them contain an even number of digits.

Example 1:

Input: nums = [12,345,2,6,7896]

Output: 2

Explanation:

* 12 contains 2 digits (even number of digits).
* 345 contains 3 digits (odd number of digits).
* 2 contains 1 digit (odd number of digits).
* 6 contains 1 digit (odd number of digits).
* 7896 contains 4 digits (even number of digits).
* Therefore only 12 and 7896 contain an even number of digits.

Example 2:

Input: nums = [555,901,482,1771]

Output: 1

Explanation:

Only 1771 contains an even number of digits.

Constraints:

* 1 <= nums.length <= 500
* 1 <= nums[i] <= 10^5

Hint #1: How to compute the number of digits of a number ?

Hint #2: Divide the number by 10 again and again to get the number of digits.

### Answer 2

```javascript
var findNumbers = function(nums) {
var even = 0;
for(var i=0;i<nums.length;i++){
if(nums[i].toString().length % 2 === 0){
even++;
}
}
return even;
};

// Your input
[12,345,2,6,7896]
//Output
2
// Expected
2

var findNumbers = (nums) => nums.map(String).filter(num => num.length % 2 === 0).length;
```

### 977. Squares of a Sorted Array

Given an integer array *nums* sorted in **non-decreasing** order, return an array of **the squares of each number** sorted in non-decreasing order.

Example 1:

Input: nums = [-4,-1,0,3,10]

Output: [0,1,9,16,100]

Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].

Example 2:

Input: nums = [-7,-3,2,3,11]

Output: [4,9,9,49,121]

Constraints:

* 1 <= nums.length <= 10^4
* -104 <= nums[i] <= 10^4
* nums is sorted in non-decreasing order.

Follow up: Squaring each element and sorting the new array is very trivial, could you find an O(n) solution using a different approach?

### Answer 3

```javascript
var sortedSquares = function(nums) {
    let squared = [], l = 0, r = nums.length - 1;

    while (l <= r) {
        if (Math.abs(nums[l]) > Math.abs(nums[r]))
            squared.push(nums[l++] ** 2);
        else
            squared.push(nums[r--] ** 2);
    }
    return squared.reverse();
};

// Your input
[-4,-1,0,3,10]
//Output
[0,1,9,16,100]
// Expected
[0,1,9,16,100]
```

## 2-Inserting Items Into an Array

In the previous chapter, we looked at what Arrays are, and the basic programming constructs of Arrays in Java. We're now going to use these basic constructs to implement three key operations for Arrays:

* Inserting items.
* Removing items.
* Searching for items.

> These three operations are the fundamental operations for all data structures.

In this chapter, we'll be starting with **inserting items into an array**. Like before, we'll approach the learning with lots of examples and programming snippets. After that, there are some more interview questions for you to practice on. We hope you have fun!

### Basic Array Operations

Now that we have a fairly good understanding of what an *Array* actually is, and how it is stored inside the computer's physical memory, the next important thing to look at is all the operations that Arrays support. An *Array* is a **data structure**, which means that it stores data in a specific format and supports certain operations on the data it stores. Consider the *DVD inventory management software* from the introduction section. Let's look at some operations you might want to perform using this software:

* **Insert** a new DVD into the collection at a specific location.
* **Delete** a DVD from the existing collection if it doesn't make sense to keep it in the inventory anymore.
* **Search** for a particular DVD in the collection. *This is one of the most commonly executed operation on our collection, because our inventory management software would be used hundreds of times a day to look for a particular DVD asked for by the user*.

In this section, we'll be looking at the three basic operations that are supported by almost every data structure; **insertion**, **deletion**, and **search**.

### Array Insertions

>In the previous chapter, we looked at how to write elements to an Array. There is a lot more to inserting elements though, as we're about to see!

Inserting a new element into an Array can take many forms:

1. Inserting a new element at the end of the Array.
2. Inserting a new element at the beginning of the Array.
3. Inserting a new element at any given index inside the Array.

#### Inserting at the End of an Array

At any point in time, we know the index of the last element of the Array, as we've kept track of it in our *length* variable. All we need to do for inserting an element at the end is to assign the new element to one index past the current last element.

![Array_Insertion_1](https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/Figures/Array_Explore/Array_Insertion_1.png)

This is pretty much the same as we've already seen. Here's the code to make a new Array that can hold up to *6* items, and then add items into the first *3* three indexes.

```java
// Declare an integer array of 6 elements
int intArray = new int[6];
int length = 0;

// Add 3 elements to the Array
for (int i = 0; i < 3; i++) {
    intArray[length] = i;
    length++;
}
```

Let's define a function, *printArray*, to help us visualise what's happening.

```java
for (int i = 0; i < intArray.length; i++) {
    System.out.println("Index " + i + " contains " + intArray[i]);
}
```

If we run our printArray function, we'll get the following output.

```java
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 0.
Index 4 contains 0.
Index 5 contains 0.
```

Notice how indexes *3, 4,* and *5* all contain *0*? This is because Java fills unused *int* Array slots with *0*s.

Let's now add a 4th element. We'll add the number 10.

```java

// Insert a new element at the end of the Array. Again,
// it's important to ensure that there is enough space
// in the array for inserting a new element.
intArray[length] = 10;
length++;
```

Notice how we also incremented the length? This is very important, next time when we add another element, we'll accidentally overwrite the one we just added!

Running *printArray* again, we'll get the following:

```java
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 10.
Index 4 contains 0.
Index 5 contains 0.
```

#### Inserting at the Start of an Array

To insert an element at the start of an Array, we'll need to shift all other elements in the Array to the right by one index to create space for the new element. This is a very costly operation, since each of the existing elements has to be shifted one step to the right. The need to shift everything implies that this is not a constant time operation. In fact, the time taken for insertion at the beginning of an Array will be proportional to the length of the Array. In terms of time complexity analysis, this is a linear time complexity: **O(N)**, where **N** is the length of the Array.

![Array_Insertion_2](https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/Figures/Array_Explore/Array_Insertion_2.png)

Here's what this looks like in code.

```java
// First, we will have to create space for a new element.
// We do that by shifting each element one index to the right.
// This will firstly move the element at index 3, then 2, then 1, then finally 0.
// We need to go backwards to avoid overwriting any elements.
for (int i = 3; i >= 0; i--) {
    intArray[i + 1] = intArray[i];
}

// Now that we have created space for the new element,
// we can insert it at the beginning.
intArray[0] = 20;
```

And here's the result of running printArray.

```java
Index 0 contains 20.
Index 1 contains 0.
Index 2 contains 1.
Index 3 contains 2.
Index 4 contains 10.
Index 5 contains 0.
```

#### Inserting Anywhere in the Array

Similarly, for inserting at any given index, we first need to shift all the elements from that index onwards one position to the right. Once the space is created for the new element, we proceed with the insertion. If you think about it, insertion at the beginning is basically a special case of inserting an element at a given index—in that case, the given index was *0*.

![Array_Insertion_3](https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/Figures/Array_Explore/Array_Insertion_3.png)

Again, this is also a costly operation since we could *potentially* have to shift almost all the other elements to the right before actually inserting the new element. As your saw above, shifting lots of elements one place to the right adds to the time complexity of the insertion task.

Here's what it looks like in code.

```java
// Say we want to insert the element at index 2.
// First, we will have to create space for the new element.
for (int i = 4; i >= 2; i--)
{
    // Shift each element one position to the right.
    intArray[i + 1] = intArray[i];
}

// Now that we have created space for the new element,
// we can insert it at the required index.
intArray[2] = 30;
```

And here's the result of running *printArray*.

```java
Index 0 contains 20.
Index 1 contains 0.
Index 2 contains 30.
Index 3 contains 1.
Index 4 contains 2.
Index 5 contains 10.
```

Does that all sound good? The main thing to be careful of is remembering that *array.length* gives you the total capacity of the Array. If you want to know the last used slot, you'll need to keep track of this yourself using a *length* variable. Other than that, just be careful to read any elements you want to keep, before you overwrite them!

We now have a fun problem for you to test your understanding on. Enjoy!

### 1089. Duplicate Zeros

Given a fixed-length integer array *arr*, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written. Do the above modifications to the input array in place and do not return anything.

Example 1:

Input: arr = [1,0,2,3,0,4,5,0]

Output: [1,0,0,2,3,0,0,4]

Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]

Example 2:

Input: arr = [1,2,3]

Output: [1,2,3]

Explanation: After calling your function, the input array is modified to: [1,2,3]

Constraints:

* 1 <= arr.length <= 10^4
* 0 <= arr[i] <= 9

Hint #1

* This is a great introductory problem for understanding and working with the concept of in-place operations. The problem statement clearly states that we are to modify the array in-place. That does not mean we cannot use another array. We just don't have to return anything.

Hint #2

* A better way to solve this would be without using additional space. The only reason the problem statement allows you to make modifications in place is that it hints at avoiding any additional memory.

Hint #3

* The main problem with not using additional memory is that we might override elements due to the zero duplication requirement of the problem statement. How do we get around that?

Hint #4

* If we had enough space available, we would be able to accommodate all the elements properly. The new length would be the original length of the array plus the number of zeros. Can we use this information somehow to solve the problem?

### Answer 4

```javascript
var duplicateZeros = function(arr) {
    for(let i = 0; i < arr.length; i++) {
        if(arr[i] === 0) {
            arr.splice(i, 0, 0);
            i = i + 1;
            arr.pop()
        }
       
    }
};

// Your input
[1,0,2,3,0,4,5,0]
//Output
[1,0,0,2,3,0,0,4]
// Expected
[1,0,0,2,3,0,0,4]
```

### 88. Merge Sorted Array

You are given two integer arrays *nums1 and nums2*, sorted in *non-decreasing order*, and two integers *m and n*, representing the number of elements in *nums1 and nums2* respectively.

*Merge nums1 and nums2* into a single array sorted in *non-decreasing order*.

The final sorted array should not be returned by the function, but instead be stored inside the array *nums1*. To accommodate this, *nums1* has a length of *m + n*, where the first *m* elements denote the elements that should be merged, and the last *n* elements are set to *0* and should be ignored. *nums2* has a length of *n*.

Example 1:

Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3

Output: [1,2,2,3,5,6]

Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
Example 2:

Input: nums1 = [1], m = 1, nums2 = [], n = 0

Output: [1]

Explanation: The arrays we are merging are [1] and [].
The result of the merge is [1].
Example 3:

Input: nums1 = [0], m = 0, nums2 = [1], n = 1

Output: [1]

Explanation: The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.

Constraints:

* nums1.length == m + n
* nums2.length == n
* 0 <= m, n <= 200
* 1 <= m + n <= 200
* -10^9 <= nums1[i], nums2[j] <= 10^9

Follow up: Can you come up with an algorithm that runs in O(m + n) time?

Hint #1

* You can easily solve this problem if you simply think about two elements at a time rather than two arrays. We know that each of the individual arrays is sorted. What we don't know is how they will intertwine. Can we take a local decision and arrive at an optimal solution?

Hint #2

* If you simply consider one element each at a time from the two arrays and make a decision and proceed accordingly, you will arrive at the optimal solution.

### Answer 5

```javascript
var merge = function(nums1, m, nums2, n) {
    
    let i = 0;
    let j = 0;
    
    while (nums2[j] !== undefined) {
        if (nums1[i] <= nums2[j] && i < m) {
            i++;
        } else if (nums1[i] <= nums2[j] && i >= m) {
            nums1.splice(i, 1, nums2[j]);
            i++;
            j++;
        } else {
            nums1.splice(i, 0, nums2[j]);
            nums1.pop();
            m++;
            i++;
            j++;
        }
    }
};

var merge =(a,m,b,n)=>{

while (n>0 ){
    if(a[m-1]> b[n-1]){
        a[m+n-1]=a[m-1];
        m-=1;
    }
    else{
        a[m+n-1]=b[n-1];
        n-=1;
    }
}
// return a;
};

// Your input
[1,2,3,0,0,0]
3
[2,5,6]
3
//Output
[1,2,2,3,5,6]
// Expected
[1,2,2,3,5,6]
```

## 3-Deleting Items From an Array

Next on the agenda is insertion's complement—deletion.

### Array Deletions

> Now that we know how insertion works, it's time to look at its complement—deletion!

Deletion in an Array works in a very similar manner to insertion, and has the same three different cases:

1. Deleting the last element of the Array.
2. Deleting the first element of the Array.
3. Deletion at any given index.

#### Deleting From the End of an Array

Deletion at the end of an Array is similar to people standing in a line, also known as a *queue*. The person who most recently joined the queue (at the end) can leave at any time without disturbing the rest of the *queue*. Deleting from the end of an Array is the least time consuming of the three cases. Recall that insertion at the end of an Array was also the least time-consuming case for insertion.

![Array_Deletion_1](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/Figures/Array_Explore/Array_Deletion_1.png)

So, how does this work in code? Before we look at this, let's quickly remind ourselves what the length of an Array means. Here is some code that creates an Array with room for 10 elements, and then adds elements into the first 6 indexes of it.

```java
// Declare an integer array of 10 elements.
int[] intArray = new int[10];

// The array currently contains 0 elements
int length = 0;

// Add elements at the first 6 indexes of the Array.
for(int i = 0; i < 6; i++) {
    intArray[length] = i;
    length++;
}
```

Notice the *length* variable. Essentially, this variable keeps track of the next index that is free for inserting a new element. This is always the same value as the overall length of the Array. Note that when we declare an Array of a certain size, we simply fix the maximum number of elements it could contain. Initially, the Array doesn't contain anything. Thus, when we add new elements, we also increment the *length* variable accordingly.

Anyway, here's the code for deleting the last element of an Array.

```java
// Deletion from the end is as simple as reducing the length
// of the array by 1.
length--;
```

Remember how insertion we were using this printArray function?

```java
for (int i = 0; i < intArray.length; i++) {
    System.out.println("Index " + i + " contains " + intArray[i]);
}
```

Well, if we run it here, we'll get the following result, regardless of whether we run it before or after removing the last element.

```java
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 3.
Index 4 contains 4.
Index 5 contains 5.
Index 6 contains 0.
Index 7 contains 0.
Index 8 contains 0.
Index 9 contains 0.
```

What's gone wrong? Well, remember how there's two different definitions of length? When we use *intArray.length*, we're looking every valid index of the Array. When in fact, we only want to look at the ones that we've put values into. The fix is easy, we just iterate up to our own *length* variable instead.

```java
for (int i = 0; i < length; i++) {
    System.out.println("Index " + i + " contains " + intArray[i]);
}
```

Run this, and you'll get the following before the deletion:

```java
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 3.
Index 4 contains 4.
Index 5 contains 5.
```

And the following after:

```java
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 3.
Index 4 contains 4.
```

Yup, that's it! Even though we call it a deletion, its not like we actually freed up the space for a new element, right? This is because we don't actually need to free up any space. Simply overwriting the value at a certain index deletes the element at that index. Seeing as the length variable in our examples tells us the next index where we can insert a new element, reducing it by one ensures the next new element is written over the deleted one. This also indicates that the Array now contains one less element, which is exactly what we want programmatically.

#### Deleting From the Start of an Array

Next comes the costliest of all deletion operations for an Array—deleting the first element. If we want to delete the first element of the Array, that will create a vacant spot at the *0th* index. To fill that spot, we will shift the element at index *1* one step to the left. Going by the ripple effect, every element all the way to the last one will be shifted one place to the left. This shift of elements takes *O(N)* time, where *N* is the number of elements in the Array.

![Array_Deletion_2](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/Figures/Array_Explore/Array_Deletion_2.png)

Here is how deleting the first element looks in code.

```java
// Starting at index 1, we shift each element one position
// to the left.
for (int i = 1; i < length; i++) {
    // Shift each element one position to the left
    int_array[i - 1] = int_array[i];
}

// Note that it's important to reduce the length of the array by 1.
// Otherwise, we'll lose consistency of the size. This length
// variable is the only thing controlling where new elements might
// get added.
length--;
```

Starting from index *0*, we'll move every element one position to its left, effectively "deleting" the element at index *0*. We also need to reduce *length* by *1* so that the next new element is inserted in the correct position.

And here's the output we'll get, with our updated *printArray* function.

```java
Index 0 contains 1.
Index 1 contains 2.
Index 2 contains 3.
Index 3 contains 4.
```

#### Deleting From Anywhere in the Array

For deletion at any given index, the empty space created by the deleted item will need to be filled. Each of the elements to the right of the index we're deleting at will get shifted to the left by one. Deleting the first element of an Array is a special case of deletion at a given index, where the index is *0*. This shift of elements takes *O(K)* time where *K* is the number of elements to the right of the given index. Since potentially *K = N*, we say that the time complexity of this operation is also *O(N)*.

![Array_Deletion_3](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/Figures/Array_Explore/Array_Deletion_3.png)

Here is the code to delete the element at index 1. To do this, we'll need to move over the elements after it in the Array.

```java
// Say we want to delete the element at index 1
for (int i = 2; i < length; i++) {
    // Shift each element one position to the left
    int_array[i - 1] = int_array[i];
}

// Again, the length needs to be consistent with the current
// state of the array.
length--;
```

Notice that this works exactly like deleting the first element, except that we don't touch the elements that are at lower indexes than the element we're deleting.

Here is the output from the *printArray* function.

```java
Index 0 contains 1.
Index 1 contains 3.
Index 2 contains 4.
```

Did that all make sense? To help you cement what you've learned, here's a couple of programming problems for you to try. You should try to solve them without making a new Array. Do this by using the deletion techniques we've investigated above.

Once you're done, we'll look at *searching Arrays*!

### 27. Remove Element

Given an integer array *nums* and an integer *val*, remove all occurrences of *val* in *nums in-place*. The relative order of the elements may be changed.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the *first part* of the array *nums*. More formally, if there are *k* elements after removing the duplicates, then the first *k* elements of *nums* should hold the final result. It does not matter what you leave beyond the first *k* elements.

Return *k* after placing the final result in the first *k* slots of *nums*.

Do *not* allocate extra space for another array. You must do this by *modifying the input array in-place with O(1)* extra memory.

**Custom Judge:**

The judge will test your solution with the following code:

```java
int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // The expected answer with correct length.
                            // It is sorted with no values equaling val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be accepted.

Example 1:

Input: nums = [3,2,2,3], val = 3

Output: 2, nums = [2,2,_,_]

Explanation: Your function should return k = 2, with the first two elements of nums being 2.

It does not matter what you leave beyond the returned k (hence they are underscores).

Example 2:

Input: nums = [0,1,2,2,3,0,4,2], val = 2

Output: 5, nums = [0,1,4,0,3,_,_,_]

Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.

Note that the five elements can be returned in any order.

It does not matter what you leave beyond the returned k (hence they are underscores).

Constraints:

* 0 <= nums.length <= 100
* 0 <= nums[i] <= 50
* 0 <= val <= 100

### Answer 6

In computer science, an *in-place algorithm* is an algorithm which transforms input using no auxiliary data structure. However, a small amount of extra storage space is allowed for auxiliary variables. The input is usually overwritten by the output as the algorithm executes. An *in-place algorithm* updates its input sequence only through replacement or swapping of elements. An algorithm which is not in-place is sometimes called not-in-place or out-of-place.

In-place can have slightly different meanings. In its strictest form, the algorithm can only have a constant amount of extra space, counting everything including function calls and pointers. However, this form is very limited as simply having an index to a length n array requires O(log n) bits. More broadly, in-place means that the algorithm does not use extra space for manipulating the input but may require a small though nonconstant extra space for its operation. Usually, this space is O(log n), though sometimes anything in O(n) is allowed.

```javascript
/*
Time: O(n)
Space : O(1)
*/
const removeElement = (nums, val) => {
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] === val) {
      nums.splice(i, 1)
      i--
    }
  }

  return nums.length
};


// O(n) solution
var removeElement = function(nums, val) {
    let rightIdx = nums.length - 1;
    let rightVal;
    for (let i = nums.length - 1; i > -1; i--) {
        const element = nums[i];
        if (element === val) {
            if (rightVal !== undefined) {
                nums[i] = rightVal;
                nums[rightIdx] = '_';
                rightIdx--;
                rightVal = nums[rightIdx];
            } else {
                nums[i] = '_';
                rightIdx--;
            }
        } else if (rightVal == undefined) {
            rightVal = element;
        }
    }
    return rightIdx + 1;
};

// Your input
[3,2,2,3]
3
//Output
[2,2]
// Expected
[2,2]
```

### 26. Remove Duplicates from Sorted Array

Given an integer array *nums* sorted in *non-decreasing order*, remove the duplicates in-place such that each unique element appears only once. The *relative order* of the elements should be kept the *same*.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the *first part* of the array *nums*. More formally, if there are *k* elements after removing the duplicates, then the first *k* elements of *nums* should hold the final result. It does not matter what you leave beyond the first *k* elements.

Return *k* after placing the final result in the first *k* slots of *nums*.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

**Custom Judge:**

The judge will test your solution with the following code:

```java
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be *accepted*.

Example 1:

Input: nums = [1,1,2]

Output: 2, nums = [1,2,_]

Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

Example 2:

Input: nums = [0,0,1,1,1,2,2,3,3,4]

Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]

Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

Constraints:

* 0 <= nums.length <= 3 * 104
* -100 <= nums[i] <= 100
* nums is sorted in non-decreasing order.

### Answer 7

```javascript
/*
The strategy for this problem is:

1. using a pointer to maintain the index of the last unique number
2. traverse the array and compare the number to last unique number since the array is in non-decreasing order
3. update pointer and the value inplace
4. return the length of unique numbers
*/

/*
EASY READING
This is for easy reading:
*/
const removeDuplicates = (nums) => {
  let cur = 0;
  for (let i = 1; i < nums.length; ++i) {
    if (nums[i] === nums[cur]) continue;
    ++cur;
    nums[cur] = nums[i];
  }
  return cur + 1;
};

/*
LESS CODE
This is for less code but the logic is the same as above:
*/
const removeDuplicates = (nums) => {
  let cur = 0;
  for (const n of nums) {
    n > nums[cur] && (nums[++cur] = n);
  }
  return cur + 1;
};

// Your input
[1,1,2]
//Output
[1,2]
// Expected
[1,2]
```

## 4-Searching for Items in an Array

Finally, we're going to look at the *linear search* algorithm—the most basic and versatile array search algorithm.

### Search in an Array

> Finally, we're going to look at the most important operation of all. More often than not, it comes down to the speed of searching for an element in a data structure that helps programmers make design choices for their codebases.

There's more than one way of searching an Array, but for now, we're going to focus on the simplest way. Searching means to find an occurrence of a particular element in the Array and return its position. We might need to search an Array to find out whether or not an element is present in the Array. We might also want to search an Array that is arranged in a specific fashion to determine which index to insert a new element at.

If we know the index in the Array that may contain the element we're looking for, then the search becomes a constant time operation—we simply go to the given index and check whether or not the element is there.

#### Linear Search

If the index is not known, which is the case most of the time, then we can check every element in the Array. We continue checking elements until we find the element we're looking for, or we reach the end of the Array. This technique for finding an element by checking through all elements one by one is known as the *linear search* algorithm. In the worst case, a *linear search* ends up checking the entire Array. Therefore, the time complexity for a *linear search* is *O(N)*.

![Array_Search_1](https://leetcode.com/explore/learn/card/fun-with-arrays/527/searching-for-items-in-an-array/Figures/Array_Explore/Array_Search_1.png)

Let's see the *linear search* algorithm in action, with all the edge cases handled properly. When we say edge cases, we basically mean scenarios that you wouldn't expect to encounter. For example, the element you're searching for might not even exist in the Array. Or, an even rarer, but possible, scenario is that the input Array doesn't contain any elements at all, or perhaps it is null. It's important to handle all of these edge cases within the code.

```java
public static boolean linearSearch(int[] array, int length, int element) {
    // Check for edge cases. Is the array null or empty?
    // If it is, then we return false because the element we're
    // searching for couldn't possibly be in it.
    if (array == null || length == 0) {
        return false;
    }

    // Carry out the linear search by checking each element,
    // starting from the first one.
    for (int i = 0; i < length; i++) {
        // We found the element at index i.
        // So we return true to say it exists.
        if (array[i] == element) {
            return true;
        }
    }

    // We didn't find the element in the array.
    return false;
}
```

That's the function we can call to determine whether or not a particular element is in an Array. Notice how we take care of the edge cases before proceeding with the actual search, and that we don't check the rest of the elements once we'd found the element we were looking for.

There are many variations to this algorithm, such as returning the first location, last location, or all the locations (an element could be in the Array more than once). Let's see what happens when we call the *linearSearch* function.

```java
public class ArraySearch {
    public static void main(String args[]) {

        // Declare a new array of 6 elements
        int[] array = new int[6];

        // Variable to keep track of the length of the array
        int length = 0;

        // Iterate through the 6 indexes of the Array.
        for (int i = 0; i < 6; i++) {
            // Add a new element and increment the length as well
            array[length++] = i;
        }

        // Print out the results of searching for 4 and 30.
        System.out.println("Does the array contain the element 4? - " + ArraySearch.linearSearch(array, length, 4));
        System.out.println("Does the array contain the element 30? - " + ArraySearch.linearSearch(array, length, 30));

        // Does the array contain the element 4? - true
        // Does the array contain the element 30? - false
    }

    public static boolean linearSearch(int[] array, int length, int element) {
        // Check for edge cases
        if (array == null || length == 0) {
            return false;
        }

        // Check each element starting from the first one
        for (int i = 0; i < length; i++) {
            // We found the element at index i, so return true.
            if (array[i] == element) {
                return true;
            }
        }

        // We didn't find the element in the array.
        return false;
    }
}
```

As expected, we're able to find the element *4* in the Array, but not *30*.

#### Binary Search

*This section is optional. It briefly introduces a more advanced searching algorithm that you will learn more about in a later Explore Card.*

There is another way of searching an Array. If the elements in the Array are in sorted order, then we can use *binary search*. *Binary search* is where we repeatedly look at the middle element in the Array, and determine whether the element we're looking for must be to the left, or to the right. Each time we do this, we're able to halve the number of elements we still need to search, making *binary search* a lot faster than *linear search*!

The downside of *binary search* though is that it only works if the data is sorted. If we only need to perform a single search, then it's faster to just do a *linear search*, as it takes longer to sort than to *linear search*. If we're going to be performing a lot of searches, it is often worth sorting the data first so that we can use *binary search* for the repeated searches.

You can find out more about *binary search* on our *Binary Search Explore Card*. For *Arrays 101*, it is okay for you to use either *linear search* or *binary search*.

Hopefully, the *three basic Array operations* are clear now! Like always, there are a couple of problems for you to try for yourself now.

After that, we'll be having a look at *In-Place Array Operations*. What are those, you might be asking? Let's not get ahead of ourselves though—you'll find out soon!

### 1346. Check If N and Its Double Exist

Given an array *arr* of integers, check if there exists two integers *N* and *M* such that *N* is the double of *M* ( i.e. *N = 2 x M*).

More formally check if there exists two indices *i* and *j* such that:

* i != j
* 0 <= i, j < arr.length
* arr[i] == 2 * arr[j]

Example 1:

Input: arr = [10,2,5,3]

Output: true

Explanation: N = 10 is the double of M = 5,that is, 10 = 2 * 5.

Example 2:

Input: arr = [7,1,14,11]

Output: true

Explanation: N = 14 is the double of M = 7,that is, 14 = 2 * 7.

Example 3:

Input: arr = [3,1,7,11]

Output: false

Explanation: In this case does not exist N and M, such that N = 2 * M.

Constraints:

* 2 <= arr.length <= 500
* -10^3 <= arr[i] <= 10^3

### Answer 8


```javascript
/*
Background:

1. Some JavaScript methods return undefined, some return false, and some -1 on not found logic
2. As you go down different solutions, you will have more javascript than problem solving itself :) (or may be not)
3. Depending on if we have enough memory or not, we can choose one of the answers
    1. I would choose 1st solution Set
    2. Or, if someone says no more memory, then would choose the 4th solution, the simpler for (i) for (j) loop

Algo:

1. Finding if we have an element that is double or half is the question
2. That element should be not be same (which means element cannot be 0 because 0/2 = 0* 2 = 0)
3. For each element e, as we move to right of array:
    1. Check if its double or half exists in our cache (say Set/Map/Obj/Array/etc)
        If so, we found an different element ( i != j condition of question) so return true
    2. Now that we have seen this e, put in in the cache

*/

var checkIfExist = function(A) {
    let set = new Set();

    for (let e of A) {
        if (set.has(e * 2) || set.has(e / 2))
            return true;
        set.add(e);
    }

    return false
};
var checkIfExist = function(A) {
    let map = new Map();

    for (let e of A) {
        if (map.has(e * 2) || map.has(e / 2))
            return true;
        map.set(e, true);
    }

    return false
};
var checkIfExist = function(A) {
    let obj = {};

    for (let e of A) {
        if (obj[e * 2] || obj[e / 2])
            return true;
        obj[e] = true;
    }

    return false
};
var checkIfExist = function(A) {
    let n = A.length;

    for (let i = 0; i < n; i++)
        for (let j = 0; j < i; j++)
            if ((A[i] === A[j] * 2) || (A[i] === A[j] / 2))
                return true;

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    for (let e of A) {
        if (B.indexOf(e * 2) !== -1 || B.indexOf(e / 2) !== -1)
            return true;
        B.push(e)
    }

    return false
};
var checkIfExist = function(A) {
    let n = A.length;

    for (let i = 0; i < n; i++)
        if (
            ((A.indexOf(A[i] * 2) !== -1 && A.indexOf(A[i] * 2) !== i)) ||
            ((A.indexOf(A[i] / 2) !== -1 && A.indexOf(A[i] / 2) !== i))
        )
            return true;

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    for (let e of A) {
        if (B.includes((2 * e)) || B.includes(e / 2))
            return true;
        B.push(e)
    }

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    for (let e of A) {
        if (B.some((b) => b === e * 2) || B.some((b) => b === e / 2))
            return true;
        B.push(e)
    }

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    for (let e of A) {
        if (B.find((b) => b === e * 2) !== undefined || B.find((b) => b === e / 2) !== undefined)
            return true;
        B.push(e)
    }

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    for (let e of A) {
        if (B.filter((b) => b === e * 2)[0] !== undefined || B.filter((b) => b === e / 2)[0] !== undefined)
            return true;
        B.push(e)
    }

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    for (let e of A) {
        if (B.findIndex((b) => b === e * 2) !== -1 || B.findIndex((b) => b === e / 2) !== -1)
            return true;
        B.push(e)
    }

    return false
};
var checkIfExist = function(A) {
    let B = new Array();

    while (A.length) {
        if (B.includes((2 * A[0])) || B.includes(A[0] / 2))
            return true;
        B.push(A.shift())
    }

    return false
};
var checkIfExist = function(A) {
    let e;

    while ((e = A.shift()) !== undefined)
        if (A.includes((2 * e)) || A.includes(e / 2))
            return true;

    return false
};
var checkIfExist = function(A) {
    let e;

    while ((e = A.pop()) !== undefined)
        if (A.includes((2 * e)) || A.includes(e / 2))
            return true;

    return false
};

// Your input
[10,2,5,3]
//Output
true
// Expected
true
```
