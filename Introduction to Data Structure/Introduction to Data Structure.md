# Introduction to Data Structure

## Arrays 101

### Overview (Introduction)

Arrays are a simple data structure for storing lots of similar items. They exist in all programming languages, and are used as the basis for most other data structures. On their own, Arrays can be used to solve many interesting problems. Arrays come up very often in interview problems, and so being a guru with them is a must!

In this Explore Card, we'll introduce Arrays and solve some cool problems with them. This Card is beginner friendly, and we've provided lots of code snippets in Java to help you understand. Each topic begins with informative articles, followed by real interview problems for you to practice on.

In addition, the problems have hints which will help you in building up ideas on how to solve them. These hints will be subtle enough to set you on a particular path for reaching the optimized solution, without giving away the answer too easily.

After completing this Explore Card on Arrays, you will understand:

* What an Array is.
* Basic properties of Arrays.
* Implementing basic Array operations.
* Simple programming techniques with Arrays.

### Introduction

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

### Max Consecutive Ones

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

### Find Numbers with Even Number of Digits

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

### Squares of a Sorted Array

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

## Inserting Items Into an Array

In the previous chapter, we looked at what Arrays are, and the basic programming constructs of Arrays in Java. We're now going to use these basic constructs to implement three key operations for Arrays:

* Inserting items.
* Removing items.
* Searching for items.

These three operations are the fundamental operations for all data structures.

In this chapter, we'll be starting with **inserting items into an array**. Like before, we'll approach the learning with lots of examples and programming snippets. After that, there are some more interview questions for you to practice on. We hope you have fun!

### Basic Array Operations

Now that we have a fairly good understanding of what an Array actually is, and how it is stored inside the computer's physical memory, the next important thing to look at is all the operations that Arrays support. An Array is a data structure, which means that it stores data in a specific format and supports certain operations on the data it stores. Consider the DVD inventory management software from the introduction section. Let's look at some operations you might want to perform using this software:

* **Insert** a new DVD into the collection at a specific location.
* **Delete** a DVD from the existing collection if it doesn't make sense to keep it in the inventory anymore.
* **Search** for a particular DVD in the collection. This is one of the most commonly executed operation on our collection, because our inventory management software would be used hundreds of times a day to look for a particular DVD asked for by the user.

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
