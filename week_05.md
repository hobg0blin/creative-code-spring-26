# **3/5/2026**

Agenda:
1. Housekeeping
	 - Link to your sources! If you used ChatGPT/Gemini/whatever link to the chat!
	 - I was foiled once again by Brightspace and accidentally made the homework an assignment instead of a discussion post. I will move everything over to a discussion forum tomorrow so you can see each other's work.
	 - Guide to careers in the arts session tomorrow on Zoom from 2:30-3:30, RSVP [here](https://urldefense.com/v3/__https://huntercuny.joinhandshake.com/stu/events/1911182__;!!LAh5qUgpm5Y!BuztmxX_Mtu-xnCLBQ3WaAxOiOsE34046hEd97bWpwr8F7tEwR6pf9pg4LQUdGUyUEevhzSwOtKXOLf0U74JMuPUrtKj605IV6ML_-rsHAcEug$)
	 - Practice assignment due next week (3/11)
	 - Homework #4 due 3/18 (much less homework from here on out!)
	 - Extra credit is up! Feel free to look for other things that meet the criteria & I'll be updating it as I come across events.
2. Presentations (Elijah and Desiree)
3. Homework discussion
4. Demo: recursion
5. Tutorial: repetition & loops

---
## Homework Discussion

In breakout rooms, share your projects, walk through your process and final outcomes, and try to answer any questions you might have had issues with! We will share in groups for ~10-15 minutes, then come together as a class and look through everyone's work.

---
## Demo: Recursion
![](<./images/image-11 1.png>)
*Print Gallery*, MC Escher

> **Recursion = a function that calls itself.**

One interesting facet of programming languages is that they allow for recursion: functions can call themselves. The basic elements of recursion:

1. Base case: a condition where the function terminates. If you don't have a base case, your function will run infinitely, which will usually cause your code to crash.
2. Recursive case: a condition where the function should call itself.

A [very simple example in p5](https://editor.p5js.org/brondle/sketches/jn4E676U-):


![](<./images/image-11.png>)

Gives us:

![](<./images/image-12.png>)

Worth noting: recursive functions "bubble up": the code doesn't run until the last function is called after the base case. So, you can't really tell in the sketch, but the smallest circle is actually the one getting drawn first. For a more thorough explanation of this process, see the [call stack](https://medium.com/@marc.herman.rodriguez/recursion-and-the-call-stack-93666f923226).

We can't *actually* compute infinity, but recursion allows us to create the illusion of doing so.

Recursion is extremely useful in solving certain computational problems, but it also has neat artistic applications! Visually, we can think of Russian Nesting Dolls or the "endless mirror" effect of two mirrors facing each other. Recursion allows us to recreate these effects.


![](<./images/image-6.png>)

[**Droste Effect:**](https://en.wikipedia.org/wiki/Droste_effect): an image that contains itself, that then contains itself, that then contains itself, and so on. Named for the cocoa tin above.

![Sierpinski Gasket](<./images/Fractal_tree.gif>)

Fractals: infinitely complex self-repeating patterns. Mandelbrot set, fractal trees, and many, many, more. Fractals contain patterns at *every zoom level*.

**Examples**

![](<./images/image-13.png>)
The Alhambra ceiling.

![](<./images/image-14.png>)
African indigenous fractal architecture (Ron Eglash)

Cyriak Harris - [whatever this is](https://www.youtube.com/watch?v=GAvS1ndtEKg), [hand fractals](https://mathcraft.wonderhowto.com/news/cyriak-harris-fractal-freakiness-0131000/)
### Exercise: Recursion

Spend a few minutes trying out a couple of the tools below (no need to try all of them). Then, pick one and try making something. Once you've settled on a final output, title it and share it in the chat.
1. [Droste Spiral Maker]([https://javier.xyz/droste-creator](https://droste-spiral.samolevsky.com/))
2. [Fractal Tree Maker in p5](https://editor.p5js.org/brondle/full/gXTuPxt8a) - be warned, this can slow down at high levels of depth. You can also tweak the code if you want [here](**https://editor.p5js.org/brondle/sketches/gXTuPxt8a**)
3. [Mandelbrot creator](https://www.zazow.com/mandelbrot/create.php)
4. [Nico's Fractal Machine](https://sciencevsmagic.net/fractal/#0060,0090,1,1,0,0,1)
5. [UsefulJS Fractal builder](http://usefuljs.net/fractals/) - click and drag over a section of the canvas to zoom in. Not super intuitive.
6. [Fractal Lab](https://hirnsohle.de/test/fractalLab/) - this is *not* beginner-friendly, but you can play around with the examples in *Fractal Library* if you want a challenge.
link fixed???
## Tutorial: Repetition and Loops

### Review

Begin by making a new sketch titled "In-Class 5.1".

- Create 5 columns
- With an if-statement, make a single column turn red when you hover over it (you should use `mouseX` and `mouseY` for this). Each column should _not_ have a fill until they are hovered. They can either have `noFill()` or a fill of white.

### Identifying Patterns

With your sketch you just made, what pattern are we seeing? How can we mathematically relate each rectangle with one another?

### Coding Glossary: Loops

<table>
<tbody>
<tr><td>loop</td><td>

code that repeats the content inside `{}`. the `draw()` is a loop that already exists for us.

</td></tr>
</tbody>
</table>

### While Loop

A `while()` loop is very similar to an `if()` statement. They follow similar syntax that use `()` and `{}`.

When we build out an `if()` statement, we put the conditional expression inside the `()` and the code that is locked in the `{}`. A `while()` loop is the same.

```js
while(conditional expression){
    // loop something
}
```

But, there are some extra steps in order to get the loop functional.

<h1>

It is super important at this point to make sure you do not have `Auto Refresh` checked in your p5 editor.

 </h1>

1. The first thing we want is to declare a number that will control the loop and determine _when the loop stops_. This is just a normal variable.

```js
let iterator = 0;
```

2. Next, we determine how many times our loop wants to execute using our new variable and a conditional expression. Once this conditional becomes `false`, the loop stops.

```js
iterator < 10;
```

This means our loop will iterate 9 times, starting at 0. This conditional is what goes inside the `()` of our `while()`

```js
while (iterator < 10) {}
```

3. We need to change our variable inside our loop, meaning inside the `{}`. This is just like a variable changing in the draw, where it increments once it hits the bottom (or wherever the variable is located).

```js
while (iterator < 10) {
	iterator += 1;
}
```

Our final code for our loop will look something like:
![loop](https://raw.githubusercontent.com/samheckle/code-toolkit-fa-25/main/images/week_04/loop.gif)

### For Loop

A `for()` loop is a shorthand way of writing a `while()` loop. Instead of having 3 separate lines of code (declaring iterator, writing conditional, incrementing iterator), we do it all inside the `()` of the `for()`, all separated by a `;`.

To write

```js
let iterator = 0;
while (iterator < 10) {
	iterator += 1;
}
```

As a `for()` loop, we combine all these lines into one.

```js
for (let iterator = 0; iterator < 10; iterator += 1) {
	// do something 10 times
}
```

---

## Demos

## Review Videos

- [4.1: While and For Loops](https://www.youtube.com/watch?v=cnRD9o6odjk)
- [4.2: Nested Loops](https://www.youtube.com/watch?v=1c1_TMdf8b8)

## Useful/Misc Links

- [Droste Effect in p5](https://editor.p5js.org/isohedral/sketches/iNUAHFZLM)
-  [Coding Train — Fractal Trees (Recursive)](https://thecodingtrain.com/challenges/14-fractal-trees-recursive/) 
- [p5.js official example fractal tree example](https://p5js.org/examples/repetition-recursive-tree/)