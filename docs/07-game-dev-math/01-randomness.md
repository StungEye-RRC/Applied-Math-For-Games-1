---
title: Randomness
parent: Game Dev Math
nav_order: 2
---

<!--prettier-ignore-start-->
# Randomness
{: .no_toc }

If something is unpredictable and doesn't seem to follow a recognizable pattern we call it **random**.

Randomness is a crucial element of lotteries, cryptography, simulations, games, and generative art.

## Table of Contents
{: .no_toc .text-delta }  

1. TOC
{:toc}

<!--prettier-ignore-end-->

## Module Topics

- Mean and Standard Deviation
- Probabilities and Distributions
- Pseudo-Random Numbers
- Random Walks

## Objectives

By the end of this module you should be able to:

- Explain what is meant by mean and standard deviation and how to calculate these values from a dataset.
- Describe how to calculate the probability of a single uniform event (coin toss, card selection).
- Differentiate between uniform and Gaussian probability distributions.
- Use p5js to generate uniform, gaussian, and Perlin random numbers.
- Use p5js to simulate and graph the probability distributions of uniform and Gaussian events.
- Implement a random walk simulation using p5js.

## Textbook Chapter

[Intro Chapter - Randomness - Nature of Code](/Applied-Math-For-Games-1/assets/pdf/noc_chp0_2021_draft.pdf) [pdf]

**Attribution:** The textbook for this course is Daniel Shiffman's Nature of Code. The Java Processing version of the book is [available online](https://natureofcode.com/book/). PDF of the p5js version linked above is [under development](https://github.com/nature-of-code/noc-book-2) and is licensed under the [Creative Commons Attribution-NonCommercial 3.0 Unported License](http://creativecommons.org/licenses/by-nc/3.0/).

## Computer Generated Random Numbers

Computers cannot generate true random numbers. This is because computer algorithms are deterministic; when given a specific input they always produce the same output. Because of this we call the random numbers that are generated by computers **pseudo-random**.

Sequences of pseudo-random numbers are predictable if you know the algorithm being used and the "seed" value used to start the sequence.

The "seed" is itself just a number. It's common to use the current time as a seed, since that means the sequence of pseudo-random numbers will be different each time we run the generator.

<iframe src="https://editor.p5js.org/stungeye/embed/J9k1jo_8z" scrolling="no" frameborder="no" width="50" height="50"></iframe>

☝️ _Click the above square to generate a new pseudo random number from 0 to 9._

## P5.js Random Numbers

P5.js includes a function for generating pseudo-random numbers called `random()`.

Without any arguments it returns a random floating point number from 0 up to (but not including) 1:

```javascript
let randomFloat = random(); // Some float from 0 up to (but not including) 1
```

If one numeric argument is given, it returns a number from 0 up to (but not including) the argument:

```javascript
let randomFloat = random(99); // Some float from 0 up to (but not including) 99
```

If two numeric arguments are given, it returns a number from the first argument up to (but not including) the second argument:

```javascript
let randomFloat = random(500, 510); // Some float from 500 up to (but not including) 510
```

Use `floor()` if you want random integers:

```javascript
let randomInteger = floor(random(4)); // 0, 1, 2, or 3 (but never 4)
let anotherRandomInteger = floor(random(10, 13)); // 10, 11, 12, (but never 13)
```

You can also pass an array as an argument pick a random element from that array:

```javascript
let shoppingList = ["goat", "oats", "boat", "coat"];
let randomWord = random(shoppingList);
```

To generate a predictable sequence of pseudo random numbers you can first set the seed:

```javascript
randomSeed(42);
let first = random(); // Always the same "random" number.
let second = random(); // Always the same "random" number.
let third = random(); // Always the same "random" number.
```

## Random Walker

![Attribution: Dan Shiffman - Nature of Code - Chapter 0](eight_directions_chap_0_nature_of_code_shiffman.png){: .small .inline }

In the following sketch a "walker" starts in the middle of the canvas. It then moves pseudo-randomly in one of eight possible equally weighted directions. If the walker's new location is white, it will be painted black. If the pixel is already shaded, it will be painted a lighter shade of grey.

<iframe src="https://editor.p5js.org/stungeye/embed/JN0sVjPmO" scrolling="no" frameborder="no" width="200" height="200"></iframe>

☝️ _Click the canvas to restart the sketch._

[View / Edit This Sketch Using p5.js Web Editor](https://editor.p5js.org/stungeye/sketches/JN0sVjPmO)

## Probabilities

The chance of an event occurring out of a set of possible outcomes is called a **probability**.

When we flip a coin there are two possible outcomes: Heads and Tails

Each outcome has a 50% chance of occurring, or a probability of 1/2 or 0.5.

When we roll a six-side die, there are six equally possible outcomes:

- Probability of a 1: 1/6
- Probability of a 2: 1/6
- Probability of a 3: 1/6
- etc.

In these examples every outcome has an equal probability.

## Varied Probabilities

For certain events, the chance of the outcome isn't just 1 out of the possible number of outcomes.

When pulling a card from a deck of 52 play cards, the probability of pulling an ace is:

`number of aces / total numbers of cards = = 4 / 52 = 0.077 = ~8%`

The probability of pulling a diamond is over three times greater:

`number of diamonds / number of cards = 13 / 52 = 0.25 = 25%`

## Sequences of Probabilities

We can calculate the probability of a sequence of events by multiplying the individual probabilities.

The probability of a coin turning up heads three times in a row is:

`(1/2) * (1/2) * (1/2) = 1/8 = 0.125`

So anytime you flip a coin three times you have a 12.5% chance that all three flips will be a head.

## The Gambler's Fallacy

The probability of rolling only heads decreases as the sequence increases. That said, the chance of rolling a head on each flip of this sequence never changes.

If I managed to flip heads 100 times in a row, there's still a 50% chance that the next flip will be a head.

Thinking otherwise is called the **Gambler's Fallacy**, because gambler's often fool themselves into thinking that past random events will affect the outcome of future events.

## Randomness With Probabilities

Let's say you want to drop some loot with the following probabilities:

- 70% chance of: 🍄
- 20% chance of: 💰
- 10% chance of: 🗡️

To code this you might create an array where the items match their expected probabilities:

```javascript
let lootBag = ["🗡️", "💰", "💰", "🍄", "🍄", "🍄", "🍄", "🍄", "🍄", "🍄"];
let drop = random(lootBag);
```

But you could also use an if/else chain:

```javascript
let lootChance = random(); // Number from 0 up to (but not including) 1
let drop;

if (lootChance < 0.1) // (0 >= lootChance < 0.1) => 10% chance
  drop = "🗡️";
} else if (lootChance < 0.3) { // (0.1 >= lootChance < 0.3) => 20% chance
  drop = "💰";
} else { // (0.3 >= lootChance < 1.0) => 70% chance
  drop = "🍄";
}
```

## Generating Noise