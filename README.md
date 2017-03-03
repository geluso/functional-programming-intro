# Intro to Functional Programming

## Learning Objectives
* Define functional programming
* Side effects
* Pure functions
* Higher Order functions

Functional programming is a style of programming that treats programs
like mathematical functions. Mathematical functions, like addition,
subtraction, multiplication, or the area of a region are all strictly
defined. Adding 3 to 8 always equals 11. Functional programming strives
to make programs behave consistently like mathematical functions by
writing **pure functions** that eliminate **side effects**.

A **pure function** is a function that always produces the same output
when given the same input.

Have you ever written a program that sometimes behaves one way, then sometimes
behaves another way? You've written an impure function with **side effects**.
A **side effect** is something about the state of your program that's changed
by the program running. Functional programming hates side effects because
side effects ruin **pure functions**. Remember, the whole point of functional
programming is to treat programs like mathematical functions that always return
the same output when given the same output.

Here's an example of an arbitrary function called `foo` that would be considered
impure because it returns two different values for the same input:

```js
foo(3) // returns 5
foo(3) // returns 92
```

OK, `foo` is an arbitrary, general example. Now look at this one. How angry
does it make you that a function called `add` returns different values when it's
given identical input?

```js
add(3,2) // returns 5
add(3,2) // returns 92
```

Functional programming takes an extreme stance and says *all* functions should
be **pure** and without **side effects** because functional programmers are
tired of fighting against bugs where their program behaves inconsistently.
Functional programmers realize that if they can use programming techniques that
enforce function purity and eliminate side effects that their programs will be
much, much more reliable.

## Functional Programming Techniques
Now we know that the whole point of functional programming is to strive to
make our programs behave more like pure mathematical functions where the same
input is guaranteed to produce the same output without side effects.

We'll soon see how [Redux](http://redux.js.org/) applies these ideas from
functional programming to help developers create more pure applications that 
eliminate side effects and perform consistently, and become much easier to
test too!

So, so far these functionall programming techniques are all abstract and
we haven't seen any concrete examples about how to reduce side effects
and write pure functions. Let's get to it!

First, let's take a look at higher order functions.

## Higher Order Functions
JavaScript is an especially fun and powerful lanaguage because it supports
**higher order** functions. "Higher order" means functions can be created while
the program is running, functions can be stored in variables, and functions can
be returned from other functions. In other words, functions are treated just
like numbers, strings, arrays, and all other objects in the language. Not all
programming languages support **higher order** functions, and not all languages
make these types of functions as easy to use as JavaScript does. Let's take a
look at what **higher order** functions allow us to do.

Here are the properties of **higher order** functions:

* functions can be stored in variables
* functions can be passed to functions as parameters
* functions can be created while the program is running
* functions can be returned from functions

## Passing Functions to Functions
```js
function happyBirthday() {
  console.log("Happy birthday to you!");
}

function happyBirthdaySteve(name) {
  console.log("Happy birthday Steve Jobs!!");
}
```

```js
var song = [happyBirthday, happyBirthday, happyBirthdaySteve, happyBirthday];
doAll(song);
```

```js
function doAll(arrayOfFunctions) {
  for (var i = 0; i < arrayOfFunctions.length; i++) {
    // get the function out of the array and save it to a variable
    var oneFunction = arrayOfFunctions[i];

    // execute the function!
    oneFunction();
  }
}
```

Output:

```
Happy birthday to you!
Happy birthday to you!
Happy birthday Steve Jobs!!
Happy birthday to you!
```

## Common High Order Functions
Saving functions into variables, and passing functions as parameters, and
returning functions from functions open a whole new world of **functional
programming** techniques. **Higher order** functions allow us to encapsulate
functionality that we write over and over again into new functions that allow
us to perform complex tasks easily.

Here's the four most common higher order functions:

### forEach
`forEach()` is a function that accepts an array and another function. The
`forEach()` function iterates through the array and applies the other function
to each thing in the array.

```js
// forEach accepts an array, and another function as a parameter
function forEach(array, func) {
  // iterate over the array, just like normal
  for (var i = 0; i < array.length; i++) {
    // get each item out of the array
    var item = array[i];
    // pass each item to the higher order function and have it
    // execute itself accepting each item as a parameter.
    func(item);
  }
}
```

We can use the `forEach()` function to pass in an anonymous function that's
defined when the program runs:

```js
var names = ["Sam", "Beth", "Carol"];
forEach(names, function(name) {
  console.log("Hello" + name + "!");  
});
```

Or, we can even pass in the name of the `greet` function and the `forEach`
function will use it's name as a reference and still be able to pass the
function as a parameter and execute it later.

```js
var names = ["Sam", "Beth", "Carol"];
function greet(name) {
  console.log("Hello" + name + "!");  
});

forEach(names, greet);
```

Output:

```
Hello Sam!
Hello Beth!
Hello Carol!
```

## map
TODO: finish writing map example upon contract negotiation

## filter
TODO: finish writing filter example upon contract negotiation

## reduce
TODO: finish writing map example upon contract negotiation
