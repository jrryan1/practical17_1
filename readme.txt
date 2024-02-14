Dataset:
Our dataset comes from the UCI Machine Learning repository link. The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns.

Problem:
Portugese Banking Instituation ran 17 campaigns that occurred between May 2008 and November 2010, corresponding to a total of 79354 contacts. To optimize future campaigns, they are looking for a way to predict who will respond positively to the campaigns.

Analysis:
Initial analysis with Linear Regression was poor with less than 10% accuracy on the training data.

Running basic analysis with Logistic Regression, we saw an increase to ~11% for both testing and training data.

Further comparison between KNeighbors, LogisticRegresion, SVC, and DecisionTreeClassifier had higher accurracy (see table 1).  However, deeper analysis showed that only KNeighbors and DecisionTree had predicted any positive responses. 

See Graphs: 
"dt matrix.png" - Showing confusion matrix for the decision tree with only 98 true positive and 1055 false negative.  

"logr matrix.png" and "svc matrix.png" - Showing confusion matrix for the logistic regression and SVM (respectively) with no participants marked as likely to respond.

"knn matrix.png" - Showing confusion matrix for the KNeighbors classifier with 76 true positive and 1077 false negatives.  This does have the least false positive (179 vs DT 338)


Table 1

Model		Training Time	Train Accuracy	Test Accuracy	
--------------------------------------------------------------
SVM		15.441671	0.887119	0.888026

Logistic 
Regression	0.897097	0.887119	0.888026

KNN		0.031723	0.889126	0.878023

Decision Tree	0.109993	0.916966	0.864718


Additional data manipulation seemed to decrease the number of true positive moving that prediction closer to 0. 


Best solution:
After multiple data manipulation and evaluating the different options, KNeighbors with a simple data scaler was able to achieve nearly 50% True Positive.  However, this also increased the False Positive to nearly 50% of the data provided.

See graph: "knn pred revised data.png" for the confusion matrix on the final solution. 

Unfortunately with the scaled data and KNN approach, this is not easy to describe characteristics for a human to model for manual selection. With Logistic Regression, we did see some modeling with scoring towards individuals with more time, retired and students vs working professionals. More data could improve this evaluation. Interestingly, removing data on house ownership removed almost all TP values. This information could be used with a larger model to determine if there is a relationship between home ownership, age and response to these offers.


Final Evaluation:
The data was not conducive to a clear guidelines. Best case was a 50% response. We recommend using marketing experts to tailor programs based on age, home ownership, and existing bank assest and then evaluate the effectiveness of specific approaches on each of these groups as separate co-horts and determine if there are models that can predict responses within the subgroups.