# Validation

We want to split up our data into training and testing datasets. How do we do this?

Typically, here's what the pipeline would look like:

```
Input => Split test/train => Feature optimization => Classifier => Output
```
- Split test/train: what this validation bit is about
- Feature Optimization: use something like PCA to cut down on the amount of features required.
- Classifier: take some guesses.

Then, to verify the results, the same procedure is repeated above with the test data instead of the
train data. However, things that must be fit should still be fit to the old data to "maintain their
configuration" even though they're run on new data.

## K-fold Cross validation
- A method for determining how much of your data should be test vs training.

Pick a number, in this case, `k`:
  - Split up all your data into `k` bins.
  - For each of the bins:
    - Select that one bin as your training set.
    - Run a learning experiment using that one bin as the test dataset, and the rest as the training dataset.
  - Average the accuracies of all the scores in each experiment.

Literally, this runs your whole pipeline `k` times. Of course, this comes with a time penalty.
However, you gain the ability to basically use all your data for both training and testing data,
which is really cool (since the runs of the algorithm are done seperately, you don;t have to worry
about the results from one round of testing leaking into another tound of testing)

This is the kind of thing you'd use to verify a trend exists, not necisarily every time you want to
use your classifier to take real data from the world and predict.

## Randomization is key.
Before doing cross-validation, randomize the order of your data if the order of your data doesn't
matter. You don't want any implicit biases from the order of the data to leak in! 

# Parameter tuning
Turns out cross validation can also be used to iterate through a bunch of guesses for parameters and
help you determine which set of parameters is going to be the best for a given data set.

- Start with a list of parameters that you're interested in validating, and for each parameter set:
  - Do a cross-validation passing the parameters to your pipeline.
  - Get the average accuracy from each run.
  - Store that accuracy somewhere.

The highest accuracy corresponds to the set of parameters that probably will work the best.
