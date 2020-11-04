# Heart-disease


Abstract:  This dataset is a human heart disease database similar to a database already present in the repository (Heart Disease databases) but in a slightly different form.
I have to find wheather a patient have heart problem or not.To classify this problem I use five classifier.





# Classifier 1: Naïve bayes

Scheme:       weka.classifiers.bayes.NaiveBayes 
Relation:     heart
Instances:    270
Attributes:   14
Test mode:    270-fold cross-validation



Correctly Classified Instances         230               85.1852 %
Incorrectly Classified Instances        40               14.8148 %
Kappa statistic                          0.698 
Mean absolute error                      0.1811
Root mean squared error                  0.3584
Relative absolute error                 36.532  %
Root relative squared error             71.8673 %
Total Number of Instances              270     



=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0.893    0.200    0.848      0.893    0.870      0.699    0.899     0.914     1
                 0.800    0.107    0.857      0.800    0.828      0.699    0.899     0.880     2
Weighted Avg.    0.852    0.159    0.852      0.852    0.851      0.699    0.899     0.899     




=== Confusion Matrix ===

   a   b   <-- classified as
 134  16 |   a = 1  
  24  96 |   b = 2




# Classifier 2: lazy_IBk

Scheme:       weka.classifiers.lazy.IBk -K 1 -W 0 -A "weka.core.neighboursearch.LinearNNSearch -A \"weka.core.EuclideanDistance -R first-last\""

Relation:     heart
Instances:    270
Attributes:   14
Test mode:    270-fold cross-validation



Correctly Classified Instances         202               74.8148 %
Incorrectly Classified Instances        68               25.1852 %
Kappa statistic                          0.4917
Mean absolute error                      0.2537
Root mean squared error                  0.5   
Relative absolute error                 51.1773 %
Root relative squared error            100.2544 %
Total Number of Instances              270     




=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0.760    0.267    0.781      0.760    0.770      0.492    0.747     0.727     1
                 0.733    0.240    0.710      0.733    0.721      0.492    0.747     0.639     2
Weighted Avg.    0.748    0.255    0.749      0.748    0.749      0.492    0.747     0.688     




=== Confusion Matrix ===

   a   b   <-- classified as
 114  36 |   a = 1
  32  88 |   b = 2








# Classifier 3:Trees_j48


Scheme:  weka.classifiers.trees.J48 -C 0.25 -M 2
Relation:     heart
Instances:    270
Attributes:   14
Test mode:    270-fold cross-validation
Number of Leaves  : 	22
Size of the tree : 	38


Correctly Classified Instances         217               80.3704 %
Incorrectly Classified Instances        53               19.6296 %
Kappa statistic                          0.6008
Mean absolute error                      0.2537
Root mean squared error                  0.4294
Relative absolute error                 51.1892 %
Root relative squared error             86.092  %
Total Number of Instances              270     



=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0.840    0.242    0.813      0.840    0.826      0.601    0.736     0.769     1
                 0.758    0.160    0.791      0.758    0.774      0.601    0.736     0.703     2
Weighted Avg.    0.804    0.205    0.803      0.804    0.803      0.601    0.736     0.740     



=== Confusion Matrix ===

   a   b   <-- classified as
 126  24 |   a = 1
  29  91 |   b = 2











# Classifier 4: Trees_RandomForest


Scheme: weka.classifiers.trees.RandomForest -P 100 -I 100 -num-slots 1 -K 0 -M 1.0 -V 0.001 -S 1
Relation:     heart
Instances:    270
Attributes:   14
Test mode:    270-fold cross-validation



=== Summary ===

Correctly Classified Instances         220               81.4815 %
Incorrectly Classified Instances        50               18.5185 %
Kappa statistic                          0.6244
Mean absolute error                      0.2718
Root mean squared error                  0.3622
Relative absolute error                 54.8371 %
Root relative squared error             72.6146 %
Total Number of Instances              270     




=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0.840    0.217    0.829      0.840    0.834      0.624    0.894     0.908     1
                 0.783    0.160    0.797      0.783    0.790      0.624    0.894     0.878     2
Weighted Avg.    0.815    0.191    0.815      0.815    0.815      0.624    0.894     0.895     





=== Confusion Matrix ===

   a   b   <-- classified as
 126  24 |   a = 1
  26  94 |   b = 2






# Classifier 5: Meta_FilteredClassifier

Scheme:  weka.classifiers.meta.FilteredClassifier -F "weka.filters.supervised.attribute.Discretize -R first-last -precision 6" -W weka.classifiers.trees.J48 -- -C 0.25 -M 2


Relation:     heart
Instances:    270
Attributes:   14
Test mode:    270-fold cross-validation



Correctly Classified Instances         212               78.5185 %
Incorrectly Classified Instances        58               21.4815 %
Kappa statistic                          0.5628
Mean absolute error                      0.2958
Root mean squared error                  0.4223
Relative absolute error                 59.6777 %
Root relative squared error             84.6748 %
Total Number of Instances              270     



=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0.827    0.267    0.795      0.827    0.810      0.563    0.742     0.779     1
                 0.733    0.173    0.772      0.733    0.752      0.563    0.742     0.769     2
Weighted Avg.    0.785    0.225    0.785      0.785    0.785      0.563    0.742     0.775     




=== Confusion Matrix ===

   a   b   <-- classified as
 124  26 |   a = 1
  32  88 |   b = 2







# Classifier 6: Rules_PART

Scheme:       weka.classifiers.rules.PART -M 2 -C 0.25 -Q 1
Relation:     heart
Instances:    270
Attributes:   14
Test mode:    270-fold cross-validation
Number of Rules  : 	19



Correctly Classified Instances         218               80.7407 %
Incorrectly Classified Instances        52               19.2593 %
Kappa statistic                          0.6113
Mean absolute error                      0.2193
Root mean squared error                  0.4311
Relative absolute error                 44.2447 %
Root relative squared error             86.4369 %
Total Number of Instances              270     




=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0.813    0.200    0.836      0.813    0.824      0.612    0.736     0.744     1
                 0.800    0.187    0.774      0.800    0.787      0.612    0.736     0.669     2
Weighted Avg.    0.807    0.194    0.808      0.807    0.808      0.612    0.736     0.711     





=== Confusion Matrix ===

   a   b   <-- classified as
 122  28 |   a = 1
  24  96 |   b = 2








# Summary:

After implementing 6 classifier ,I have seen that  classifier-1: naïve bayes classifier correctly classify 230 instances out of 270  instances with 85.1852 % accuracy.

