# Ensemble Learning

Stacking is an ensemble learning technique that uses predictions from multiple models (for example decision tree, knn or svm) to build a new model. This model is used for making predictions on the test set. 

Blending follows the same approach as stacking but uses only a holdout (validation) set from the train set to make predictions. In other words, unlike stacking, the predictions are made on the holdout set only. The holdout set and the predictions are used to build a model which is run on the test set. 

Bootstrapping is a sampling technique in which we create subsets of observations from the original dataset, with replacement. The size of the subsets is the same as the size of the original set.
Bagging (or Bootstrap Aggregating) technique uses these subsets (bags) to get a fair idea of the distribution (complete set). The size of subsets created for bagging may be less than the original set.
Boosting is a sequential process, where each subsequent model attempts to correct the errors of the previous model. The succeeding models are dependent on the previous model.

Bagging algorithms:
* Bagging meta-estimator 
* Random forest 
Boosting algorithms:
* AdaBoost 
* GBM 
* XGBM 
* Light GBM 
* CatBoost 
Looking at it step-by-step, this is what a random forest model does:
1. Random subsets are created from the original dataset (bootstrapping). 
2. At each node in the decision tree, only a random set of features are considered to decide the best split. 
3. A decision tree model is fitted on each of the subsets. 
4. The final prediction is calculated by averaging the predictions from all decision trees. 
To sum up, Random forest randomly selects data points and features, and builds multiple trees (Forest) .

Adaptive boosting or AdaBoost is one of the simplest boosting algorithms. Usually, decision trees are used for modelling. Multiple sequential models are created, each correcting the errors from the last model. AdaBoost assigns weights to the observations which are incorrectly predicted and the subsequent model works to predict these values correctly.


Gradient Boosting or GBM is another ensemble machine learning algorithm that works for both regression and classification problems. GBM uses the boosting technique, combining a number of weak learners to form a strong learner. Regression trees used as a base learner, each subsequent tree in series is built on the errors calculated by the previous tree.

￼

XGBoost (extreme Gradient Boosting) is an advanced implementation of the gradient boosting algorithm. XGBoost has proved to be a highly effective ML algorithm, extensively used in machine learning competitions and hackathons. XGBoost has high predictive power and is almost 10 times faster than the other gradient boosting techniques. It also includes a variety of regularization which reduces overfitting and improves overall performance. Hence it is also known as ‘regularized boosting‘ technique.


Let us see how XGBoost is comparatively better than other techniques:
1. Regularization: 
    * Standard GBM implementation has no regularisation like XGBoost. 
    * Thus XGBoost also helps to reduce overfitting. 
2. Parallel Processing: 
    * XGBoost implements parallel processing and is faster than GBM . 
    * XGBoost also supports implementation on Hadoop. 
3. High Flexibility: 
    * XGBoost allows users to define custom optimization objectives and evaluation criteria adding a whole new dimension to the model. 
4. Handling Missing Values: 
    * XGBoost has an in-built routine to handle missing values. 
5. Tree Pruning: 
    * XGBoost makes splits up to the max_depth specified and then starts pruning the tree backwards and removes splits beyond which there is no positive gain. 
6. Built-in Cross-Validation: 
    * XGBoost allows a user to run a cross-validation at each iteration of the boosting process and thus it is easy to get the exact optimum number of boosting iterations in a single run. 
 Light GBM beats all the other algorithms when the dataset is extremely large.LightGBM is a gradient boosting framework that uses tree-based algorithms and follows leaf-wise approach while other algorithms work in a level-wise approach pattern.

