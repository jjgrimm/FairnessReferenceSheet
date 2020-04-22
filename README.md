# Multiple Notions of Fairness 

Currently in machine learning, researchers have been attempting to develop methods that allow a model to consider multiple perspectives on what is considered "fair" for a given situation.  Much work has been done to consider how to capture and leverage perceptions of fairness from many individuals, often with very different strategies. We have developed this document to serve as a reference sheet to help anyone understand the current common terminology and concepts used in this research. This document is a living document, with our goal to continue developing it alongside developing research. 

## Defining Fairness

The first concept that is critical to understand is **fairness**. Generally an outcome is considered fair if it does not contain bias. The multiple definitions of bias are discussed below to avoid confusion, but here we are simply looking to avoid a disproportionate outcome.  Outcomes can be considered disproportionate either directly among individuals, or across individuals broken into groups based on some characteristic. Thus we will define separate terminology for **individual fairness** and **group fairness**, including the kinds of outcomes that are seen in both. In order to understand may of these terms, we must also define some necessary statistical terminology. 

## Definitions of Bias

**Bias** - This occurs in a dataset when a collection of input variable values occur more than others. It is a measure of how far a given dataset is away from a truly random dataset. This is necessary for machine learning to work and generate accurate predictions.

**Colloquial Bias** - Colloquially, when somebody states that an outcome is biased they generally mean that it is not fair, and this is what we are hoping to avoid by considering multiple notions of fairness.

**Inductive / Learning Bias** - Another notion of bias that is necessary for machine learning to work.  It is the set of assumptions used in supervised learning to help predict the output for any unseen input. There are many different ways to introduce this, one method is to use an attribute or set of characteristics to associate an unseen input with similar and known inputs. The unseen input can then be classified similarly to the known inputs. 

**Statistical Bias** - This occurs when the binary classifier outcome does not properly reflect the distribution of the underlying target variable. For example, consider a model that classifies men and women to be either Republican or Democrat based on their social media data. If 30 percent of the individuals are women, then that distribution should reflect in the classifications and both the classified Republicans and Democrats should still have about 30 percent women. Otherwise, there exists statistical bias. 

## Statistic Terminology

**Accuracy** - The probability that a point is correctly classified, found by adding the True Negative Rate with the True Positive Rate. 

**False Negative Rate (FNR)** - This is the probability that a positive point is classified incorrectly. It is the ratio of positive points classified as negative over the total number of positive points. 

**False Positive Rate (FPR)** - This is the probability that a negative point is classified incorrectly. It is the ratio of negative points classified as positive over the total number of negative points. 

**Negative Predictive Value (NPV)** - This is the probability that a negative classification is accurate, defined as a ratio of the number of correctly classified negative points over the total number of points classified as negative. 

**Positive Predictive Value (PPV)** - This is the probability that a positive classification is accurate, defined as a ratio of the number of correctly classified positive points over the total number of points classified as positive. 

**Sensitivity / True Positive Rate (TPR)** - This is the probability that a positive point is classified correctly, or mathematically the ratio of correctly classified positive points over the total number of positive points (including those classified as negative).

**Specificity / True Negative Rate (TNR)** - This is the probability that a negative point is classified correctly, or mathematically the ratio of correctly classified negative points over the total number of negative points (including those classified as positive).

**Well-Calibrated** - A model that appropriately reflects the distribution of its target variable, or when the different groups have the same **PPV**.

## Machine Learning (ML) Specific Terminology

**Binary Classifier** - While there are many types of classifiers and methods for developing them, a binary classifier simply takes an input and decides if that input should receive a positive or negative classification based on some predefined rules.  

**Supervised Learning** - The task of learning a function that maps an input to an output based on given example input-output pairings. The function is learned from a created training dataset and then evaluated on a different testing dataset.


## Group Fairness Concepts and Terms

**Demographic Parity** - A model of group fairness has demographic parity if the difference in **TPR** among different demographics is less than a chosen threshold (accounting for expected error).

**Disparate Impact** - A form of systematic discrimination that adversely affects a **protected class**.
 
**Equalized Odds** - Also known as separation or positive rate parity, can be used when the classifier is unknown. This states that the model should accomplish both **TPP** and **FPP**. 

 **False Positive Parity (TPP)** - This exists across groups if the groups have equal **FPRs**. 

**Group Fairness** - Ensure that different groups (generally based on their protected attribute) are treated equally based on any number of chosen notions of fairness (such as demographic parity). 

**Protected Class** - A protected class is any group of individuals that are legally protected by the same characteristic, including race, religion, age, sex and more.  

**Statistical Parity** - This exists when the accuracy of the binary classifier is equal across groups. The specifics of how the accuracy is measured may change based on the real world problem, as the consequences of an inaccurate classification may not always be equal - sometimes a false positive may carry larger consequences than a false negative. 
 
>**Note**: This is one place where it becomes obvious why multiple notions of fairness should be considered. Statistical parity can be defined as a model being well calibrated, or with parity across false or true positives (TPP and FPP). However, it is impossible for a model to be well calibrated and maintain TPP and FPP, unless the fraction of positives to the total number of points is the same in all groups. Since this is rarely the case, researchers can just choose to define their model as fair based on whatever one notion is convenient in that case. 

 **True Positive Parity (TPP)** - This exists across groups if the groups have equal **TPRs**. 


## Individual Fairness Concepts and Terms


**Annotator / Judge** - An individual responsible for deciding if it would be unfair to treat the individuals substantially differently based on their given features. Often these judges are represented in a model as a set of pairs of feature vectors, with each pair in their set representing two individuals they believe should not be treated differently because of their similar features. This allows the model to consider multiple notions of fairness across individuals.  

**Feature Vector** - Rather than directly comparing individuals, somebody judging if two people are similar should be given general features of the individuals. A model should not be making any decisions based on a legally protected attribute, so the target features of an individual should be taken and considered on there own. To accomplish this goal, most mathematical models represent individuals as a vector of relevant/necessary features and simply give judges these feature vectors. 

**Individual Fairness** - Similar individuals are treated similarly. This requires a method for deciding which individuals are similar, generally by letting judges complete pairwise comparisons on a set of feature vectors.  

**Protected Attribute** - A protected attribute is any attribute of an individual that is legally protected by United States federal anti-discrimination law. This includes race, religion, national origin, age, sex, and more. 

