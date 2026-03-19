
## Generative Music & Making Music With Code

> **Generative music: music created by a system or process, not composed note-by-note by a human.**

Like the generative text and images we've looked at, generative music has a history that long predates computers. The key is, as with other art forms we've looked at, rulesets that result in indeterminate results, from tape looping to improvisational systems.

### Artists & Works

**Terry Riley, [*In C*](https://www.youtube.com/watch?v=u7IErSweXpk)** (1964)

Musicians are guided to repeat a series of 53 melodic fragments, individually determining how to repeat them, how many repetitions, and whether or not to transpose them up. The piece ends when *every* player has made it to the 53rd fragment. It is, by its nature, indeterminate and its length and sound are dependent entirely on the choices of the players. I *highly* recommend seeing it performed live if you get the chance.

**Steve Reich, [*It's Gonna Rain*](https://www.youtube.com/watch?v=vWN9I-qa9GQ) (1965)**

Keeps with the tradition of "happy accidents" in generative music - Reich used two tape recordings of a Pentecostal preacher to create the piece. The two fell out of sync, so Reich used phase shifting to explore all possible repeated harmonies before they eventually get back in sync with one another. Major inspiration for Eno.

**La Monte Young**, ***[Dream House](https://vimeo.com/62965018)* (1966-present)**

An audiovisual installation that produces a continuous sound based on 32 sine wave tones. The audio is experienced differently as you move throughout the space. The [permanent installation](https://www.melafoundation.org/) is in NYC, and you can visit it for extra credit - I highly recommend going in person, the videos don't do it justice.

**Brian Eno, *[Music for Airports](https://www.youtube.com/watch?v=vNwYtllyt3Q&list=RDvNwYtllyt3Q&start_radio=1)* (1978)**
Eno coined the term "generative music." *Music for Airports* uses four tape loops of different lengths playing simultaneously — because the loops are different lengths, they drift in and out of phase with each other, creating music that never exactly repeats. The algorithm serves as the composition in his work. He later developed software (Koan, later Bloom) to generalize this idea, and is widely considered the father of ambient music.

**William Basinski, [*Disintegration Loops*](https://www.youtube.com/watch?v=mjnAE5go9dI&list=RDmjnAE5go9dI&start_radio=1) (2002)**
An accident: Basinski was digitizing old analog tape loops when the tape began to deteriorate mid-transfer. He let it run. The gradual degradation of the audio became the piece.

**More recent:**
- [Holly Herndon](https://en.wikipedia.org/wiki/Holly_Herndon) — AI-trained vocal synthesis, algorithmic composition
- [Ryoji Ikeda](https://www.ryojiikeda.com/) — data-driven sound and visual art, mathematical structure
---

## Making Music With Code

Pretty much everything you'll see in class today is built with the [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API). This can be pretty intimidating at first, but when you use libraries like p5 sound or Tone.js, you're effectively just writing code to create MIDI sound, the same output that Digital Audio Workstations like Ableton create. Using these tools, we can create our own synthesizers, either for users to make music in the traditional DAW mode or for our own extended/generative work. Making music with code really centers around a few simple concepts:

*A quick aside: I am **not** a musician - if there are any musicians in class who find issues with these explanations, feel free to butt in.

**Frequency & Amplitude**

Sound is vibration. Two numbers describe most of what you need:

- **Frequency** (Hz) — how fast the vibration is. Higher frequency = higher pitch. 440 Hz is concert A. Human hearing ranges from about 20 Hz to 20,000 Hz.
- **Amplitude** — how strong the vibration is. In code, usually expressed as a value from 0 (silent) to 1 (full volume).

These map directly to the `osc.freq()` and `osc.amp()` calls in p5.sound.

**Synthesis vs. Sampling**

Two basic ways to make sound with code:

- **Synthesis** — generate a waveform mathematically. No audio file needed. This is what an oscillator does.
- **Sampling** — play back a recorded audio file. This is what `loadSound()` does.

Most music software uses both. A drum kit is usually samples; a synth lead is usually synthesized.

**Waveforms**

When you create an oscillator, you pick a waveform shape. Each has a distinct timbre:

| waveform | sound character |
|---|---|
| sine | smooth, pure tone — like a tuning fork |
| triangle | slightly hollow, softer than square |
| square | buzzy, hollow — classic 8-bit sound |
| sawtooth | bright, harsh — classic synth/lead sound |

All four produce the same pitch at the same frequency; the shape changes the *tone* of the sound.

Using an oscillator with a chosen waveform, frequency, and amplitude is how we make synthesized sounds.


**Fun examples:**
- [otomata](https://marwahaha.github.io/otomata/): make music with a cellular automata grid
- [patatap](https://patatap.com/): built with Tone.js - shapes that correspond to sound. More [here](https://en.wikipedia.org/wiki/Patatap)

---

### Live Coding

Live coding is a performance practice where code is written or modified in real time, usually with the screen projected for the audience. The music (or visuals, or both) changes as the performer edits — they write code the same way traditional performers play their instruments.

Live coding has a loose global community organized around [TOPLAP](https://toplap.org/). [livecode.nyc](https://livecode.nyc/) is the local chapter - you can also go to one of their meetups or events for extra credit!

**Practitioners:**
- **[Alex McLean](https://yaxu.org/)** (aka yaxu) — one of the founders of TOPLAP and creator of TidalCycles, the pattern language that Strudel is based on. [Performance example]([https://www.youtube.com/watch?v=XifWBDnFEGs](https://www.youtube.com/watch?v=fIuqDKzYBzc)).
- **[Sam Aaron](https://sam.aaron.name/)** — creator of Sonic Pi, which started as an educational tool for teaching programming through music and grew into a serious live performance instrument. 
- **[Kindohm](https://kindohm.com/)** (Mike Hodnick) — Minneapolis-based livecoder, works primarily in TidalCycles. Known for dense, industrial-influenced patterns.
- **[Olivia Jack](https://ojack.xyz/)** — creator of [Hydra](https://hydra.ojack.xyz/), a browser-based live coding environment for visuals. Often combined with live-coded audio; a good example of the audio/visual pairing that runs through a lot of this work.
- **[DJ Dave](https://www.youtube.com/watch?v=JiQHclg_648)** — often performs with [Char Stiles](https://www.youtube.com/watch?v=lEJiP4JGEh0) handling live-coded visuals simultaneously.

**Tools:**
- [Sonic Pi](https://sonic-pi.net/) — Ruby-based, designed to be approachable. Good starting point.
- [Strudel](https://strudel.cc/) — browser-based port of TidalCycles. Pattern-focused, JS syntax.
- [Gibber](https://gibber.cc/playground/index.html) — browser-based, more visual feedback than Strudel.
- [Hydra](https://hydra.ojack.xyz/) — browser-based live coding for visuals; pairs well with Strudel or Gibber for audio.
- [Orca](https://hundredrabbits.itch.io/orca) — esoteric: a 2D grid of characters that generate MIDI events in real time. Made by [100 Rabbits](https://100r.co/site/home.html), a 2-person art collective that live on a houseboat!