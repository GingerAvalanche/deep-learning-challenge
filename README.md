# Homework 21 - Deep Learning

## Description

These notebooks detail an attempt to reach 75% predictive accuracy with a neural network. Specifically, the features were used to predict whether or not a charity would be successful. Multiple rounds of both feature tweaking and neural net tuning were used to attempt to reach the accuracy goal. However, it was not reached.

## Analysis

#### Data Preprocessing

  * What variable(s) are the target(s) for your model?

The IS_SUCCESSFUL variable was the target of the model - to have the network predict if a given campaign would be successful

  * What variable(s) are the features for your model?

The features that were eventually used in the model were: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, ORGANIZATION, and INCOME_AMT

  * What variable(s) should be removed from the input data because they are neither targets nor features?

The following features were removed, after it was determined that they had too little impact on the predictive capabilities of the model: USE_CASE, STATUS, SPECIAL_CONSIDERATIONS, ASK_AMT

#### Compiling, Training, and Evaluating the Model

  * How many neurons, layers, and activation functions did you select for your neural network model, and why?

I selected 2 hidden layers (80 relu neurons, 30 tanh neurons) and 1 output layer (1 sigmoid neuron). This was the very first network I had tried. I also did two separate waves of network tuning that showed other configurations were more effective. However, I didn't use those for two reasons: 1) the increase in effectiveness was often eclipsed by random chance on subsequent trainings of the same networks, and 2) often, subsequent trainings would enter error states where accuracy would tank, for reasons unknown.

  * Were you able to achieve the target model performance?

I was not able to achieve 75% target accuracy.

  * What steps did you take in your attempts to increase model performance?

For the feature sets, I used the itertools library to compare every permutation of feature columns that existed (some 510 combinations), and then also compared 24 combinations of outlier-reduction classifications for the remaining features. I am confident that I chose the most effective features for the network that I could have, with the results I obtained.

For the neural network tuning, I tuned twice. The first tuning was before testing the features, in which I had keras-tuner test up to 30 neurons per layer, with up to 5 layers, with 5 possible activation functions. After not achieving the desired results even after tweaking the feature sets, I tuned again, this time testing up to 128 neurons per layer, with up to 5 layers, with all 14 possible activation functions and all 11 possible optimizers. The most accurate results were not significantly more accurate than my original model, so I ended up discarding the results of both tuning runs due to consistency concerns.

#### Summary

This model should be able to accurately predict the outcome of an Alphabet Soup charity campaign with almost 75% certainty.

A logistic regression model could also be used to answer the same question, seeing as the two share the same basic premise: split a dataset into two parts (predictive parameters/features and classification parameters/targets) and use the former to predict the latter.

### Notes

I was never able to figure out why models that worked during tuning would give 700%+ loss rates and low accuracy rates during subsequent trainings with the same hyperparameters. The only thing I noticed was that it never seemed to happen with the Adam optimizer.

### Source

No code was copied from external sources.
