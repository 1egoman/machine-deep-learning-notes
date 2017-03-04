# K Means clustering
A form of unsupervised learning. This means that we don't start with
"predefined" categories and instead categories are generated procedurally.

## The algorithm
- Basically, we start with center points that are randomly (or otherwise)
  placed. Randomly works though which is what I think makes this really cool.
- Iterate through the below steps:
  1. For every data point, determine the "center" point that the data point is
  closest to.
  2. Once all points have been divided up into groups, for each group:
    - Take the average of all the x coordinates of the data points.
    - Take the average of all the y coordinates of the data points.
    - Move the center point to the given (x average, y average) point.
  3. With the new center point positions, run the algorithm again.

What will happen is that as the algorithm progresses, the centers start to
migrate to where you'd expect. This is because the data that is gathered in each
sample (each "iterative group") directly effects the next run of the algorithm,
so large errors keep dividing in half until they become negligible.

## Edge cases
- If two "centers" are put into the middle of a cluster, they'll fight for the
  points in that cluster and in turn that cluster will be split up into two when
  in fact it should realyl be classified as one. Therefore, the initial
  locations of the center points can have a strong effect on the outcome of the
  clusters that are formed. This idea of having a split that is really
  suboptimal but in fact is classified as optimal is called a *local minimum*.
- If a cluster can be split up in a different way that garuntees the same
  "minimization distrobution", then the clusters can be misclassified. An
  example of this is a graph devided into 4 quarters with one point in the
  center of each quarter, with two centers. it may devide it vertically or
  horisontally, depending on the initial locations of the centers.

## SKLearn
- `sklearn.cluster.KMeans`
