# Spaced repetition from the ground up

Here is the complete algorithm described in the [Spaced Repetition From The Ground Up](https://controlaltbackspace.org/spacing-algorithm/) post.

This is only meant to serve as further brainstorming material for the design of the system. Afaict the algorithm described here is supermemo-2.

The post was read and this document was written fully by a human and not AI to prevent any inaccuracies.

## The Algorithm

### Interval calculation
- Arbitrary values.
- Always round down fractions.
- Add 1 to the calculated interval.
- Randomize the interval by a small percent of it (%10) to prevent clustering. A 10-day interval can be 9 or 11.

### Ease
- Indicates how hard a particular card is.
- New cards get %250.
- Never drops below %130.

### Difficulty levels
- Easy: I remembered the answer to this card easily. The interval was too short and should increase more this time.
- Good: I remembered the answer to this card, and I had to think a little but not too hard. The interval was about right.
- Hard: I remembered the answer to this card, but only with great difficulty. The interval was too long and should increase less this time.
- Again: I did not remember the answer to this card. I need to try again soon.

### Difficulty level - interval calculation
- Easy: multiply with ($ease * %130)
- Good: multiply with $ease
- Hard: multiply with %130
- Again: reset to 1 day

### Difficulty level - ease change
- Easy: +15 pp
- Good: no change
- Hard: -15 pp
- Again: -20 pp

### Overdue cards interval update
- Easy: interval + overdue amount
- Good: interval + (overdue amount / 2)
- Hard: interval + (overdue amount / 4)
- Again: interval

### Order of operation
1. Review the cards due today.
2. Update the intervals for overdue cards, if there are any.
3. Calculate new intervals and save them.
4. Calculate new ease levels and save them.