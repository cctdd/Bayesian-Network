# Bayesian-Network
A model of diabetes prediction using symptom (An application of Bayesian Network) 
The bayesian network model was applied to a dataset that contain yes/no values to the symptoms of diabetes and gender. The bayesian network was then tested on various situations and at the end the efficiency of the model was calculated.
![DALL·E 2023-11-11 13 50 22 - A conceptual illustration of a Bayesian network for diabetes prediction  The network consists of various nodes representing common symptoms of diabete](https://github.com/cctdd/Bayesian-Network/assets/122665014/5944fb60-d2b1-4494-94ce-9497a5b9c886)

## Introduction ##
In this project, for the predictive analysis for prevention, the Bayesian Network model was adopted. The diabetes data used was obtained from the UC Irvine repository and it containes 521 observations and 17 features. The data was reprocessed such that it could be used for the model and some features were also removed for simplicity. The Bayesian Network model was then created for the selected features. At the end, the model was tested by creating some situations, which were predicted using the Bayesian Network. For this new cases, the conditional probability was calculated, considering the network design and configuration made for the variables and their relationships child-parent.
## Data Presentation and Filtering ##
The diabetes data used was obtained from the [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/529/early+stage+diabetes+risk+prediction+dataset) and it containes 521 observations and 17 features.
The dataset is composed of 16 features and the classification (expressed by the columns), and 521 instances (number of entries). So, it is a multivariate dataset with 1 integer feature and 15 binary features. Each feature is associated with a certain symptom/characteristic of the individual:
+ Age (integer) - age of the individual
+ Gender (binary) - gender of the individual
+ Polyuria (binary) - production of excessive urine
+ Polydipsia (binary) - excessive thirst
+ Sudden Weight Loss (binary) - individual has had a drastic drop of his weight
+ Weakness (binary) - individual feels weak
+ Polyphagia (binary) - feeling of extreme hunger
+ Gential Thrush (binary) - gential yeast infection
+ Visual Blurring (binary) - diminished visual capacity
+ Itching (binary) - individual feels the necessity to ich
+ Irritability (binary) - individual has irritated skin
+ Delayed Healing (binary) - individual takes more time than others to heal a wound
+ Partial Paresis (binary) - weakned muscle groups
+ Muscle Stiffness (binary) - tighten muscles or muscles groups
+ Alopecia (binary) - hair loss
+ Obesity (binary) - individual is overwieghted
+ Class (binary) - will have diabetes
Following this, null values was investigated and there was none.

## Exploratory Analysis ##
In order to reduce the complexity of the probelem, we did a correlation analysis between all the dataset and most especially with the Class column. From the result of this analysis, we selected values with more importance due to thier correlation values in the correlation table below:
![correlation](https://github.com/cctdd/Bayesian-Network/assets/122665014/942c7b8c-a136-4c1d-893e-a0b147639c93)

Hence the variables selected are those that have the highest correlation with the Class column and are : 
+ Gender
+ Polyuria
+ Polydipsia
+ Weight Loss
+ Polyphagia
+ Partial Paresis
+ Obesity

## Bayesian Network Design ##
The selected variables were used to make a bayesian network design ![BayesianNetworkDesign](https://github.com/cctdd/Bayesian-Network/assets/122665014/82b22af2-2ae6-498f-8679-a149996c209a)
as shown below: 
As observed the network was generated with this understanding: 
+ Since Gender is random, a male or a female may have Diabetes
+ Polyuria is the condition that makes a person excrete abnormal volumes of urine. Polydipsia is a condition where someone posses an obnormal great thirst. Weightloss refers to the reduction of the total body mass due to a mean loss of fluid, body fat, or lean mass. Therefore in the SECTION A of the image below;
  ![NEW](https://github.com/cctdd/Bayesian-Network/assets/122665014/c948edb1-fc23-40be-820b-6ea32341d965)
excess excretion of urine can cause both weight loss and great thirst.
+ Partial Paresis or partial paralysis, refers to the incomplete loss of muscle function or weakness in a part of the body as his can also lead to weight loss, we made the dependence.
+ Polyphagia is the medical term for excessive or extreme hunger, and this can lead to Obesity which is the exterme gain of weight.
+ Finally, Obesity, Polydipsis, WeightLoss and Gender can be directly associated to Diabetes.


