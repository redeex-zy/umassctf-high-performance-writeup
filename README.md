# High Performance — Writeup

Some OSINT challenges are hard because the rabbit hole is deep. This one was not deep at all. It was hard in a more realistic way: it was very easy to get confident too early.

The challenge prompt was:

> I've heard there's a computer shop in the area that sells a computer that isn't designed to run Windows, macOS, or Linux. What's the processor that's in their flagship, PCIe-capable system?

Flag format: `UMASS{Name of Processor}`

At first glance, this sounded almost too direct: geolocate the image, find the shop, identify the unusual computer, extract the processor, submit. That is technically the solve path, but the challenge is good because the final step is just ambiguous enough to punish anyone who stops verifying too early.

## Starting from the zip

The provided archive was simple: it contained a single image, `high-performance.png`.

That immediately made the intended starting point clear. There was no metadata trick, no hidden note, no extra file to parse. The screenshot was the whole entry point.

When I opened the image, I was honestly expecting at least one easy pivot: a storefront, a street sign, a visible business name, a bus stop, anything. Instead, it was just a quiet European-looking street scene with parked cars and residential-style buildings. Useful in a broad sense, but not the kind of image that gives you the answer in one jump.

So the first problem was not “what computer shop is this?”  
It was: **where is this even supposed to be?**

## First impressions from the image

The screenshot gave more of a general feeling than a direct lead.

It looked like a small Western European city: narrow street, tidy buildings, clean road layout, quiet atmosphere, nothing especially flashy. My first geographic instincts were places like Luxembourg, Belgium, northern France, or western Germany.

That is not a precise answer, but it was enough to start narrowing.

At this point, the clue text became more useful than the image itself.

## The first important realization

The wording says:

> “there's a computer shop in the area”

That mattered a lot. It suggested that the shop itself did **not** necessarily need to appear directly in the screenshot. In other words, the image was probably only meant to identify the general area, and from there the rest of the solve would come from nearby businesses.

That changed the way I approached it.

Instead of trying to force an exact building identification immediately, I focused on identifying the **town / area** first and then searching for computer shops nearby that matched the second half of the clue.

## Narrowing the location

From the architecture and overall feel, I kept coming back to **Luxembourg** as the most likely country. The image had that very specific quiet, compact, almost understated urban feel that I associate with Luxembourg locations.

Following that lead, I eventually landed on **Differdange, Luxembourg**.

That was the first real breakthrough, because once I had Differdange, the search space for “computer shop in the area” became much smaller and much easier to work with.

From there, I found **AAA Technology**.

## Finding the right shop

AAA Technology stood out quickly, because it was not just a generic computer repair or office hardware store. It had the kind of niche-computing profile that made the second half of the clue suddenly make much more sense:

> “a computer that isn't designed to run Windows, macOS, or Linux”

That strongly suggested some alternative computing ecosystem, and once I found AAA Technology, the most plausible direction became **Amiga-related systems**.

This was the point where I felt like I had basically solved the challenge.

That feeling was premature.

## The first wrong turn

Once I was in the Amiga hardware space, I made what I think is the most natural mistake in the challenge: I went looking for the most “flagship-looking” PCIe-capable machine I could find.

That led me to the **AmigaOne X5040**.

At the time, it looked like an excellent fit:
- clearly non-mainstream
- clearly outside the normal Windows/macOS/Linux world
- PCIe-capable
- and very easy to interpret as a flagship product

The processor associated with it is:

**Freescale P5040**

That sounded convincing enough that I submitted:

`UMASS{Freescale P5040}`

It was wrong.

## Why the wrong answer was so tempting

In hindsight, this is what makes the challenge good: the wrong answer was not random at all. It was believable.

The reasoning was not lazy. It looked something like this:
1. identify the area
2. find the shop
3. recognize the Amiga angle
4. find a premium PCIe-capable system
5. extract the processor
6. submit

That is a perfectly human solve path. The problem is that I quietly changed the wording of the challenge in my head.

I treated:

> “their flagship, PCIe-capable system”

as if it meant:

> “the most powerful or premium-sounding niche machine I can find”

That is plausible, but it is not proven.

And that is exactly the kind of mistake OSINT challenges punish.

## The realization that fixed it

After the wrong submission, I went back and reread the prompt more carefully.

The challenge does **not** ask for:
- the strongest machine in the ecosystem
- the most expensive historical system
- the most famous Amiga product
- or the coolest answer you can find

It asks for the processor in **their flagship, PCIe-capable system**.

That pushed me back toward the store’s actual relevant offerings instead of the broader Amiga ecosystem. In other words, I stopped looking for “what sounds flagship to me” and started looking for “what best matches the shop context and the clue wording.”

That shift made the rest of the solve much cleaner.

## Second pass: the intended system

This time I stayed much closer to the systems actually relevant to the shop and the wording of the prompt.

That led me to the **A1222+**.

This fit the clue much better:
- it belongs to the Amiga ecosystem
- it is clearly outside the normal Windows/macOS/Linux space
- it is explicitly PCIe-capable
- and it matched the challenge in context more cleanly than my first guess

The listed processor for the A1222+ is:

**NXP QorIQ P1022**

So the correct flag is:

`UMASS{NXP QorIQ P1022}`

## Why this challenge worked well

What I liked about this challenge is that it did not require some absurd rabbit hole or one impossible leap. The research path was fair, and the clue gave enough structure to stay grounded.

The difficulty came from something much more realistic: **overconfidence**.

Once I found the correct shop and the correct ecosystem, it was very easy to stop verifying and submit the first processor that seemed “flagship enough.” The challenge punished that in a very fair way.

That is what made it a good medium OSINT challenge to me. It was not hard because the answer was hidden impossibly well. It was hard because it required discipline all the way to the final step.

## Final flag

`UMASS{NXP QorIQ P1022}`

## Closing thoughts

If I were describing the real solve path honestly, it would be:

- unzip the file
- stare at a street that looks far too normal
- narrow the country vibe toward Luxembourg
- land on Differdange
- find AAA Technology
- get excited because the Amiga angle appears fast
- tunnel vision onto the X5040
- submit too early
- get punished
- reread the prompt more carefully
- stop assuming “flagship” means “most impressive sounding”
- find the A1222+
- extract **NXP QorIQ P1022**
- solve

That is probably why this challenge stuck with me more than a one-shot solve would have. It was not the kind of problem that overwhelms you with difficulty. It was the kind that waits for you to get comfortable, then checks whether you are still reading carefully.

And in OSINT, that is usually where the real mistakes happen.
