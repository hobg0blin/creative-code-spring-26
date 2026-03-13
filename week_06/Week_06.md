## Agenda

1. Housekeeping: midterm assignment, class forum
2. Presentations: Angel & Xiaomen
3. Check-in: any questions about the practice, or in general?
4. Lecture - Bots & Generative Text
5. Exercise: make your own bot
6. Tutorial: Arrays & Data Structures

## [Lecture: Generative Text](<./Week 6 Lecture Notes.md>)

## [Exercise - Make Your Own Bot](<./Exercise - Make Your Own Bot.md>)

## Tutorial: Data Structures I

### Coding Glossary: Arrays

| Review | | 
|---|---|
| variable | name for a placeholder piece of data |
| declaration | using `let` to assign a value to a variable or using `function` to create a new function | 
| variable types | `boolean`, `number`, `string` (words) |

| New terms | | 
|---|---|
| array | data structure that holds a *series* of variables, uses `[]`, order matters| 
| element | one piece of array data |
| index | location of a particular element, starting at index of 0 |

#### Declaring an ***Array***
```js
let myNewArray = []
```

#### Initializing an array with ***Elements***
```js
let myNewArray = [10, 15, 20]
```
#### Retrieving a specific ***Element*** with the ***Index***
The index is the location of the data we want to grab. The location is automatically assigned because of the `array`, since it is a *series* of data, so it always starts at 0 and increases by one for every element. When we want to retrieve a specific element, we use `[]` and the index (location) we want to grab.

```js
myNewArray[0] // 10
myNewArray[1] // 15
myNewArray[2] // 20
```
#### Arrays are like tables

<table>
<tbody>
<tr><td>index</td><td>0</td><td>1</td><td>2</td><td>3</td></tr>
<tr><td>value</td><td>"this"</td><td>"is"</td><td>"a"</td><td>"sentence"</td></tr>
</tbody>
</table>

```js
let data = ["this", "is", "a", "sentence"]
```

In code, we typically only want an array to hold 1 type of data. So it should be *either* a list of numbers, booleans, or strings.

#### Arrays are Living Variables
We can change the value of an element in the array by reassigning it, like we do with normal variables.

```js
let teachers = ["Brent", "Patrick", "Rory"]
teachers[1] = "Brent" 
// override the old value, reassign to new
// teachers is  ["Brent", "Brent", "Rory"]
```
If we use an index (location), that does not exist yet, it will add empty `undefined` items in the series until it gets to that location.
```js
let animals = ["Cat", "Dog"] // animals has elements at 0 and 1
animals[4] = "Giraffe"
// animals is now ["Cat", "Dog", undefined, undefined, "Giraffe"]
```
This isn't the best way to add to an array, because we don't want to accidentally create empty variables.

---

#### Unique Attributes of an Array
JavaScript is an object-oriented programming language, so whenever we create a piece of data (like a variable or an array), it is considered an `object`.

`Objects` allow us to enact specific actions *on* them. We need to reference the specific object in order to do that action.

##### `.push()`

`push()` is a function we have seen inside of p5, but [`.push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) is a function that exists in an array. We need to use the name of our array, and the `.` to use the specific function.

```js
let myArray = [2, 4, 6]
myArray.push(8)
// this automatically adds 8 to the end of the array
// the new array is [2, 4, 6, 8]
```
This adds an element to the end of the array.

**Note**: This is different from p5's `push()` method. p5 has redefined `push()`/`pop()` to store states. `.push()` has different syntax and *must* be used *on* an array. So anytime we see the prepending `.`, it likely means it needs to be used on an object.

##### properties
Properties are variables that are unique to an object (in this instance an array). We again use the `.` to reference a specific property we want to access. 

Arrays have a property called [`length`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length). This gives us how many items exist in the array.
```js
let myArray = [2, 4, 6] // 3 items total
myArray.length // this is 3
```
This counts the number of ***elements*** that exist inside the array.

##### Arrays and Loops

Typically it is very cumbersome to access every element inside of a loop every time. Given an array:

```js
let pets = ["dog", "cat", "hamster", "giraffe", "horse"]
```

If we want to use or reference any one of these we would need to do something like:

```js
print(pets[0]) // prints: dog
print(pets[1]) // prints: cat
print(pets[2]) // prints: hamster
print(pets[3]) // prints: giraffe
print(pets[4]) // prints: horse
```

But, we already see a pattern of a number increasing every time. So, using the attributes we know so far, we can go through the loop. We already know our end condition, because it is the number of elements in our loop. So we could write:

```js
for(let count = 0; count < 5; count++){
    print(pets[count])
}
```

But, our end condition might be malleable, or we might add another pet later on. So we can use the property `.length` instead of 5.

```js
for(let count = 0; count < pets.length; count++){
    print(pets[count])
}
```

If we wanted to make it clearer, we could declare a local variable:

```js
for(let count = 0; count < pets.length; count++){
    let currentPet = pets[count]
    print(currentPet)
}
```

There is a shorthand for this! If we don't need to know the number, we can automatically create and assign `currentPet`:

```js
for(let currentPet of pets){
    print(currentPet)
}
```

This is a special loop *just for arrays*, that is shorthand for assigning a variable to the index of the current iteration.

## Data Structures Part 2: Objects

An object is a data structure similar to an array.

<table>
<tbody>
<tr><td>object</td><td>

data structure that holds variables using key-value pairs. it is unordered.

</td></tr>
<tr><td>key</td><td>

the `property` we access when we want to retrieve a piece of data from the object.

</td></tr>
<tr><td>value</td><td>

similar to the `element` in an array, the data that is stored

</td></tr>
</tbody>
</table>

#### Objects are also like tables

<table>
<tbody>
<tr><td>property</td><td>word1</td><td>word2</td><td>word3</td><td>word4</td></tr>
<tr><td>value</td><td>"this"</td><td>"is"</td><td>"a"</td><td>"sentence"</td></tr>
</tbody>
</table>

```js
let data = {
    word1: "this",
    word2: "is", 
    word3: "a",
    word4: "sentence"
}
```

#### Unique Attributes of an Object

We can add new `properties` by simply using a new property name. 

```js
let myObj = {
    a: 10,
    b: 15
}
myObj.c = 20
// this automatically adds .c as an accessible property
// the new object is {a:10, b:15, c:20}
```

---

## Review Videos
* [7.1 What is an array?](https://www.youtube.com/watch?v=VIQoUghHSxU)
* [7.2 Arrays and loops](https://www.youtube.com/watch?v=RXWO3mFuW-I)
* [7.3 Arrays of Objects](https://youtu.be/fBqaA7zRO58?si=ZSNTxbtpKlpeK4Jz)

## Review Documentation (these are textbook definitions)
* [for...of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of) loops with arrays
* [array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
* [object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

## Demos

- [In-class demo](https://editor.p5js.org/brondle/sketches/S969dWhz2)

## Useful/Misc Links
- [Gutenberg, Dammit!](https://github.com/aparrish/gutenberg-poetry-corpus](https://github.com/aparrish/gutenberg-dammit)
- [Markov Chains in p5](https://editor.p5js.org/codingtrain/sketches/Y6SvoMcyH)
- [Tracery](https://tracery.io/)
