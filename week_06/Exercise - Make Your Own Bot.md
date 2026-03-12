## Exercise

Make your own bot with [Blue Bots, Done Quick](https://bluebotsdonequick.com/). You'll need a [Bluesky account](https://bsky.app/) to use for your bot (if you have a personal account, don't use it unless you're OK with the bot automatically posting to it!)

## Quick Guide

Blue Bots, Done Quick uses [Tracery](https://tracery.io/) to produce generative sentences. The way Tracery works is basically to make a sentence with placeholders for text that is randomly selected from an array (a list of things in JavaScript - for now, we're just using lists of strings or words). You can play with this [p5 tracery example](https://editor.p5js.org/allison.parrish/sketches/ByfvClyTg) to get a sense of how it works.

![](<../../Attachments/image-13.png>)
So, this will produce a sentence *like* "The quick brown fox jumped over the lazy dog", but with random adjectives, verbs, and animals. 

It gets the words for the randomized sentence from the JSON (JavaScript Object Notation)  in the "JSON view" panel. The important stuff to remember here:
JSON always starts with `{}`. It will break if you don't include this.

The items like "origin" or "animal"  are `keys`: we can reference them in our randomized sentence by surrounding them with `#` symbols. "origin" is `reserved`, and is used to store the sentence we'll be inserting random words into.

The stuff after the `:` is an array of strings. 
Stuff to remember: 
- *always* make sure your information is inside of the brackets `[]`
- surrounded by quote marks `""`
- and there is a comma after each item. 

So if I wanted to make a very simple Tracery bot I could do something like this: create a new key in the JSON view

![](<../../Attachments/image-15.png>)

And update my "origin" sentence (this will automatically update it in the JSON):

![](<../../Attachments/image-16.png>)

If everything is formatted right, you should be able to see a preview post inside the app - you can hit "Reroll" to generate a new one:
![](<../../Attachments/image-17.png>)

Once you're happy with your bot, you can post automatically by hitting "Post Now", or set a posting interval in "Posting Frequency".