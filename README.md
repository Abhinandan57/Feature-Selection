# Feature-Selection
- Whenever the data is collected, it is not always collected in a very clean manner. Sometimes there will be human errors, duplicate data present in multiple features, correlated features etc. Hence feature selection plays a important role as not all the features are important. We have to select the important features.

## What is the purpose of Feature Selection?
- Many learning algorithms perform poorly on high-dimensional data. This is known as the __Curse of Dimensionality__.
- There are other reasons we may wish to reduce the number of features including:  
1. Reducing computational cost  
2. Reducing the cost associated with data collection  
3. Improving Interpretability (having just few feaures makes more sense than couple of different features)

# Feature Selection Techniques

__1. Univariate Selection__  

__2. Feature Importance__  
- This technique gives you a score for each feature of your data. Higher the score, more relevant the feature is.

__3. Correlation__  
- If your independent feature values are increasing along with your dependent feature values, we call it as Positive Correlation.
- If your independent feature values are decreasing along with your dependent feature values, we call it as Negative Correlation.
- If your independent feature values are increasing and your dependent feature values are decreasing or vice-versa, we call it there is no Correlation.
- If an independent feature is highly correlated with dependent feature we need not remove those kind of features because those features can play a very important role when we train our machine learning model. But if we have independent features lets say 3 independent features, and they are highly correlated with each other i.e. more than 90% then from these 3 we will use only 1 feature. Because these 3 will behave like duplicate features. In case of duplicate features we need not take all the features, we take either one of those features. This way we can remove features.
- All the functionalities that we will apply w.r.t correlation on the training dataset, will do the similar things on the test dataset as well. Suppose in the training dataset we have 4 features which are higly correlated, then we will remove 3 features directly from the training dataset and we will not the correlation retest again on the test dataset. We will also remove those features from testing dataset.
- We will remove the correlated features but one thing to keep in mind that the correlated features should not be removed w.r.t dependent features. We will try to only remove the correlated features w.r.t independent features. If both the features are highly correlated i.e. 80% or 90% correlated with each other then we can drop one of these features. Because both the features are doing the same task. In correlation we only drop those features that re highly correlated.
- Threshold value need not be always 80%, sometimes it can be around 90%. The domain expert person can actually say the value of this threshold.

__4. Information Gain (Mutual Information in Classification)__  
-Mutual information between two random variables is a non-negative value, which measures the dependency between the variables. It is equal to zero if and only if two random variables are independent, and higher values mean higher dependency.
- Mutual Information (MI) estimate mutual information for a discrete target variable.
- The function relies on nonparametric methods based on entropy estimation from k-nearest neighbors distances.
- A quantity called mmutual information measures the amount of information one can obtain from one random variable given other.
- This technique is applied to a __Classification__ problem.
- The mutual information between two random variables x and y can be stated formally as follows:  
__I(x ; y) = H(x) - H(x | y) where I(x ; y) is the mutual information for x and y, H(x) is the entropy for x and H(x | y) is the conditional entropy for x given y. The result has the units of bits.__
- You will never get a negative value while using mutual_info_classif(). You will either get 0 or positive number within 1.
- If you are getting a very very high number, that particular feature is the best/most important feature or is the most dependent feature or you can say the dependency on the target is too much.
- __Difference Between Information Gain and Mutual Information Gain :__  
I(x ; y) = H(x) - H(x | y) and IG(S, a) = H(S) - H(S | a)  
As such, mutual information gain is sometimes used as a synonym for information gain. Technically, they calculate the same quantity if applied to the same data.
- Information Gain technique is used in case of continuous target variable.

__5. Dropping constant features__  
- In this technique we will be removing the features which have constant features, which are actually not important for solving the problem statement.

__6. Fisher Score - Chisquare Test__  
- We compute chi-squared stats between each non-negative feature and class (target feature). Non-negative feature means features that do not have any -ve values.
- This score should be used to evaluate categorical variables in a classification task.
- This score can be used to select the n_features with the highest values for the test chi-squared statistic from x, which must contain only non-negative features such as booleans or frequencies (e.g., term counts in document classification), relative to the classes.
