# Bayesian-Network
A model of diabetes prediction using symptom (An application of Bayesian Network). 
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

## Probability Distribution ##
After having the network structure, and having formated the data, the next step is to calculate the probabilities of occurrence for each variable (Categorical variables and Conditional Categorical variables), taking into account the bayesian network scheme and the relations between a variable and its parents. For an independet event, the probability of it's occurence is given by:
$$P(A) = {A  occurences \over Total Number of Occurences } $$
The conditional probability formula is dependent on how many "parents" a certain variable has. The general formula that represents the conditional probability is the following:
$$P(A|B) = {P(A) \bigcap P(B) \over P(B) }$$
Which can be simply read as the probabiity of A happening given that B occured. Therefore in the A section of the network the probability of Polyuria is an independent probability obtianed by obtaining the total number of polyuria =1 and polyuria =0 and taking their ration to the total number of Polyuria observation. However the probabiliy of Polydipsia is dependent on Polyuria therefore the Polydispia probability is obtained for fourcases. This 4 cases are obtained in pair for the two possible cases of Polyuria:
1. Case Polyuria = 1: The probability of polydipsia was obtanined using the conditional probability formula, with P(B) = probability that polyuria is 1 and P(A) being the two cases for polydipsia = 1 and polydipsia =0
2. Case Polyuria = 0: The probabilty of polydipsia in this case was calculated the same way wth the exception that here, B = probability that Polyuria = 0

The same method was followed throughout to obtain the ConditionalCategorical Matrix used in computing the Bayesian Network.

## Bayesian Model ##
The Bayesian Network (BN) model was developed by following the Bayesian Network graph shown above. This extract of the code:BayesianNetwork([gender,polyuria,partial_paresis,polyphagia,polydipsia,obesity,weight_loss,diabetes],
                          [(polyuria,polydipsia),(polyuria,weight_loss),(partial_paresis,weight_loss),(polyphagia,obesity),(obesity,diabetes),(polydipsia,diabetes),(weight_loss,diabetes),(gender,diabetes)]) can be explain as follows:
+ The first inner group shows all the states that are considered.
+ The second group shows the edges which is the connection between each feature and another which essentially creates the graph.

After obtaining the Model and the state, the possible choices for each of the states was investigated. Since we are trying to investigate the situations using the model, we have three possible choices for each states:
+ 1: Meaning the state is present
+ 0: Meaning the state is not present
+ ?: Meaning the state is to be predicted

## Model Application to Examples ##
A Bayesian model has the ability to predict not only the final classification (in this case the presence or absence of diabetes), but also other variables of the model. In the cases above the gender was also predicted apart from the diabetes.
+ Example 1: 
It is possible to observe that most of the positive correlated variables with the classification are 1, the gender (which has a negative correlation) is also 1, lowering the probability of the having diabetes. The obtained result indicates that based on the known variables, the individual will have diabetes with a probability of 0.93.
In the second example, the situation is almost the same as the first one, except for the gender that is 0 in this case, which increases the probability of having diabetes and, as it is poissble to see, the individual will certainly have diabetes with a probability of 1.
The last example shows that it is possible to predict other variables apart from the diabetes classification; the gender was predicted, with a 0.63 probability of being 1 (which means to be a male); meanwhile the probability of not having diabetes was 0.68
Another interesting example, which also is capable of evaluating the created Bayesian Network, is to pass to the model the variables of the original dataset without the label (the diabetes classification) and check the accuracy of the model. Creating the situations using a cycle and retrieving the variables gender, polyuria, partial_paresis, polyphagia, polydipsia, obesity, weight_loss, the predictions were obtained and compared with the labels.
+ Example 2:
In the second example, the objective was to test the flexibility of the model, by trying to input values of the variables that somehow contradict themselves. The choosen example was to input values of 1 for the variables that are positivly correlated with the presence of diabetes, however, pass the classification as 0. This contradicts the model architecture, leading to a failure in predicting the probability of the gender, being male or female. As seen from the code output the probability values are NaN for this case.

As observed, the accuracy of the Bayesian Network model as quite low, as its value was only around 65%. This was somehow expected, as some of the original variables were discarded to create the model, and the fact that the Bayesian Network does not pass through the conditionality between variables (child is only dependent on the parents), which is not true in real cases. These two factors could have possibly contributed to the low accuracy of the model.

## Pros and Cons ##
Pros: 
+ Bayesian Networks provide a natural framework for probabilistic reasoning, allowing not only for point estimates but also probability distributions, which can be essential in assessing diabetes risk and uncertainty.
+ Bayesian Networks can aid in automated feature selection, helping researchers identify the most relevant factors affecting diabetes outcomes.
+ These networks can be used to infer causality between variables, which is crucial in understanding the mechanisms and drivers of diabetes and its complications.

Cons:
+ Complex networks with many variables can become computationally intensive, making them less scalable for some applications.
+ Bayesian Networks assume conditional independence between variables given their parent nodes, which may not always hold in real-world healthcare data
+ As Bayesian Networks become more complex, there is a risk of overfitting to the training data, particularly if there is limited data available.

## Future Improvements ##
To elevate the effectiveness of the designed Bayesian Network for the diabetes diagnosis, a few improvements can be done. First, the expansion of the dataset, both in terms of quantity and diversity, as more data empowers the model to learn data patterns and relationships, ultimately increasing the accuracy. Additionally, enhancing the complexity of the Bayesian Network can improve its ability to represent a wider range of diabetes-related factors, capturing numerous potential interactions and dependencies among variables and increasing the performance of the network. Finally, to ensure a reliable assessment of accuracy, the usage of techniques such as k-folds cross-validation, which prevent overfitting problems and offers a realistic estimate of the model's real-world performance.
