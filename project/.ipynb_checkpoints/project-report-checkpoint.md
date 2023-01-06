# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Lucia del Valle Ledezma

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?

I realized that if the prediction are negative an error occurs, In order to solve that, I had to set all values to 0.

### What was the top ranked model that performed?
 The top ranked model was WeightedEnsemble_L3

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
First of all I realized that dataset has a datatime feature, as I learned in the clasroom this field ca be splitted.
In the first moment I tried only adding the hour feature, but for "Stand Out Suggestions" I splitted the date in individual parts, hour, day, month and year.
- Ref. Model Deployment Workflow. 8. Data Cleasing and Feature Engeneering : datetime parser

### How much better did your model preform after adding additional features and why do you think that is?
The model improve a lot, its score in kaggle went down to 0.68 aprox. This occurrs because aditional  and more clear information is given to the algorithm,

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
When I tried different hyper parameter, the model performed better, it's score improve to 0.48, maybe because increasement of the learning_rate wich allow the model }
learn quickly and the increase of number epoch in both kind of models.¿

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time in hyperparamter tunning and feature engineering. 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
| model	     |num_epoch  |learning_rate	         |num_boost_round |score    |
|------------|-----------|-----------------------|----------------|---------|
|initial  	 | 20	     | 3e-4                  | 100            | 1.80410 |
|add_features| 20	     | 3e-4                  | 100            | 0.68806 |
|hpo	     | 30   	 | 0.11             	 | 130            | 0.48898 |

#### References:
- Default values in the previous table (initial and add_feature models):
    - num_epoch, learning_rate: https://github.com/autogluon/autogluon/blob/master/tabular/src/autogluon/tabular/models/tabular_nn/hyperparameters/parameters.py
    - num_boost_round : https://lightgbm.readthedocs.io/en/latest/Parameters.html#num_iterations
    
### Create a line plot showing the top model score for the three (or more) training runs during the project.
#### With basic requirements:
![model_train_score.png](img/model_train_score.png)
#### all
![model_train_score.png](img/model_train_extended_score.png)
### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.
#### With basic requirements:
![model_test_score.png](img/model_test_score.png)
#### all
![model_test_score.png](img/model_test_extended_score.png)

## Summary
I started training a basic model with Autogluon, then I continued doing feature engineering when I got a better model performance, after that I tried hyperparameter tunning by setting three parameters with different values and  the results were better I spected, so  I wanted to improve even more my model then I decided to split the datetime field in individual parts (year, month, day and hour) and with the last configuration I ran the trainning process again by ignoring the datetime column, with which the model did not improve enough. Also I plotted several representative graphs such as lines, histograms and heatmap in order to visualize the distributions of the variables and their correlations, the trainning behaviour, etc.
For the two lastest models I had to change the time_limit parameter to 300 instead 600 (the value for the two first models) because those gave me errors in log console and break the training.
Final Summary Table:
| model	       |num_epoch  |learning_rate	       |num_boost_round |score    |
|--------------|-----------|-----------------------|----------------|---------|
|initial  	   | 20	       | 3e-4                  | 100            | 1.80410 |
|add_features  | 20	       | 3e-4                  | 100            | 0.68806 |
|hpo	       | 30   	   | 0.11             	   | 130            | 0.48898 |
|add_features_2| 30  	   | 0.11                  | 130        	| 0.49749 |

Finally the last model "hpo" is the best.

## Conclusion
This experience was amazing and useful for me, because I could use the concepts learned during the course in the classroom, Futhermore It give me more clarity about feature engineering. Also thanks to it I could learn more about how to use the AWS platform and its specific tool for  Machine Learning "SageMaker".

