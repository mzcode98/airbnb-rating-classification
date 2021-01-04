# AirBnb Ratings Classification

![Alt Text](https://github.com/mzcode98/airbnb-rating-classification/blob/main/images/Screen%20Shot%202021-01-03%20at%205.39.29%20PM.png?raw=True)

##### Matthew Zhang
##### Objective:
Often times AirBnb success is determined by customer experience. In this case, I will be a company analyst looking to help AirBnb hosts enhance overall customer satisfaction by classifying listings into three categories: Subpar(0), Good(1) and Best(2); further, determining which aspects of properties can be improved. Through modeling, I hope to gain valuable insights in order to form strategy and help generate company success.

To illustrate which characteristics of listings are important, I hope to perform feature level analysis to gain further insights into the models and how they behave.

## Overview

Data was used from Inside AirBnb and I chose to explore the Los Angeles data set. The data set included around 31,000 rows and 74 unique columns/features (Beds, communication rating, price, etc.). After cleaning there were around 29,000 rows and 36 distinguishable features. My target was feature engineered and split into 3 classes based on measures of central tendency. The classes are well-balanced, while in the future for imbalanced classes I would carefully consider SMOTE and or Tomek Links.

## Goals
#### 1. Classify property ratings into 3 aforementioned classes.
#### 2. Determine which features have influence on model preditive power. 
#### 3. Create an accurate model with low error that includes important features and can serve as recommendations for hosts to improve within their listings.

### Exploratory Data Analysis
I wanted to emphasize the spread of classes across each predictor and see which ones contained the most variance to help my model. 
To help me understand this, I looked at a variety of different graph types using Seaborn and also engineered dummy variables for my categorical variables.

![Alt Text](https://github.com/mzcode98/airbnb-rating-classification/blob/main/images/Screen%20Shot%202021-01-03%20at%202.40.15%20PM.png?raw=true)
##### This is one of many visualizations that demonstrate the variability within classes for a specific features. We can see that Classes 1 and 2 have more superhost status compared to Class 0. Furthermore, Class 0 has marginally more non-superhosts than Classes 1 and 2.
![Alt Text](https://github.com/mzcode98/airbnb-rating-classification/blob/main/images/Screen%20Shot%202021-01-03%20at%202.41.01%20PM.png?raw=true)
##### Evidently, Class 0 has more availability in the future and is less booked compared to Classes 1 and 2 which have better ratings.

### Intermediate Model: Decision Trees
This was a Decision Tree Classifier, which partitions the data into separate nodes based on information gain until there is a homogenous set that helps classify new points.
Since I am classifying ratings in a ternary classification, I determined my best metric to be the accuracy of the model.
The vanilla received an accuracy of .60 which I was later able to improve to .68 after performing a max_depth and Grid Search Cross Validation and I have a graph and report of what that looks like. We can see the max depth is around 6.
![Alt Text](https://github.com/mzcode98/airbnb-rating-classification/blob/main/images/Screen%20Shot%202021-01-03%20at%203.11.16%20PM.png?raw=true)



## Predictive Modeling
Moving to the Baseline model for my primary algorithm: I used the Random Forest Classifier, which is an ensemble of Decision Trees and combines multiple trees with a unique subset of features to create variance through bootstrapping and subspace sampling.
Despite this, my baseline model overfit with a perfect training set accuracy and .68 testing accuracy, so I had some tuning to do.

FINAL Model: Again to help validate the model, I ran GridSearch, but this time also examining the Out-Of-Bag error rate which is an error for predictions outside of the bootstrapped sample. (sampling with replacement).
I was able to reach a final accuracy of 70% which is improved from the single decision tree and baseline model. 
Interpreting the confusion matrix, the true classes are labeled on the left and the model predicted classes are labeled below. We can see that for Subpar (0) 2,000/2,700 were predicted correctly. For Good(1) 1,600/2,400 were predicted correctly, and for Best(2) 1,500/2,100 were predicted correctly. And for each class, we can say the differences were misclassifications into the other classes. 
![Alt Text](https://github.com/mzcode98/airbnb-rating-classification/blob/main/images/Screen%20Shot%202021-01-03%20at%203.21.50%20PM.png?raw=true)

There is also a visualization of feature importances to the model calculated by information gain. Clearly, the number of reviews was marginally more impactful than the others. 
![Alt Text](https://github.com/mzcode98/airbnb-rating-classification/blob/main/images/Screen%20Shot%202021-01-03%20at%203.21.41%20PM.png?raw=true)


## Next Steps
##### Conclusions: These models effectively classify AirBnb listings into the 3 classes. It is important to note that the model is especially useful because it helps AirBnb as a company understand and predict ratings for listings with not a lot of reviews. If there were already a lot of reviews, we could just use the ratings. But rather than having lots of users having to review the listing, the model can predict potential ratings into these categories. 

### The recommendations I have from feature analysis are: To thoroughly clean properties before customers arrive, Reach a superhost status (which means to have credibility), and improve communication between customer and host. 


##### For future work, I would like to explore different property types and how they influence customer visitations and perform similar analysis on different cities across the globe.
