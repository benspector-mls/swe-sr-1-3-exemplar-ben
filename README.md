# swe-sr-1-3

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Question 1

Read the [findIndex documentation on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex). When would you want to use `findIndex` instead of `indexOf`? Include an example to enhance your response.

### Response 1

Both `findIndex` and `indexOf` look through an array for a value and return the index of that value if it is found, or `-1` if no such value exists. 

The difference is that `indexOf` takes in a value to find and returns the index of the first value that is equal to that value. `findIndex` on the other hand takes in a callback, invokes that callback on each value in the array, and returns the index of the first value for which the callback returns `true`. In other words, it returns the first value that satisfies the callback's condition.

For example:

```js
const nums = [1, 1, 2, 3, 5, 8, 13, 21];

// find the index of the value in the array that equals 5
console.log(nums.indexOf(5)); // prints 4

// find the index of the first number that is greater than 10
console.log(nums.findIndex((num) => num > 10); // prints 6
```

## Question 2

The callback that you provide to `forEach`, `filter`, or `map` can include up to three parameters. 

```js
const arr = ['a', 'b', 'c', 'd'];

arr.forEach((param1, param2, param2) => {

});
```

What values will be provided to those three parameters? To support your response, provide an example of how you might use all three parameters to do something.

### Response 2

The three parameters will receive the following values:
1. `element` - The current element being processed in the array.
2. `index` — The index of the current element being processed in the array.
3. `array` — The array the higher order method was called upon.

For example, you could use those three parameters like so: 

```js
const friends = ['ben', 'carmen', 'itzel', 'zo', 'gonzalo'];

friends.forEach((element, index, array) => {
  console.log(`${element} is friend number ${index + 1} out of ${array.length}`);
});

/* Output:
"ben is friend number 1 out of 5"
"carmen is friend number 2 out of 5"
"itzel is friend number 3 out of 5"
"zo is friend number 4 out of 5"
"gonzalo is friend number 5 out of 5"
*/
```

## Question 3

According to our [style guide](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/cheatsheets/style-guide#iterators-and-generators) (adopted from AirBnb), it is recommended that you only use array higher-order functions like `forEach` instead of `for` loops.

What do you see as the benefit of doing this?

### Response 3

The main benefit is the readability of your code. Higher-order functions hide away the technical details of iterating making the code easier to read. They also reduce the chances of making mistakes such as starting at the wrong index or creating an infinite loop.

```js
const friends = ['ben', 'carmen', 'itzel', 'zo', 'gonzalo'];

// Traditional for loop
for (let i = 0; i < friends.length; i++) {
  console.log(friends[i]);
}

// Using forEach
friends.forEach(friend => console.log(friend));
```

## Question 4

Below is a regular expression. What kinds of strings does it identify? Explain each portion of it.

```
/^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/
```

Tip: Visit https://regexr.com/ to learn Regex and to help understand regular expressions.

### Response 4

This regular expression can be used to identify email addresses! Here's how it works:
* `^[a-zA-Z0-9._-]+@` — this portion checks to see that the email starts with one or more letters, numbers, periods, underscores, or dashes followed by the `@` symbol.
* `[a-zA-Z0-9.-]+` — this portion looks for the "domain" part of the email (`"gmail"`, `"hotmail"`, `"yahoo"`, etc...) by looking for one or more letters numbers, periods, or dashes
* `\.[a-zA-Z]{2,4}$` — this portion checks to see that the email ends with a period followed by 2-4 letters. This is the `".com"` or `".edu"` portion of the email.

## Question 5
Imagine you are teaching a brand new programmer a brief lesson about callback functions. Your lesson should have the following components:
* An explanation of the concept with an analogy ("A callback function is a ... It is like a ...")
* An example of the syntax for a higher order function that accepts a callback.
* An explanation of the syntax using the terms **callback**, **higher order function**

Below, we've provided an outline for your response but feel free to modify it as you see fit.

### Response 5

A **callback** function is a function provided to and invoked by another function. The function using the callback function is called a **higher-order** function. It is like a recipe prepared by a chef. The recipe is the function to make a meal and the chef is the function that executes that recipe. 

A really popular higher-order function that accepts a callback function is the `forEach` method of arrays.

```js
let sum = 0;
const addToSum = (number) => {
  sum += number;
}

const nums = [1, 2, 3];
nums.forEach(addToSum);
```

In this example, the `forEach` method used on the last line is a higher-order function that accepts the callback `addToSum`. The `forEach` method invokes the given callback function on every value in the array. The result is that each number is added to the `sum`, giving us a total of `6` at the end of the program.
