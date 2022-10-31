# Neural_Network_Charity_Analysis

## Overview of the analysis: 
The goal of this analysis is to develop a model that helps Alphabet Soup evaluate whether applicants for charitable donations will succeed in their cause should Alphabet Soup fund them. To support the analysis, Alphabet Soup has provided a large dataset with metadata about previously funded organizations. Using this dataset, we will develop a Neural Networks Machine Learning algorithm to predict successful applications. Python's TensorFlow library will be used to create a binary classifier that is capable of predicting whether applicants will be successful if funded.

## Results:

### Data Preprocessing
#### What variable(s) are considered the target(s) for your model?
"IS_SUCCESSFUL" is the target for this model. Target (or dependent) variables represent the outcome variable of interest and is the variable we are using to train this model.

#### What variable(s) are considered to be the features for your model?
Feature variables include input variables to our model. These include all columns except those that we dropped ("EIN" and "NAME"). Specifically, the features of this model include APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT.

#### What variable(s) are neither targets nor features, and should be removed from the input data?
Variables to be removed are those noted above: EIN and NAME. We suspect that these variables do not add any predictive value to the model and thus, should be removed. These variables typically have unique values and result in noiser data.

### Compiling, Training, and Evaluating the Model

#### How many neurons, layers, and activation functions did you select for your neural network model, and why?
- I used 200 neurons for the first layer because it is meant to be double the amount of input features which was 100 rows for this dataset. For the second layer, I used 90 neurons.
- For this model, I used 2 hidden layers as the addition of a 3rd layer didn't improve the model significantly. Additional hidden layers can increase the risk of overfitting the training data.
- Relu was the activation function of choice as it had the best accuracy for this model. For the loss function, I used binary crossentropy because it's used for binary classificaiton models.
- I trained the refined model using 500 epochs (original was 100).

#### Were you able to achieve the target model performance?
Yes, the model exceeded the target performance goal of 75%. This was an improvement over the original optimization score of 72.6% (initial model). The refined model increased accuracy to 76.1%. 

#### Initial Model
![image](Images\model1.jpg)

#### Refined Model
![image](Images\model2.jpg)

#### What steps did you take to try and increase model performance?
To improve performance, I decided to bin the "ASK_AMT" values and brought back the "NAME' column, binning them as well. There were many orgs with multiple applications, so binning by NAMES made sense for categorizing. I also increased the number of epochs from 100 to 500 as well as the number of neurons for each layer.

### Summary: 

The accuracy score and model loss tell us how well the model works. The refined model achieved the target accuracy goal but the loss is 62% indicating that the model has a high chance of failing. The original model is on par with probabability of failure at 56% (accuracy = 72.6%).

I would recommend evaluating other models before selecting one to advise Alphabet Soup on what applications to fund. The high probabability that the model fails is concerning. It could be that the input data does not provide adequate predictors for success. It is worth evaluating this data in simpler supervised machine learning models before making this determination. I would recommend logistic regression models for comparison including the Random Forest model. In addition, I would seek additional input variables to determine if they support the model in predicting success. 