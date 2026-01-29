#  1/29/26

![](<./images/week_01/intro.gif>)

*Source: [Casey Reas, 2010](https://reas.com/p18_s2/)*

---

## Agenda

1. Syllabus
2. Introductions
3. What's creative code?
4. Break
5. p5 basics 
6. Tutorial: Drawing with p5.js
7. Submit tutorial

---

## [Syllabus](https://github.com/hobg0blin/creative-code-spring-26)

General stuff:

* If I am ever going too fast through *any* material, please interrupt me! 
* This is my first time using Brightspace, so bear with me.
* You don't need permission to take a water break, go to the bathroom, etc. We'll usually take a ~20 minute break around the halfway mark.
* You can turn your camera off if you're eating/taking a break/whatever, just don't leave it off for extended periods of time.
* If you have specific accessibility needs that I'm not meeting, please reach out to me privately. I'm happy to work with you to make sure this class works for you.
* Questions? Comments? Needs? Email me! Open communication is greatly appreciated. If you have to miss class, expect to be late, or are struggling with an assignment, please let me know.


---

## Introductions

### me

| Brent Bailey (he/him)                                                                                                                                                                        |                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Software engineer & creative technologist                                                                                                                                                    | [bront.rodeo](https://www.bront.rodeo/)                                                                                    |
| currently: web dev & teaching @ hunter                                                                                                                                                       | previously: eyebeam, ITP, a whole lot of artist studios & startups                                                         |
| things you can ask me about: most kinds of code, software engineering, machine learning, the new media art industrial complex, portfolio review, resume review, grad school, games & gamedev | please ask me about these things in [office hours](https://calendly.com/brentlbailey/office-hours) - book by 5pm Wednesday |

### you

* Name, pronouns (optional), year, program
* What interests you? What do you spend your free time doing?
* What are you looking to get out of this class?
* What experience do you have with code? (This is not a trick question, knowing your experience levels as individuals and as a class will help tailor the direction the course takes)

---

## Introduction to p5
### Tutorial: Learning about the p5 Editor

Make an account: <https://editor.p5js.org/>

#### Looking at the p5 Editor

| Click the Gear Icon in the Upper left. |                                             |
| -------------------------------------- | ------------------------------------------- |
| These are my preferred settings.       | ![p5 settings](<./images/week_01/settings.png>) |

### Writing and Running Code

![p5.editor](<./images/week_01/p5_editor.png>)

### General Flow

| How to submit homework                                 |                                                          |
| ------------------------------------------------------ | -------------------------------------------------------- |
| 1. Rename sketch to enable saving                      | ![../../images/week_01/1.png](<./images/week_01/1.png>)] |
| 2. Save your sketch (you can also press ⌘+S or Ctrl+S) | ![](<./images/week_01/2.png>)                            |
| 3. Finish your assignment                              |                                                          |
| 4. Tidy your code                                      | ![](<./images/week_01/tidy.png>)                         |
| 5. Retrieve the URL and submit.                        | ![](<./images/week_01/url.png>)                          |

### Definitions: Coding Glossary vs. p5 Glossary

| coding glossary                                              | p5 glossary                                 |
| ------------------------------------------------------------ | ------------------------------------------- |
| terms that can be used *universally* when talking about code | terms that are specific to p5 and our class |

#### Coding Glossary

<details>
<summary> algorithm </summary>
series of steps to execute to solve a problem
</details>

<details>
<summary> syntax </summary>
grammars or punctuation of the language you code in
</details>

<details>
<summary> javascript </summary>

a programming language [^1]

</details>

<details>
<summary> p5.js </summary>

a javascript library[^2]

</details>

[^1]: the technical definition is a lightweight interpreted language with first-class functions
[^2]: it is **not** a programming language, but a way of interpreting plain javascript

<details>
<summary> documentation / reference </summary>

a dictionary for syntax of a particular coding language

</details>

<details>
<summary> comment </summary>

a way in code to write notes

</details>

``` js
    // this is a comment
    // we write comments in our code to explain what is going on and to organize ourselves
    /* this is also a comment
    but it
    can
    go
    on
    as
    many
    lines
    as
    you
    want
    (just remember to close it) */
```

<details open>
<summary>  function </summary>

an instruction or command, may or may not have ***parameters***, also known as ***methods***

</details>

``` js
    // the syntax of a function is the name followed by parenthesis 
    functionName()
```

<details open>
<summary>  parameter </summary>

value that is passed into the function, also known as ***argument***

</details>

``` js
    // parameters go inside the parenthesis
    functionName(parameterValue)
```

some p5 examples of functions with and without parameters

``` js
    // without parameters
    beginShape()

    // with parameters
    fill(255)
    background(255)
```

#### p5.js Glossary

<details>
<summary>  sketch </summary>

the name of the things you are making in p5.js web editor

</details>

`setup()`: happens before the animation loop and *executes one time*. once it completes, it moves to the next line in the code.

![setup gif](<./images/week_01/setup.gif>)

`draw()`: is the animation loop, executes with framerate

![draw gif](<./images/week_01/draw_loop.gif>)

<details open>
<summary>  canvas </summary>

the area on the screen where the code is executed, similar to an artboard. uses the cartesian coordinate system (x, y).

</details>

![coordinates](<./images/week_01/coordinates.png>)

Important to note here is the blue line represents the x-axis, increasing from left to right. The red line represents the y-axis, increasing from top to bottom.

`(0, 0)` starts from the top left corner and increases until the `width` and `height` have been reached. The width and height are determined by the parameters passed in to the `createCanvas()` function located in setup.

#### p5 Functions covered in class

[rect()](https://p5js.org/reference/p5/rect/)
```
// remember any parameter wrapped in [] is optional
// x: x position, from top left corner (unless otherwise specified)
// y: y position, from top left corner (unless otherwise specified)
// w: width of rectangle, in pixels
// h: height of rectangle, in pixels
// optional rounding of edges using radius in px from top left, top right, bottom right, bottom left
rect(x, y, w, [h], [tl], [tr], [br], [bl])
```
[fill()](https://p5js.org/reference/p5/fill/)
```js
// r, g, b values with optional alpha
// from 0 - 255
fill(v1, v2, v3, [alpha])
// color names, wrapped in quotations
// fun tool to see all the color names: https://tools-olive.vercel.app/t/css-named-colors
fill('color name')
// greyscale, with optional alpha
// from 0 - 255
fill(gray, [alpha])
```
We also covered `circle()`, `ellipse()`, `line()`, `stroke()`, `noStroke()`

Options for your assignment next week:
* Look at any additional shapes in [2D primitives](https://p5js.org/reference/#2D%20Primitives), such as arc, quad, triangle
  
Challenge:
* Experiment with [curves](https://p5js.org/reference/#Curves) and [vertices](https://p5js.org/reference/#Vertex)

---

## Demos
## Review Videos

If you struggled with any of the material this week, please review these coding train videos.

- [1.1 - p5.js](https://www.youtube.com/watch?v=yPWkPOfnGsw&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=2)
- [1.2 - web editor](https://www.youtube.com/watch?v=MXs1cOlidWs&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=3)
- [1.3 - shapes](https://www.youtube.com/watch?v=c3TeLi6Ns1E&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=4)
- [1.4 - color](https://www.youtube.com/watch?v=riiJTF5-N7c&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=5)
- [1.5 - errors](https://www.youtube.com/watch?v=LuGsp5KeJMM&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=6)
- [1.6 - comments](https://www.youtube.com/watch?v=xJcrPJuem5Q&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=7)

## Useful Misc Links
* [curve visualization](https://editor.p5js.org/samheckle/full/VIr36n9gq)
* [p5 examples](https://p5js.org/examples/)
* [p5 community](https://p5js.org/community/)
* [p5 showcase, 2022](https://showcase.p5js.org/#/2022-All)
---

