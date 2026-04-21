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

If we want *a bunch* of these, we end up copy-pasting the whole structure. And if we want to change how all pads work, we have to update every copy. Classes solve this by letting us define the shape **once**, then make as many as we need.

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

You can think of the constructor as a little setup routine for each instance. Anything you want every pad to have from the moment it exists - a property, an oscillator, a starting value - goes here.

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

Note: inside a class body, methods are *not* separated by commas. This is a common mistake when people are coming from the world of object literals.

---

## Inheritance

Sometimes you have several classes that share most of their behavior but differ in one or two specific ways. Rather than copy-pasting all the shared stuff, we can use **inheritance**: define a *base class* that holds the shared behavior, then make *subclasses* that only describe what's different.

```js
class Pad {
  constructor(name, color) {
    this.name = name
    this.color = color
  }

  draw() { /* shared drawing logic */ }

  play() { /* base behavior */ }
}

class SamplePad extends Pad {
  constructor(name, color, sample) {
    super(name, color)   // call the parent constructor first
    this.sample = sample
  }

  play() {
    super.play()         // call the parent's play()
    this.sample.play()   // then add our own behavior
  }
}
```

- **`extends`** means "this class is a kind of that class." A `SamplePad` *is a* `Pad`.
- **`super(...)`** inside a subclass constructor calls the parent's constructor. You have to call it before you can use `this`.
- **`super.method()`** calls the parent's version of a method — useful when you want to *extend* behavior, not replace it.
- **Overriding**: if a subclass defines a method that already exists on the parent, the subclass version wins. JavaScript always picks the most specific one.

### Polymorphism

Because `SamplePad` *is a* `Pad`, you can put both kinds into the same array and treat them the same way:

```js
for (let p of pads) {
	p.play()
}
```

The main sketch doesn't know (or care) which kind of pad it's dealing with — it just calls `.play()` and each instance does the right thing. This is called **polymorphism** and it's one of the main reasons OOP is powerful.

### `instanceof`

If you ever *do* need to check what kind of subclass something is:

```js
if (pads[i] instanceof SamplePad) {
  console.log("that was a sample!")
}
```

Most of the time you don't need to, you can just call the method and let the class figure it out. If you find yourself writing a lot of `instanceof` checks, that's usually a sign more behavior should move into the classes themselves.

---

## Things To Know

### Inheritance vs. Composition 

Inheritance is powerful, but it can get confusing fast. A good rule of thumb: use inheritance for **"is-a" relationships** (a `SamplePad` *is a* `Pad`). Use **composition** - storing other objects as properties - for **"has-a" relationships** (a `Pad` *has* an `Oscillator`).

A lot of beginner OOP code ends up with long inheritance chains that are impossible to follow. If you're not sure whether to inherit, default to composition.

### Avoid Overcomplicating Things

Classes are great when you have many things that share behavior and state. They're overkill when you just need a single object or a loose bag of data. Not every sketch needs classes! The moment to reach for a class is when you notice yourself duplicating structure, or when an object needs to track its own state and behavior over time.

The general rule for all the tricks we've learned so far is "DRY": Don't Repeat Yourself. If you're writing the same line or segment of code over and over again, think about ways you could make it into a function, object, or class - it makes your code more readable, easier to write, and less confusing. Comments are great, and you should use them as much as possible, but the best code is code that's so easy to understand it *doesn't need* comments.

### The Classes Were Already Inside The House

`"hello".toUpperCase()`, `[1,2,3].push(4)`, `mouseX.toFixed(2)` — these all work because strings, arrays, and numbers are all instances of built-in classes. JavaScript `class` syntax just gives you a clean way to define your own.

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

