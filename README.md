# deep-learning-challenge

This is my submission for Module 21 Challenge with Berkeley Data Analytics Boot Camp.

Running `charity_deep_learning.ipynb` will give you a notebook that uses a Neural Netowrk to create a binary classifier to predict whether applicants will be successful if funded by Alphabet Soup. The model from this notebook will be saved as `AlphabetSoupCharity.h5`.
Running `AlphabetSoupCharity_Optimization.ipynb` will give you a more optimized version of the previous notebook with a higher accuracy. The model from this notebook will be saved as `AlphabetSoupCharity_Optimization.h5`.

## Overview of the analysis:

The purpose of this analysis was to evaluate a Neaural Network to predict whether applicants will be successful if funded by Alphabet Soup. Accuracy in this context is critical for Alphabet Soup when they are looking to assess financial risks and make decisions about approving funding.

## Results:

### Data Preprocessing:
* What variable(s) are the target(s) for your model? `IS_SUCCESSFUL` is the target variable.
* What variable(s) are the features for your model? `NAME`,`APPLICATION_TYPE`,`AFFILIATION`,`CLASSIFICATION`,`USE_CASE`,`ORGANIZATION`,`STATUS`,`INCOME_AMT`,`SPECIAL_CONSIDERATIONS`,`ASK_AMT`,`IS_SUCCESSFUL` are all used as features in building the model.
* What variable(s) should be removed from the input data because they are neither targets nor features? `EIN` is the only varibale not used in the model.

### Compiling, Training, and Evaluating the Model:
* How many neurons, layers, and activation functions did you select for your neural network model, and why?
    * I used a total of 4 layers (1 input, 2 hidden, 1 output)
    * 16(input layer), 8(first hidden), 4(second hidden), 1(output layer) were the number of neurons used
    * I used `relu` for the input layers and the 2 hidden layer, and `sigmoid` for the ouput layer activation functions
    All of these were chosen after testing with different layer amounts and neuron amounts
* Were you able to achieve the target model performance?
    * Starting performance after final layer, neurons, and activation function chocies (`.728`):
        ![First Change](https://github.com/YannisPapa/deep-learning-challenge/blob/main/images/base_file.PNG?raw=true)
    * Performance after reducing amount of buckets for `INCOME_AMT` by puting ones with less than a certain amount into 'Other' (`.729`):
        ![Second Change](images\after_income_buckets.PNG)
    * Performance after reducing amount of buckets for `NAME` by puting ones with less than a certain amount into 'Other' (`.792`):
        ![Third Change](images\after_income_name_buckets.PNG)
* What steps did you take in your attempts to increase model performance?
    * First i took some time to try different settings for number of layers and neurons and differnt fuction types.
    * Next i tried different bucketing for some of the Features such as `APPLICATION_TYPE`, `CLASSIFICATION`, `INCOME_AMT`, and `ASK_AMT`
    * Finally the last thing that made a big difference was Using the `NAME` feature and bucketing the ones that occured less than 5 times into 'Other'

## Summary:

The results of this analysis demonstrate that neural networks can be effectively used to predict the likelihood of success for applicants funded by Alphabet Soup. Through iterative improvements, including optimizing the number of layers and neurons, refining feature selection, and reducing categorical granularity through bucketing, the model's performance improved significantly.

Despite these enhancements, the final accuracy of the model still has room for improvement. This suggests that while neural networks are powerful, they may not always provide the best solution for this specific classification problem.

To further improve performance, exploring tree-based models like Random Forest or XGBoost could be tried. These models handle structured data well, are better at managing class imbalance, and provide interpretable feature importance, making them a strong alternative to neural networks for this task.
