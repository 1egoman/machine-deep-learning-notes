# SVM

They didn't explain how these guys work. Basically, they try to maximise the
distance between two different "categories", and where all those "maximised"
points are located a line is drawn through them. How "maximised" this data is is
known as the margin.

Using a special function called a kernal, one can define a "custom" boundry.
Basically, a kernal is another feature that is calculated that adds another
dimension to the data. In all of the examples shown, the kernal represents the
desision surface the two choices, and when it is added as a feature, the tird
dimension will then contain very different values for each "type" of thing.

Why? For a given point, something within the "kernal" and something outside the
"kernal" will have similar values and each will "cluster" across the added
dimention that adding the kernal as a feature will give you. THerefore, the
linear "decision surface" (now really more of a plane) can then be drawn in the
3rd dimention between the two clusters.

## Kernal type, C and Gamma
Two variables were discussed, C and Gamma:
- C controls how forgiving the SVM is. THis means one can control whether
  "outliers" should be taken into account always or whether to (after a point)
  just take them out of the picture. If C is small, more samples can be
  misclassified and the "seperation plane" becomes more general. An excessively
  large C means take every sample into account no matter what, which can cause
  overfitting.

- Gamma represents the "jaggedness" of a particular kernal. If gamma is high,
  the kernal will "wrap around" the training data. While this may at first seem
  good, this can lead to overfitting of a dataset. So caveat emptor!

## Pros of SVM
- Work well when there's a clear margin of separation between categories
- Don't do well with noise
## Cons of SVM
- Don't work well in very large datasets
