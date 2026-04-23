Agenda:
1. Presentations
2. Homework review
3. Tutorial: external libraries
4. [FINAL](<./FINAL.md>)


----
## Tutorial: External Libraries

p5.js and p5.sound.js are two core frameworks that we have used in this class that focus on graphic and sound explorations in the web. But we can also use _external_ (meaning not maintained by the Processing Foundation) libraries that leverage p5 to do interesting things.

You can see a full list of the libraries of p5 by visiting https://p5js.org/libraries/directory/.

### Video Explorations

We can leverage the webcam to do a lot of things inside p5.js, and we can even manipulate individual pixels.

Let's start with regular pixel manipulation and then add a library on top of it.

The most important line of code for video allows us to enable webcam usage.

```js
// prompts the browser to use the webcam
webcam = createCapture(VIDEO);
```

We could _also_ use a phone camera instead if we wanted

```js
// if i am using a phone camera
let constraints = {
	audio: false,
	// back camera code
	video: {
		facingMode: {
			exact: 'environment', // back camera
		},
	},
	// front camera code
	//video: {
	//facingMode: "user"
	//}
};
webcam = createCapture(constraints);
```

What this does is allow us to add the webcam as an HTML element. If we wanted to hide that element and just display the camera on the screen, we could write

```js
//... in the setup
webcam.hide();
//... in the draw
// display webcam data to the draw
image(webcam, 0, 0);
```

### Example Library: Using ml5

https://ml5js.org/ is a library built on top of p5 to use machine learning. They have a few different types of tools that you are welcome to use, but today's demo will focus on BodyPose https://docs.ml5js.org/#/reference/bodypose

The first thing we always do when using an external library is open up our `index.html` and import the library code.

```html
<script src="https://unpkg.com/ml5@1/dist/ml5.js"></script>
```

## Demos and Resources

### Demos

### External Resources

- Allison Parrish, [Working with Video](https://creative-coding.decontextualize.com/video/)
- Coding Train `ml5` Playlist [Introducing ml5 using FaceMesh](https://thecodingtrain.com/tracks/ml5js-beginners-guide/ml5/0-introduction/patt-vira)
- Coding Train [Live Video and `createCapture()`](https://thecodingtrain.com/tracks/pixels/pixels/createCapture) Playlist