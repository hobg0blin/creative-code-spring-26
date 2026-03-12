

## A Little Background on Generative Text

![Text of "To Make a Dadaist Poem" by Tristan Tzara, 1920, with instructions for the cut-up technique](<./images/Pasted image 20260311120428.png>)

I'm sure you'll be shocked to learn that generative text, like other techniques we've covered in class, has a history that significantly predates the invention of the computer. We've talked about Dada before in class: one of the original forms of generative text was dadaist poetry, or the [cut-up technique](https://en.wikipedia.org/wiki/Cut-up_technique) where you cut up a newspaper article, shake up the words, and write them down to make a poem. This has influenced writers like William Burroughs, but maybe more interestingly a *significant* number of songwriters, like David Bowie, Thom Yorke, and Jeff Mangum.

Key thing to note here: the dadaist poetry instructions are a generative algorithm! A clear and predictable instruction set that results in an unpredictable result. We can *easily* translate this to JavaScript, as you can see in [this cut-up method sketch](https://editor.p5js.org/brondle/sketches/vuha7AnC8). Try playing with it by adding in your own text!

The cut-up method uses a newspaper article, but with code we can use any text we want as long as it's formatted correctly. In the context of generative text, we call this base text a "corpus": it's a body of text you pull from to create a generative output. The links this week includes a massive corpus of every book on Project Gutenberg - for "coherent" generative text, you usually need an insane amount of data. Most LLMs, for example, are trained on basically every recorded word that is publicly accessible, and some that aren't supposed to be!

Some other key historical moments in generative text:

![ELIZA chatbot terminal showing a conversation between a user and the mock Rogerian psychotherapist program](<./images/image-11.png>)

[ELIZA](https://en.wikipedia.org/wiki/ELIZA), the first chatbot. Used slightly more elaborate natural language processing ruleset to mimic the process of psychotherapy. People *immediately* came to believe it was much more intelligent than it was - this term is called the [ELIZA effect](https://en.wikipedia.org/wiki/ELIZA_effect). One of the earliest examples of one of the more dangerous quirks of human psychology, which is our extreme tendency to project intelligence or understanding onto anything that can produce text. Worth remembering when you engage with AI and chatbots.

[Markov chains](https://en.wikipedia.org/wiki/Markov_chain): the very first "AI" method - a relatively simple next-token predictor. Again, not that complex! You can implement a Markov chain [easily in p5.js](https://editor.p5js.org/codingtrain/sketches/Y6SvoMcyH)

After Markov chains, people were convinced we were a few years away from true artificial intelligence, but it ended up taking about 45 years for computation to catch up with math, when the latest AI boom started. I'll get deeper into AI/ML later in the semester - for now we can just focus on a couple of things:

![Diagram of the transformer architecture showing encoder and decoder stacks with multi-head attention, feed-forward, and embedding layers](<./images/image-12.png>)

[Transformers](https://en.wikipedia.org/wiki/Transformer_(deep_learning)): the mechanism behind large language models (like ChatGPT or Gemini) - introduced in 2017. The math is complex, but you can actually implement transformers in just [200 lines of pure Python](https://karpathy.github.io/2026/02/12/microgpt/)!

[Word embeddings](https://en.wikipedia.org/wiki/Word_embedding): ways to measure word similarity. These are often used in text generation to pair similar or opposite words together.

## Artists Who Work With Generative Text

![A generative poem from Allison Parrish's Reconstructions: "Banners, and the sun / Proud and one sun, and weary souls..."](<./images/Screenshot 2026-03-11 120629.png>)

[Reconstructions](https://reconstructions.decontextualize.com/), Allison Parrish

![Cover of Subcutanean by Aaron Reed, a dark atmospheric novel cover with the tagline "a novel where no two copies are the same"](<./images/Pasted image 20260311121053.png>)

[Subcutanean](https://blog.zarfhome.com/2020/05/subcutanean-and-variations-thereof),  Aaron Reed

![Page 1 of Megawatt by Nick Montfort, showing densely repeated sentence variations beginning "Watt heard voices"](<./images/Pasted image 20260311121352.png>)

[Megawatt](https://apod.li/megawatt), Nick Montfort

### Bots

Bots can be useful - weather or train updates - and in some cases are forms of citizen journalism, like [@congressedits](https://en.wikipedia.org/wiki/CongressEdits). 

![](<./images/image-22.png>)
For this class, we're more interested in creative applications of bots. Unfortunately since Twitter became *X* they started charging heavily for API access, and it is no longer a bot-friendly place, but for a few years in the 2010s there was a beautiful little scene where people made art and meme bots for each other's entertainment.

![A post from @RoofSlapping@botsin.space reading "*slaps roof of your mouth* this bad boy can fit so many teeth in it"](<./images/Pasted image 20260311120249.png>)

[Roof Slapping Bot](https://post.lurk.org/@RoofSlapping@botsin.space), Darius Kazemi

![](<./images/image-18.png>)

![](<./images/image-19.png>)

[NYT First Said](https://bsky.app/profile/nyt-first-said.bsky.social) - Max Bittker, currently inactive

![parrish-everyword-gallery-1](<../images/parrish-everyword-gallery-1.gif>)

[Everyword]([https://the-next.eliterature.org/works/755/0/0/](https://www.decontextualize.com/2011/10/everyword-on-gawker/)) - Allison Parrish

![](<./images/image-20.png>)

[horse_ebooks](https://www.newyorker.com/tech/annals-of-technology/horse-ebooks-is-human-after-all) - initially a spambot that was then purchased by some BuzzFeed employees who used it as an art experiment - still not entirely clear what was human-written and what was bot-written.

[A big, big list of bots](https://gist.github.com/derhuerst/1cb20598b692aa87d9bb)