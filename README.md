# AdaBoost-KNN-SVM-for-Wine-Dataset-Classification
Here I use three different Machine Learning Classifiers to try classifying the wine dataset, see my report in the readme file

The dataset that I used was the Wine Quality Dataset which included a binary classification of
type (Red or White). The data set was originally split into two parts - red and white - on the UCI
Machine Learning repository website. However, I merged the two datasets and added the
classifier values 0 for Red and 1 for White. The dataset consists of 11 features such as acidity,
ph, density, alcohol content and more. In total, there were 6495 data points, which is unequally
distributed as the red group makes up 75% of the total data points.
The 3 classifiers that I chose included Adaboost, KNN and SVM. For each method a 0.75/0.25
training testing spilt was used. For all 3 methods, 5-fold cross-validation was used. For each
method a parameter optimization loop was also ran and the value that resulted in the highest
overall accuracy was used.

For Adaboost the parameter,optimized was the number of weak classifiers ranging from 1 to 100
in increments of 10. Accuracy increased linearly from 10 to 30, but followed a rolling hills
pattern for higher values. At the end, 70 was the optimal value which resulted in an accuracy of
99.2%. However, 10 trees were able to get an accuracy of 98%. So the jump in accuracy is not
really significant. I assume using an even lower number of trees would result in similar levels of
accuracy. Therefore on the basis of minimizing computing resources and complexity, I would be
fine with using 10 weak classifiers as using more provides diminishing returns. Adaboost
provided the highest accuracy overall. I kind of expected this result as the dataset is structured in
a way for which adaboost would be the ideal algorithm. For example, the twos groups have
substantially different means with little crossover in variables like pH and alcohol content.
Therefore it is no surprise that the algorithm achieved nearly 100% accuracy. As evident by the
ROC curve which reaches the top left corner.

For the KNN algorithm, the parameter optimized was the number of neighbours from 1 to 40.
Disappointingly the optimal number was 1 which achieved an accuracy of 94.4%. The general
trend was that accuracy decreased (not by a significantly measure) as the number of neighbours
was increased. I wasn’t expecting this, I thought maybe 3-5 would be optimal. However, 1 being
the optimal value makes sense; most of the errors would come from a heavily overlapped section
between the two groups. Therefore adding more neighbours may just result in noise. I still kind
of find it funny that the best approach was the simple approach of using the classification of a
single known point closest to the actual value.

SVM achieved a similar max accuracy to KNN, of 95%. The SVM kernel used was the Radial
basis function, with the optimization parameter of the gamma (smoothness) from 0.1 to 1 in
increments of 0.1. The optimal value was determined to be 0.1 with accuracy decreasing almost
perfectly linearly with increases in gamma. I wasn’t expected this result either, as a I assumed for
a lack of a better term a more squiggly line would have resulted in lower error, due to the
complex overlap region mapping. However, I guess an almost straight line was better suited for
this specific dataset. SVM was significantly more resource hungry, having nearly 8 times the
training time compared to Adaboost and KNN. Which is definitely something I will have to
consider going forward.

My overall reflection is that based on the dataset, some classifiers are better suited to datasets
than others. Adaboost is probably best for datasets that have multiple parameters capable of
perfectly slicing datasets Such as this dataset used. It should also be noted that the approach and
parameters we think are best is probably not, as is evident by multiple false assumptions covered
in the report. Therefore, trying out as many methods as possible is worth it. I also learned that
considering things like training and testing time can become a major hurdle, especially with large
datasets and methods like SVM. I also realized the value of cross-validation. Without it I got
significantly different results each time I ran my code, however, the differences between runs
became significantly less when I implemented cross-validation.
