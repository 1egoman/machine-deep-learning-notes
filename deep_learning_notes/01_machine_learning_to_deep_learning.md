# Deep Learning
- A subset of machine learning
- Really only has become popular in the last 10 years or so

- The course focuses on classification.

## Turning detection (x,y location) problems into classifcation problems
- Say you have a large image and are looking for people in that image.
- You can train a classifier with a bunch of images of people.
- Then, you run that classifier multiple times over small sections of the image.
- THe sections that are classified as a person you then can assume have people in them, and the
  other sections don't.

## Turning relevancy problems into classification problems.
- Problem: Given a search term and a list of choices, rank choices by relevancy.
- Train a classifier that takes as input a query and a list of choices and returns a boolean of
  relevant or irrelevant.
- Since you're classifying the pair, you're able to still use a boolean classifier
- This method won't rank the relevant results, only return onces that are relevant.


# Logistic classifier
- Linear classifier

WX + b = y

Where:
- `X` is the input vector
- `Y` is the output vector (sometimes refered to as "Logits" in the context of logistic regression)
- `W` is a matrix of weights
- `b` is the bias

What's going on here?
- X is a big vector of information that comes from the input for a given data sample. For example,
  could be pixel values of an image, sound frequency over time, etc.
- X is multiplied by W, a matrix. Matrix multiplication is like bitmasking - the matrix is ued to
  say "how much" of each element of X is in the output. Ie, if X=[1, 2] and W=[[0, 1], [0, 0]] then
  WX is going to be [0, 2] - the first element was "masked out" and the second element was kept.
- Bias I'm not realyl sure how it's used now, but my guess is a "fudge factor" to make the math work
  out.

# Softmax
- Takes as input a bunch of weights and as output determines the probablility of each weight.
- The results are expressed as floats where `sum(softmax(ANYTHING)) == 1` (they're probabilites,
  they add up to 100%)

- If items passed into softmax are big, then the results will be very polarizing. This is because as
  the number gets bigger, the numerator of the function gets bigger because a larger number is
  further along the exponential curve than a small number (as x -> infinity on an exponential graph, the respective
  change gets greater along the y axis for a set distance along the x axis). This effects the
  numerator and denominator in one case and the denominator in all the other cases.

- If the items passed into the softmax are small, then they get closer to the normal distrucution of
  all inputs.

```
def softmax(x):
  e_to_each_term = [math.e ** n for n in items]
  return [math.e ** n / sum(e_to_each_term) for n in items] 
```

- In plain language:
  - do `e^n` for each term in the input vector.
  - take the sum of the previous step, store into `terms_sum`
  - each term in the input space maps to `e^n / terms_sum`

  5^n
  ------
  (5^n + 5^n+1 + 5^n+2 + ...)

*NOTE*: The larger the inputs to softmax, the more confident the classifier. Intuitely, this makes
sense, because each number represents "more" of a percent of the total as a number gets bigger.

THerefore, as a classifier gets more confident, we should expect it to return larger numbers prior
to entering the softmax step.

# One hot encoding
Transforming a vector of probabilities to its boolean representation where the largest probability
gets 100% and the rest get 0%.
ie, `[0.7, 0.2, 0.1] -> [1.0, 0.0, 0.0]`



  TIPF or TIPS fund
