# Papermemo 

## A design for a paper-and-pen based, scalable and efficient spaced repetition system

## Why?

This system is meant to serve people who need a spaced repetition system, but don't have ready access to digital devices or when digital device usage is undesired.

## How?

- The system is composed of 3 slightly modified [Leitner systems](https://en.wikipedia.org/wiki/Leitner_system), each with varying base periods (day, week, month) piped back to back. Anybody seeking to use or understand Papermemo should first get familiar with the Leitner system, especially the *Proficiency levels* mode. 
- The [design.jpeg](design.jpeg) file further explains the system. It's not very well articulated at the moment due to lack of time. A dedicated person should be able to understand it.
- The system is meant to be used with a custom keyboard sized box (3D printed) made for this purpose.
  - A possible design for the box is: 3 rows, each with 10 slots to put the Leitner layer decks in, along with 31 3D-printed decks to put in these slots, each of which hold hard-paper based cards.
  - Color coding can be used on the decks instead of numbers (in Leitner system) for faster access.
  - Daily review process: 
    1. Take the relevant decks for today out of their slots. Don't take out the cards out of the decks to prevent mixup.
    2. Review the decks and move the cards depending on remember/forget.
    3. Put the decks back into their slots.
- There are a total of 33 decks. Cards move through the in the following order:
  1. 1 waitlist deck to store new cards before they move into the system.
  2. 1 deck reviewed every day, holding maximum 7 cards.
  3. 10 daily Leitner decks, each holding ~8 cards.
  4. 10 weekly Leitner decks, each holding ~32 cards.
  5. 10 monthly Leitner decks, each holding ~230 cards.
  6. The retired cards deck, to store retired cards indefinitely.
- Maximum interval tops out at 7 months before a card is retired.
- If a card is remembered correctly it stays or moves according to Leitner system. If it's not remembered correctly it moves to the previous layer.

## Limitations

- The system accepts at most 7 new cards a day, totaling at ~2500 cards/year (you can still make cards and put them in the waitlist).
- At most 96 cards can be reviewed per day.

## Design decisions

- Implementing a more modern and efficient algorithm was [considered](supermemo2.md), but it seemed too impractical. There seems to be no practical and scalable pen-and-paper based solutions which require the user to make calculations.
- The intervals are matched as closely as possible with the Mochi app's defaults. Mochi multiplies the previous interval with 1.8 on remember and 0.5 on forget. Unlike Anki, Mochi considers fractional results in day calculation are doesn't round under the hood, they are only rounded to the closest (not rounded down) integer when presenting the intervals to the user. Thus, if a card is remembered correctly each time the interval series look like this: 1 days, 2 days, 3 days, 6 days, 10 days, 19 days and so on.

## Status

There have been no users of the system and it has not been tested in the real world.

## Prior art

There are no known prior pen-and-paper based spaced repetition systems that are both efficient and scale to thousands of cards.