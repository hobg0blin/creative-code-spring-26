# Week 12: 4/30/26 - Data and its Discontents

## Agenda

1. Housekeeping
2. Presentations 7
3. Lecture/tutorial: Data art, APIs and datasets in p5
4. Exercise: personal dataset

---

## Housekeeping

- Final project: option 2 proposals due **today** (4/30) by email - sign-off needed.

---

## Presentations

You know the drill by now! Add your feedback to the [class doc](https://cryptpad.fr/doc/#/2/doc/edit/DNEhyy68JqoUKqIDtyV5YZG3/).

---

## Tutorial: Loading data in p5

First, review the [NYC Squirrel Census](https://data.cityofnewyork.us/Environment/2018-Central-Park-Squirrel-Census-Squirrel-Data/vfnx-vebw) - to see the dataset itself, click "Data".
In your sketch, you'll want to add
```html
<script src="https://cdn.jsdelivr.net/npm/chroma-js@2.4.2/chroma.min.js"></script>
```
to `index.html`, the same as we did with `ml5.js` last week. We'll be using [chroma.js](https://gka.github.io/chroma.js/) to add some color to our visualizations.
### Coding Glossary

| Review               |                                                                                                                         |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| array                | ordered series of values, accessed by index (`arr[0]`)                                                                  |
| object               | named bag of values, accessed by key (`obj.name`)                                                                       |
| `map(v, a, b, c, d)` | rescales `v` from range `a–b` into range `c–d`                                                                          |
| `preload()`          | special p5 function that runs *before* `setup()`; this is where we can load things like images or datasets<br>          |
| JSON                 | JavaScript Object Notation: a text format for objects and arrays that can be saved in a file; same syntax as JS objects |

| New terms        |                                                                                                        |
| ---------------- | ------------------------------------------------------------------------------------------------------ |
| dataset          | an array of objects that all share the same keys (one row per object)                                  |
| API              | a URL you can hit that gives you back data, often live                                                 |
| GeoJSON          | JSON with a specific shape for geographic data - features have `geometry.coordinates` and `properties` |
| `loadJSON(url)`  | reads a JSON file (local path or URL) and returns the parsed data                                      |
| `loadImage(url)` | same idea, but for images                                                                              |

### What a dataset looks like in JS

A dataset is just an array of objects with the same keys:

```js
let cats = [
  { name: "Tuna",  age: 3, weight: 9.5 },
  { name: "Mochi", age: 7, weight: 12 },
]

cats[0]         // the whole first object
cats[0].name    // "Tuna"
cats.length     // 2
```

### Loading data: `preload()` and `loadJSON()`

Loading anything takes time, and sometimes we need to access the things we're loading in the `setup()` call. `preload()` is p5's solution: it runs first, and p5 waits for everything in it to finish before calling `setup()`.

```js
let data

function preload() {
  data = loadJSON("books.json")  // local file
}

function setup() {
  console.log(data)  // by now, fully loaded
}
```

`loadJSON` works the same way for a URL:

```js
data = loadJSON("https://earthquake.usgs.gov/.../all_hour.geojson")
```

A local file and an API are the same thing as far as `loadJSON` is concerned, it will figure out which it is and load the data regardless.

### Gotchas

`loadJSON` returns a placeholder object that gets *populated* later, after the file finishes loading. So **you can't access sub-fields of an object inside `preload()`** - they're not there yet:

```js
// broken - raw.features is undefined at this moment
function preload() {
  let raw = loadJSON(url)
  quakes = raw.features
}

// correct - save the whole thing, access attributes in setup()
let raw

function preload() {
  raw = loadJSON(url)
}

function setup() {
  quakes = raw.features
}
```

Same rules apply for `loadImage()` and other `load` functions in p5.

### Always `console.log` your data first

Field-name typos are silent. Before you draw anything:

```js
console.log("loaded dataL ", raw()
```

### `map()`

Almost every line of viz code is "map a range of data values into something that fits in our sketch":

```js
let x = map(book.year,   1960, 2025, 50, width - 50)
let y = map(book.pages,  100,  600,  height - 50, 50)  // y flipped
let r = map(book.rating, 1,    5,    4,  30)
```

---

## Exercise: Personal Data

In *Dear Data*, every postcard has a tiny custom symbol drawn for each row of data, and each feature means something. For example, the postcard was "phone calls I took this week", it could be a circle where:
- circumference represents the conversation length
- color represents how it made you feel (red for angry to blue for peaceful)
- stroke width represents volume (wider is louder)

We're going to make our own version of this - pull up [a few postcards](http://www.dear-data.com/all) if you want a reference.

**Step 1 - collect :**
Write down a tiny personal dataset of **at least 5 items** with **at least 2 attributes** each. Take some time to come up with something interesting!

Examples:
- Last 5 things you ate (food, time of day, how much you enjoyed it 1–5)
- Last 5 songs you played (title, energy 1–5, mood word)
- Last 5 texts you sent (recipient initial, length in words, emotion)
- Last 5 dreams you remember (one-word summary, weirdness 1–5, did anyone else show up Y/N)

**Step 2 - visualize:**
In p5, draw **one symbol per row**. Pick a base shape (circle, blob, weird creature, plant, whatever) and decide how each attribute changes the symbol - size, color, stroke weight, rotation, number of legs/petals/spikes, position on the canvas, etc. Then draw all five. Write your legend down somewhere so you can reference it.

Don't worry about whether it's easy to understand. *Dear Data* postcards aren't readable either; that's the point. Focus on *expressiveness*.

You can hardcode the data as an array of objects at the top - no need to load a file:

```js
let meals = [
  { food: "bagel", time: 9, enjoyment: 4 },
  { food: "salad", time: 13, enjoyment: 2 },
  // ...
]
// then loop over meals and draw one symbol per entry
for (let i = 0; i < meals.length; i ++) {
let xPos = 10
let yPos = i*15
// draw meal at xPos, yPos 
}
```

**Step - share:**
Drop a screenshot in the chat with a one-line legend ("size = enjoyment, color = time of day"). We'll look at a few together.

---

## Before next class

- Next week: we'll take some time to do guided work on finals. Bring your final in whatever state it's in and any questions you have about it.
- Final project due **5/14**.
- If you took option 2: I need your proposal email **today** for sign-off.

---

## Demo & Resources

### Demo:

### Resources:

- [Library of Missing Datasets - Mimi Ọnụọha](https://materialising-data.org/2020/06/19/mimi-onuoha-the-library-of-missing-datasets/)
- [Mimi Ọnụọha's site](https://www.mimionuoha.com/)
- [Dear Data - Lupi & Posavec](http://www.dear-data.com/theproject)
- [White Collar Crime Risk Zones - Lavigne et al.](https://whitecollar.thenewinquiry.com/)
- [Sam Lavigne projects](https://lav.io/)
- [Jer Thorp - *Living in Data* / blog](https://www.jerthorp.me/)
- [Data Feminism (free online)](https://data-feminism.mitpress.mit.edu/)
- [RAWGraphs](https://app.rawgraphs.io/) - point-and-click viz tool, has built-in sample datasets via "Try our data" if you want to explore further
- [NYC Squirrel Census](https://data.cityofnewyork.us/Environment/2018-Central-Park-Squirrel-Census-Squirrel-Data/vfnx-vebw)
- [USGS earthquake feeds](https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php)
- [NASA Open APIs](https://api.nasa.gov/)
- [PokeAPI](https://pokeapi.co/) - fun starter API
- [NYC Open Data](https://opendata.cityofnewyork.us/) - local datasets, lots of options
- [Awesome JSON Datasets](https://github.com/jdorfman/awesome-json-datasets) - no-auth-required
- p5 reference: [`loadJSON`](https://p5js.org/reference/p5/loadJSON), [`loadTable`](https://p5js.org/reference/p5/loadTable), [`map`](https://p5js.org/reference/p5/map)
- [chroma.js](https://gka.github.io/chroma.js/) - tiny color library we'll use
- Coding Train: [10.1 Introduction to Data and APIs](https://www.youtube.com/watch?v=rJaXOFfwGVw) - relevant video
