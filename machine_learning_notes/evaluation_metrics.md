# Evaluation Metrics
How do you determine that your algorithm works?

Accuracy = total correct / total

## When accuracy isn't great....
When there's a low amount total, the "resolution" of your accuracy isn't going to be that high.
Also, because for boolean classifications you have to pick a "threshold", you need to figure out
whether you want to put the boundary of where to cast people in the middle as either true / false.

## Confusion Matrix
A way to graphically draw out the accuracy of an algorithm.

                      The actual class ()

                           A   B
                         o---o---o
                         |   |   |
                       A | _ | _ |  
                         |   |   |
   The predicted class   o---o---o
                         |   |   |
                       B | _ | _ |
                         |   |   |
                         o---o---o

Each data point in this case could either be an A or B. The goal is to determine which points were
classified accurately and which were classified incorrectly, and when classified incorrectly, how
many were classified indirectly in each way (so, A being classified as B vs B being classified as
A). In each box, the count of the given classification (so, where the predicted class was A and the
acual class was B, for example) is placed.

In a confusion matrix, the main diagonal (from top left to bottom right) contains all the correct
predictions and therefore is usually highest. This provides a rough accuracy of the matrix as a
whole.

# Precision and Recall

Recall: How often is a given prediction made?
Or, how many positive items were **recall**ed from the dataset?

A high recall means a given "answer" is used a lot.

Precision: How often does a given prediction come true?

A high precision means that a guess will likely be correct.



For example: I put 3 playing cards on the table upside down. The first is a red card, the second is
a black card, the third is a red card.

The first card I classify correctly (red).
The second card I classify incorrectly (classify as red, actually black)
The third card I also classify incorrectly (classify as black, actually red)

Recall of the red: 2 red guesses in total (first and second cards) / 3 total = 2/3
Precision of the red: 1 red guessed correctly (the first card) / 3 total guesses = 1/3
