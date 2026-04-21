# Week 10 (Makeup): 4/21/26

## Agenda

1. Housekeeping
2. Recap: synth
3. Tutorial: Classes & OOP
4. Open Forum


---
For your sketch this week, make a copy of [this starter](https://editor.p5js.org/brondle/sketches/p8x0zXApG) 
## Coding Glossary

| term        | definition                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| class       | a blueprint for creating objects that share the same properties and methods                                              |
| instance    | a single object created from a class                                                                                     |
| `new`       | keyword that creates a new instance from a class                                                                         |
| constructor | a special function inside a class that runs automatically when a new instance is created                                 |
| `this`      | inside a class, refers to the specific instance the method/property belongs to                                           |
| method      | a function defined inside a class (same idea as object methods from last week)                                           |
| property    | a variable attached to an instance, usually set up in the constructor                                                    |
| OOP         | object-oriented programming: a way of designing programs focused on using objects and classes to "encapsulate" behavior. |

---

## From Objects to Classes

Here's a plain object, like we used building our synth last time:

```js
let pad = {
  name: "A",
  color: "#e63946",
  freq: 220,
  play: function() {
    console.log("playing " + this.name)
  }
}
```

If we want *a bunch* of these, we end up copy-pasting the whole shape every time. And if we want to change how all pads work, we have to update every copy. Classes solve this by letting us define the shape **once**, then stamp out as many as we need.

```js
class Pad {
  constructor(name, color, freq) {
    this.name = name
    this.color = color
    this.freq = freq
  }

  play() {
    console.log("playing " + this.name)
  }
}

let padA = new Pad("A", "#e63946", 220)
let padB = new Pad("B", "#457b9d", 330)

padA.play() // "playing A"
padB.play() // "playing B"
```

A few things to notice:
- Class names are **capitalized** by convention (`Pad`, not `pad`). JavaScript doesn't enforce this, but everyone does it — when you see a capital letter, expect a class.
- Nothing actually exists until you call `new Pad(...)`. The class is a *blueprint* — it isn't itself an object.
- `new` is the magic word. Without it, `Pad(...)` does nothing useful.

### The `constructor`

The `constructor` is a special function that runs **once**, automatically, when you say `new Pad(...)`. Its job is to take the arguments you pass in and attach them to the new instance using `this`.

```js
constructor(name, color, freq) {
  this.name = name   // "this" = the brand-new pad being born
  this.color = color
  this.freq = freq
}
```

You can think of the constructor as a little setup routine for each instance. Anything you want every pad to have from the moment it exists — a property, an oscillator, a starting value — goes here.

### `this` again

We previously encountered `this` with plain object methods. Same idea inside a class: `this` refers to the specific instance the code is running on. `padA.play()` — inside `play()`, `this` is `padA`. `padB.play()` — inside `play()`, `this` is `padB`. Each instance has its own `this`.

As always, never forget [the `this dot`](https://www.youtube.com/watch?v=M5d7vygUPoQ).

### Methods

Methods are functions defined inside the class. They get called on an instance with the `.` syntax — exactly like `array.push()` or `sound.play()`.

```js
class Pad {
  constructor(name) {
    this.name = name
  }

  greet() {
    console.log("hi, i am " + this.name)
  }
}

let p = new Pad("A")
p.greet() // "hi, i am A"
```

Note: inside a class body, methods are *not* separated by commas. This is a common bug when people are coming from the world of object literals.

---

## The classes were inside p5 all along

Every time you've written `new p5.Oscillator('sine')` or `new p5.Reverb()`, you've been calling a constructor. *Tons* of p5 objects are just class instances - OOP is a great programming paradigm and p5 uses it liberally.

---

## Links

### Demo


### Review
- [Coding Train 6.1 — Introduction to Object-Oriented Programming with ES6](https://www.youtube.com/watch?v=xG2Vbnv0wvg)
- [Coding Train 6.2 — Classes in JavaScript with ES6](https://www.youtube.com/watch?v=T-HGdc8L-7w)
- [Coding Train 6.3 — Constructor Arguments with Classes](https://www.youtube.com/watch?v=rHiSsgFRgx4)
- [Coding Train 7.4 — The Constructor Function in JavaScript](https://www.youtube.com/watch?v=F3GeM_KrGjI)
- [MDN: Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
- [MDN: `new` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)

