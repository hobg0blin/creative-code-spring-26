# Week 04: 2/26/26

## Agenda

1. Presentations: Alex & Pedro
2. Reading discussion, practice review
3. Demo: pen plotter
4. Tutorial: Repetition and Functions
5. On Code Order
6. [Demos, Videos, Useful Links](<#demos>)

---
**Note**: I got the class order mixed up so one of the requirements for the homework assignment - using a `for` loop - was incorrect, and I've changed it to using a **custom** function. 
## Practice & Reading Discussion

**Practice Review:**
- confusion about `=` versus `==`
- "juddering" on sides (Pedro's sketch)
- any other questions?

**Reading discussion:**

In your groups, share your discussion posts, and discuss the following questions:

- Do you think true randomness is possible? Or is randomness just what Desiree called "order operating beyond our comprehension"? If it doesn't, how does that change how you think about the artists you wrote about?
- Eli mentioned that randomness allows you to be a "consumer" of your own work, which lets you experience it anew. Do you agree? What do you think artists are giving up or gaining when they introduce chance in their work? 
- Conor argued that John Cage used randomness to remove personal taste and bias from his art. Do you think you can remove yourself from the work? Did any of the artists in the reading succeed in doing so?
- Jieying points out that pseudorandom is good enough for our purposes, but can introduce massive risks in contexts like cybersecurity. How much does the distinction between psuedorandom and "true random" matter to each of you? How do you decide when a method is random enough?

Generally: what do you disagree on or agree on as a group? What are you not sure about?
## Group Exercise: Plotter Exquisite Corpse 

 In your groups, draw a body together **without looking at each other's sketches**. Split the body into parts based how many people are in your group. So if your group is four people, you could do something like:
 
 - Person 1: Head
 - Person 2: Torso
 - Person 3: Legs
 - Person 4: Feet

 Each person's sketch should begin with a line that starts at `width/2, 0` and end with a line that ends at `width/2, height`. Include a `text()` function with your initials somewhere in the sketch. You'll have 20-30 minutes, then I'll smash them together and draw them all on my pen plotter.

Don't worry about color, and make sure to use noFill(), since this will be drawn on a pen plotter (so it'll just be lines and a single color). You'll have about 30 minutes.

This is an experiment, so I apologize in advance if something breaks.

**For the future:**

Taking this class entitles you to one (1) plotter drawing of your choice (nothing *too* weird, please). Until the class is over, you are welcome to send me an SVG at any point during the semester and have me plot it for you - you can pick it up from me on campus on Mondays, Tuesdays, and Wednesdays. It doesn't have to be a p5 sketch, either! If you want to convert an image to an SVG I recommend [using Inkscape](https://jennifermaker.com/how-to-make-an-svg-file-in-inkscape/).
****
## Repetition and Functions

### Coding Glossary: Review

<table>
<tbody>
<tr><td>function</td><td>

an instruction or command, may or may not have parameters. also known as `method`

</td></tr>
<tr><td>parameters</td><td>

values that are passed into the function inside the `()`. also known as `arguments`.

</td></tr>

<tr><td>declaration</td><td>

using the keyword `let`, names and creates a variable

</td></tr>
</tbody>
</table>

Declarations can also be used for functions, using the keyword `function`

Functions need to be written **_outside_** the `setup()` and the `draw()`

We have already seen an example of this:

```js
function setup() {
  createCanvas(400, 400);
}
function draw() {}
```

`setup()` and `draw()` are functions that use the function keyword. We have also seen:

```js
function mousePressed() {
  // do something when the mouse is clicked
}
```

### Custom Functions

So far, we have only used functions that are **predefined** by p5.js. Even though we are declaring and using `setup()`, `draw()`, and `mousePressed()`, they aren't something we are specifically defining. So, we can [create our own functions](https://p5js.org/reference/p5/function/) too. These still need to be written **_after_** the `draw()`

```js
function myCoolNewFunction() {}
```

We can also make custom parameters:

```js
function myCoolNewFunction(myCoolParameter) {
  print(myCoolParameter);
}
```

**Function uses**

You can create functions that just **do something:**
```js
function sayHello() {
	console.log('hello!')
}
```

But you can also use functions to **return a value.** This is useful for things like setting variables, or long/complex if conditions:
```js
function numPlusOne(num) {
	return num + 1
}
let x = 5
let y = numPlusOne(x) // y is now 6
```

```js
function containsName(myString, name) {
	return myString.includes(name)
}

let sentence = "Brent is a very cool guy"
let containsBrent = containsName(sentence, "Brent") // will return true
let containsDave = containsName(sentence, "Dave") // will return false
```
#### Coding Glossary: Custom Functions

<table>
<tbody>
<tr><td>declaration</td><td>

using the keyword `function`, names and creates a function

</td></tr>
<tr><td>call</td><td>

to use a function elsewhere in the code

</td></tr>
<tr><td>passing arguments</td><td>

a custom function accepting inputs in their headers, which creates a local placeholder for the data that is received

</td></tr>
</tbody>
</table>

#### Why make custom functions?

1. Code can be duplicated more easily.
2. It makes our code more readable and organized, just like variables.
   - If you notice you are writing the same piece of code over and over, it can probably be a function! In programming we call this **DRY**: Don't Repeat Yourself.
   - As a general rule of thumb: if the function is longer than the code it's replacing, it shouldn't be a function (so you don't need to write functions for stuff like incrementing variables). Otherwise, if you're writing that piece of code more than twice, you might want to make it a function.

![functions vs var](https://github.com/samheckle/code-toolkit-fa-25/raw/main/images/week_04/functionvar.png)

## On Code Order

There are a lot of ways to order code - because JavaScript uses [hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting), it's pretty forgiving of mistakes.  But it's still a best practice to stick to an order for readability and maintainability. This is the order we use for this class:

1. Global Variables
2. Setup
3. Draw
4. Event Functions
5. Helper Functions (or functions you write yourself)

---

## Demos

## Review Videos

If you struggled with any of the material this week, please review these coding train videos!

- [5.1 - function basics](https://thecodingtrain.com/tracks/code-programming-with-p5-js/code/5-functions/1-basics)
- [5.2 - parameters and arguments](https://thecodingtrain.com/tracks/code-programming-with-p5-js/code/5-functions/2-arguments)