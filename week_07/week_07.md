# Week 07: 3/19/26

## Agenda

1. Housekeeping - midterm, updates to extra credit list, participation grades
2. Presentations
3. Homework review
4. (if time): Generative Music & Making Music With Code
5. Tutorial: Data Structures & Sound

---
## Presentations

Write one question or thought on each presentation in the shared doc for the class [here](https://cryptpad.fr/doc/#/2/doc/edit/LASD2gb8lDZ2sIsRerFLmfuU/).

---

## Homework Review

In breakout rooms, share your projects and try to answer any questions you had! Write down your takeaways in the [class doc](https://cryptpad.fr/doc/#/2/doc/edit/LASD2gb8lDZ2sIsRerFLmfuU/). We will share in groups for ~15-20 minutes, then come together as a class and look through everyone's work.

---
## [Notes: Generative Music & Making Music With Code](<./Week_07 Lecture.md>)

---

## Tutorial: Data Structures & Sound

Make a copy of [this template sketch](https://editor.p5js.org/brondle/sketches/HheHy1CxA) for your in-class work - we'll be using a sound file that's saved in it.

### Using addons

The p5 editor includes p5 sound by default, but it's worth noting that it's not part of the core p5 library. If you check your sketch files, you can see it in `index.html` (this html file is where our JavaScript sketch actually *lives* and is displayed - we mostly don't need to think about it, but those `<script></script>` tags are where all the libraries we use are referenced).
![image-24](<../images/week_07/image-24.png>)

Since it's a separate library, we have to reference it in its own `<script></script>` tag (explained [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/script)). This will come in handy later in the class when we cover other addons - you can include pretty much any JavaScript library this way if you get deeper into JavaScript coding in the future.
### Coding Glossary

| term             | definition                                                               |
| ---------------- | ------------------------------------------------------------------------ |
| array of objects | an array where each element is an object — combines both structures      |
| method           | a function stored as a property of an object                             |
| `.pop()`         | removes and returns the last element of an array                         |
| `.splice(i, n)`  | removes `n` elements starting at index `i`                               |
| preload()        | a p5 function that runs before `setup()`, used to load external assets   |
| oscillator       | a signal generator that produces a repeating waveform at a set frequency |


**Arrays of objects:**
```js
let sounds = [
  { name: "kick",   color: "#e63946", freq: 80  },
  { name: "snare",  color: "#457b9d", freq: 300 },
  { name: "hi-hat", color: "#2a9d8f", freq: 800 }
]

// index-based loop
for (let i = 0; i < sounds.length; i++) {
  fill(sounds[i].color)
  rect(i * 120, 150, 100, 100)
}

// for...of (shorthand for index-based loop)
for (let sound of sounds) {
  console.log(sound.name)
}
```

**Object methods:**
```js
let greeter = {
  name: "Brent",
  sayHello: function() {
    console.log("Hello, I am " + this.name)
  }
}

greeter.sayHello() // "Hello, I am Brent"
```

`this` refers to the object the method belongs to. This is the key idea behind classes — next week we'll see a cleaner way to create many objects that share the same methods. As [this coding train fancam](https://www.youtube.com/watch?v=M5d7vygUPoQ) reminds us, never forget the `this dot` (original video [here](https://youtu.be/CKeyIbT3vXI?t=439&si=xrvdYfEKWZ07DLO9)).

**Modifying arrays:**
```js
let sounds = ["kick", "snare", "hi-hat"]

sounds.pop()             // removes *and returns* "hi-hat" — sounds is now ["kick", "snare"]
sounds.splice(0, 1)      // removes 1 element at index 0 — sounds is now ["snare"]
sounds.slice(1,2) // returns a "slice" of the array - in this case, ["snare", "hi-hat"]

```

**Oscillator basics:**
```js
let osc = new p5.Oscillator('sine') // 'sine' 'triangle' 'square' 'sawtooth'
osc.start()
osc.amp(0)        // start silent
osc.freq(440)     // frequency in Hz — 440 = concert A
osc.amp(0.5, 0.1) // ramp to 0.5 over 0.1 seconds
osc.amp(0, 0.3)   // fade out over 0.3 seconds
```

Here's a [simple example](https://editor.p5js.org/brondle/sketches/OkxjJgYDd) of an oscillator in action.

**loadSound in preload:**
```js
let drumSound

function preload() {
  drumSound = loadSound('kick.mp3')
}

function setup() {
  createCanvas(400, 400)
}

// later:
drumSound.play()
```

To upload audio files: ≡ menu (the arrow sign) → Sketch Files → "+" → Upload File.
![](<../images/week_07/image-25.png>)

---

### Challenge: Make Your Own Synth

These are roughly ordered from easier to harder - try to do at least two. You can also visit the [p5.sound reference](https://p5js.org/reference/p5.sound/) and implement something else from it if you find anything that interests you.

- Try adding your own sound files from [freesound.org](https://freesound.org/) or [sampleswap.org](https://sampleswap.org/) (or use your own sound files if you have them!)
- Add extra pad objects for a wider range of sounds.
- Add a visual pulse when a pad is active — change the rectangle's brightness or size
- Modify frequency in the draw loop. Some suggestions: base it on time, frameCount, or mouse position ([`osc.freq()`](https://p5js.org/reference/p5.sound/p5.Oscillator/#freq)). See the [example](https://editor.p5js.org/brondle/sketches/OkxjJgYDd) for reference.
- Add a `type` property to each pad object (`'sine'`, `'square'`, `'sawtooth'`, `'triangle'`) and pass it to the oscillator on creation — each pad will sound different — ([`p5.Oscillator`](https://p5js.org/reference/p5.sound/p5.Oscillator/))
- Make it generative: use `setInterval` or a frame counter to trigger pads automatically in a random or sequential pattern
- Try including one of [`osc.pan()`](https://p5js.org/reference/p5.sound/p5.Oscillator/#pan), [`p5.Reverb`](https://p5js.org/reference/p5.sound/p5.Reverb/), [`p5.Delay`](https://p5js.org/reference/p5.sound/p5.Delay/), or [`p5.Filter`](https://p5js.org/reference/p5.sound/p5.Filter/).
---

## Links
### Demo
- [In-class demo: simple synth](https://editor.p5js.org/brondle/sketches/p8x0zXApG)
### Review
-  [Coding Train 7.1 — What is an Array?](https://www.youtube.com/watch?v=VIQoUghHSxU)
- [Coding Train 7.2 — Arrays and Loops](https://www.youtube.com/watch?v=RXWO3mFuW-I)
- [Coding Train 7.3 — Arrays of Objects](https://youtu.be/fBqaA7zRO58?si=ZSNTxbtpKlpeK4Jz)
- [MDN Array Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [MDN Object Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [Coding Train 17.1 — Loading and Playing Sound](https://thecodingtrain.com/tracks/sound/sound/1-loading-playing)
- [Coding Train 17.8 — p5.Oscillator](https://thecodingtrain.com/tracks/sound/sound/8-oscillator)
### Useful/Misc 

**Sound:**
- [p5.sound library overview](https://p5js.org/reference/p5.sound/)
- [official p5 sound examples](https://editor.p5js.org/thomasjohnmartinez/collections/Dp0zGclVL) - *lots* of applications of p5.sound here
- [Tone.js](https://tonejs.github.io/) - more general-purpose alternative to p5 sound
- [Chrome music lab](https://musiclab.chromeexperiments.com/Experiments)

**Free audio samples:**
- [freesound.org](https://freesound.org/) — Creative Commons samples, free account required
- [sampleswap.org](https://sampleswap.org/) — no account needed

**Livecoding**
- [livecode.nyc](https://livecode.nyc/)
- [live coding tools](https://livecode.nyc/tools)