# PCA - "Principal component analysis"
- A way to take a multidimensional data and turn it into one dimensional data.
- Can take multiple data sets and "filter out" datasets that cause a small
  change in the "output" and rank their relevancy accordingly.
- The output is known as the principal component because it represents, in
  general, all aspects of the data.
- The algorithm used can often return multiple principal components for a dataset.

## How it works
1. Given two dimensional data, draw a line that best fits the data.
  - This line minimizes the distance between each point and the line.
2. A new set of axes are drawn with the x axis being the above line and the y
axis being a perpendicular line. The intersection point of the two lines is at
the center of the "data mass".
3. Translate all your data points to this new set of axes. Since you picked a
   direction that all of your points were on, one dimension is always the same
   in each point (from the reference point of the new axes). Therefore, one of
   the dimensions of the new axes is really redundant (pretty much, there's
   going to be a little variance along the axis but we're calling that
   negligible). That means your data becomes one dimensional.

## Why this is cool
We were just able to combine two dimensions of data into one dimension of data
with a minimal amount of data loss. This means any two features that have a
linear correlation (or an approximate one) can be converted into one feature.
By reducing the amount of features one has to look through, it makes machine
learning able to happen faster (less computation for less features) and can make
trends more apparent across vast swaths of data.
