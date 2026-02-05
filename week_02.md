# Week 02: 2/5/26

## Agenda

1. Homework review & share
2. Lecture: textures, textiles, screensavers
3. Break
4. Tutorial: Variables & movement
5. Assign presentation topics, next class overview (no class next week!)
6. (If time): work on practice assignment


---

## Homework Review

In groups of 3:

- Introduce yourselves
- Share your work & documentation. If there were any parts where you struggled, share those questions and see if your group can find an answer.
- Work together to answer to the following review questions:
  1. What function is called every frame? Which function is called only once?
  2. What is a parameter?
  3. Write down an example of a p5 function with more than one parameter.
- 10-15 minutes. We will come together as a class to briefly share everyone's work.

## Variables and Movement

### Coding Glossary

<!-- prettier-ignore -->
| Generic Definitions | |
|---|---|
| expression | a unit of code that resolves to a value, eg. `1 + 3`|
| operator | syntax for expression, eg. in the above expression the operator is `+` |
| variable | name for placeholder piece of data |
| declaration | uses the keyword `let`, gives a variable a value |
| assignment | gives a value to a variable name using `=`|
| scope | where variables exist. can be global or local inside `{}` |

#### Operators

There are many different types of operators - you can read [the full list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_operators). For generic JavaScript stuff, the MDN web docs linked there are a great place to start and get familiar.

The two most important types of operators (for now):

1. assignment, ie `=`
2. arithmetic, ie `+`, `-` (math)

#### Variables and Declaration

In order to "assign" or "make this word equal to a piece of data", we `declare` a variable. `let` is the keyword we use here to tell the code, "hey, the next word is going to represent some value".

```js
let myVariable;
```

##### `let` vs `var` vs `const`

We will almost always use `let` because it is the modern way of declaring variables in JavaScript. You shouldn't really be using `const` or `var`, and these are usually flags for getting code from elsewhere. If you're curious:

`let` is **block-scoped**: it can be **redefined** but not redeclared in the same block (generally, a "block" means anything between two `{}` curly brackets).
So:
```
let x = 1
let x = 2
```
Will **not** work, but you could reassign x's value like so:

```
let x=1
x=2
```

`var` allows redeclaration within scope - this is generally a bad idea and why most people don't use it anymore:
```
var x=1
var x=5 //will work, even though it's probably a bad idea
x=6 // will also work
```

`const` (short for **constant**) can never be redefined in the scope where it's been declared:
```
const x = 1
x=2 //will not work
```
#### Assignment Operator

Assignment happens when we give that named variable a value using the `=`.

```js
let teacher = "brent";
```

We can also modify assignments with arithmetic operators:
```
let teacher = "brent"
console.log(teacher + " rules") // should print "brent rules"

let one = 1
console.log(one + 1) // should print 2
```
#### Variable Types

JavaScript isn't specific about different variable types, but we do know when p5 accepts variables as parameters in functions it will be either a "Number" or "String".

- `Number` is like 1,2,3,4,5
- `String` is a word, but wrapped in `""`

#### Variable Names

When creating variable names, we can pretty much use whatever we want, but being specific helps us and readers of our code to understand what is happening.

There is one restriction: you cannot use words that already exist in p5. These are called `reserved words` and will often throw an error.
You might have seen red squiggly lines under some of your code, this means something is wrong.
![reserved](https://github.com/samheckle/code-toolkit-fa-25/blob/main/images/week_02/reserved.png)  
If we hover over the word, it will give us some information.  
![reserved_error](https://github.com/samheckle/code-toolkit-fa-25/blob/main/images/week_02/reserved_error.png)  
`'draw' has already been declared` means that we are either using the same variable name twice, or that we are infringing on a reserved word.

Typical naming convention in JavaScript is to use `camel case`, which just means the first letter of the first word is lowercase, and every word after that has uppercase. There should be no spaces in variable names.

```js
let mySuperCoolVariableThatUsesCamelCase = "nice";
```

### Tutorial: Animation

Everything following this tutorial is specific to p5, but doesn't necessarily require the glossary. But just so you know, everything mentioned in the tutorial is not generic.

We can animate in p5 using math and applying it to variables.
![movement](https://github.com/samheckle/code-toolkit-fa-25/blob/main/images/week_02/movement.gif)  
The ball is moving at a rate of 20 pixels to the _right_ **_every frame_**. Every frame means the `draw`. So we can calculate that the position is moving `+20` on the x-axis.
This position needs to change over time!
| frame number | x position|
|---|---|
| 1 | 20 |
| 2 | 40 |
| 3 | 60 |

But how can we make a number that with every frame needs to increase by 20?  
By using a variable and a combination of arithmetic and assignment operators.

1. We need to create a variable to store the first frame position.

```js
let x = 20;
```

This will represent the location of the circle for the first frame.

```js
circle(x, 20, 30);
```

2. In order to increment `x`, we need to increase the number...

```js
x + 20;
```

...but we also need to assign it to that new number. We are overriding the previous value of x with this new updated value.

```js
x = x + 20;
```

The shorter version of this is `+=`.
```js
x += 20
```

3. Any movement needs to happen in the `draw()`, because that is the animation loop.

```js
let x = 20;

function draw() {
  background(225);
  circle(x, 20, 30);
  x = x + 30;
}
```

The reason the declaration of the variable x (ie `let x = 20`) happens before the loop is because the loop will *reset* any valuables we declare inside it - every frame of the draw loop starts from scratch. So we need the variable to be `global`, or outside of both the `setup()` and the `draw()`. This gets into scope.

### Scope

Scope is where code can "see" variables. It is defined within different `{}` blocks. So the `setup()` has a scope that is different from the `draw()`. Global means that variables exist inside the entire file and are not limited by the `{}`. This allows us to change them inside the draw loop and have that change *persist* across frames.

### Randomness

[`random()` p5 reference](https://p5js.org/reference/p5/random/)
We can incorporate randomness into our sketches by using `random()`. For now, random can take 2 parameters:

```js
random([min], [max]);
```

These are numbers, with inclusive minimum and exclusive maximum, meaning it can randomly generate the minimum number but will never generate the maximum number or any numbers larger than that. If you don't pass in a number it will generate a long decimal between 0 and 1.

Random will give us floats (numbers with decimal points, like 1.234234) instead of integers (round numbers like 1), so if we want to use integers for something we can use `floor()` to round the number down.

```js
let randNumber = random();
randNumber = floor(randNumber);
```


### `push()` and `pop()`

A way to create layers so that our style choices for each shape don't impact others is to wrap our code inside of `push()` and `pop()` functions.

```js
fill("black");

push();
fill("white"); // because white is inside the push and pop, it doesn't impact any shapes outside of them
rect(10, 10, 30, 30); // left rectangle
pop();

rect(50, 10, 30, 30); // right rectangle
```

Will give us:  
![push](https://github.com/samheckle/code-toolkit-fa-25/blob/main/images/week_02/push.png)

## Demos

- 

## Review Videos

If you struggled with any of the material this week, please review these coding train videos!

- [2.1 - existing variables in p5](https://www.youtube.com/watch?v=7A5tKW9HGoM&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=8)
- [2.2 - custom variables in p5](https://www.youtube.com/watch?v=dRhXIIFp-ys&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=9)
- [2.3 - incrementation operators](https://www.youtube.com/watch?v=T26OJGjI8qI&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=10)
- [2.4 - `random()`](https://www.youtube.com/watch?v=POn4cZ0jL-o&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=11)
- [transformations part 1: `translate()`, `rotate()`, `push()`, and `pop()`](https://www.youtube.com/watch?v=o9sgjuh-CBM)
- [transformations part 2: `scale()`](https://www.youtube.com/watch?feature=shared&v=pkHZTWOoTLM)
- [transformations part 3](https://www.youtube.com/watch?v=IVMvq9rd8dA)

## Stuff From Lecture
- [Kente Cloth](https://en.wikipedia.org/wiki/Kente_cloth)
- [Jacquard machine](https://en.wikipedia.org/wiki/Jacquard_machine)
- [Girih Tiles](https://en.wikipedia.org/wiki/Girih)
- [Piet Mondrian](https://www.wikiart.org/en/piet-mondrian)
- [The Beginnings of Generative Art - A. Michaell Noll](https://ethw.org/First-Hand:The_Beginnings_of_Generative_Art)
- [Vera Molnar  - machine imaginaire](https://www.vam.ac.uk/blog/museum-life/vera-molnar-machine-imaginaire-the-dance-of-hands-and-machine-thinking)
- [All of Rafael Rozendaal's internet-based work](https://www.newrafael.com/internet)
- [Compendium Lecture, Casey Reas](https://gray.reas.com/compendium_lecture/)
- [Scrnsave](https://github.com/Masterjx9/ScrnSave)
- [Milkdrop](https://en.wikipedia.org/wiki/MilkDrop)

## Useful Misc Links
- [Piet Mondrian, The First Digital Artist](https://www.prospectmagazine.co.uk/culture/46436/piet-mondrian-the-first-digital-artist)
- [Algorithmic Pattern Catalogue](https://algorithmicpattern.org/)
- [Programmed at the Whitney](https://whitney.org/exhibitions/programmed)
- [Sleep mode](https://www.vice.com/en/article/celebrating-the-lost-art-of-the-screensaver/), [Exhibit page](https://nieuweinstituut.nl/en/projects/sleep-mode)