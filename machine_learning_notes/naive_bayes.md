# Naive Bayes
Looks at work frequency only by determining the probability of one of the corpus words being the
current word. Because it uses frequency 

To determine the likelyhood that a corpus belongs to a category, I can multiply the probabilty of a
word being the current word in each possible "slot". Then, multiply by the "weight" of the
category. If there are two possible categories, then the weight for each (if they are weighted
evenly) is 0.5, three would be 0.3333, etc.

## Example
If group a has three words: foo with 20%, bar with 50%, baz with 30%
If group b has three words: foo with 80%, bar with 10%, baz with 10%

The probability that the corpus "foo foo bar" belongs to each:
- probability group a = p(foo) * p(foo) * p(bar) * "weight"
                 p(a) = 0.2 * 0.2 * 0.5 * 0.5 = 0.01
- probability group b = p(foo) * p(foo) * p(bar) * "weight"
                 p(b) = 0.8 * 0.8 * 0.1 * 0.5 = 0.032

Each probability needs to be normalized from the range 0-(p(a)+p(b)) to 0-1:
- Group a normalized = part / whole = 0.01 / (0.01+0.032) = 0.238095
- Group b normalized = part / whole = 0.032 / (0.01+0.032) = 0.761905

76% chance it's group b, which makes sense considering that foo is in there twice and the likelyhood
of foo in b is 80%. 

## Pros of Naive Bayes
- Large numbers of features
- Efficient (relatively speaking)

## Cons of Naive Bayes
- Breaks in weird ways
- Naive Bayes isn't as good at finding differences between things whoose output depends on the order
  of the input.
