# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME HERE

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
While trying to submit the predictions I realized that my predictions has not any negative values. We need to update the negative values with zero if there is any in predictions. 

### What was the top ranked model that performed?
WeightedEnsemble_L3 was the top ranked model that performed. 

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
During the exploratory data analysis (EDA) phase, I examined the histograms and made the following observations:

1. Binary Features: I identified certain features, namely "holiday" and "working day," that appeared to have binary values, indicating whether a particular day was a holiday or a working day.

2. Nearly Normally Distributed Features: Several features, such as "temp," "atemp," "humidity," and "windspeed," exhibited distributions that closely resembled a normal distribution. This implies that these features followed a bell-shaped curve, with most values concentrated around the mean.

3. Categorical Features: The features "season" and "weather" appeared to be categorical. While the data was fairly evenly distributed among the four seasons, there was a predominant weather category (1) throughout the dataset.

4. Monthly Distribution: The data exhibited a relatively uniform distribution on a monthly basis, spanning the years 2011 and 2012. The first 19 days of each month were allocated for training, while the remaining days were reserved for testing. Furthermore, the data was recorded at different hours throughout the day.

To enhance the model's understanding of the patterns related to bike share demand, I followed the notebook's suggestion of adding the "hour" feature to the dataset. This addition seemed reasonable as it provided a more general characteristic, enabling the trained models to gain insights into the hours of the day that might have the highest demand for bike shares without explicitly considering specific years, months, or days.

### How much better did your model preform after adding additional features and why do you think that is?
In initial phase the model score was 1.78984. When added the features and trained the model score was improved to 0.68027 but in hyperparameter optimization the model score get more improved 0.48714. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Hyperparameter optimization is essential for improving model performance, preventing overfitting/underfitting, utilizing resources efficiently, enhancing generalization, and ensuring confidence in the results. So, on doing so the model got improved its score from 1.78984 to 0.48714.

### If you were given more time with this dataset, where do you think you would spend more time?
If give more time with this dataset then we can do the follwing things:
- Add more than one feature to the dataset and train models to see if it improves Kaggle score!
- Separating hour from datetime to have additional feature
- Perform multiple rounds of hyperparameter tuning to see if it improves Kaggle score!
- Test individual algorithm types (KNN, Neural Nets, RF, XGBoost, etc) and write a detailed analysis of which one performs better on this dataset.
- Create more than the required visualizations for the report.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|    | model        | hpo1                                                                                                                                                                                            | hpo2                                                                                                                                                                                 | hpo3                                                                                                                                                     |   score |
|---:|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|--------:|
|  0 | initial      | default_vals                                                                                                                                                                                    | default_vals                                                                                                                                                                         | default_vals                                                                                                                                             | 1.78984 |
|  1 | add_features | default_vals                                                                                                                                                                                    | default_vals                                                                                                                                                                         | default_vals                                                                                                                                             | 0.68027 |
|  2 | hpo          | GBM (Light gradient boosting) : num_boost_round: [lower=100, upper=500], num_leaves:[lower=6, upper=10], learning_rate:[lower=0.01, upper=0.3, log scale], applying random search with 5 trials | XGB (XGBoost): n_estimators : [lower=100, upper=500], max_depth : [lower=6, upper=10], eta (learning_rate) : [lower=0.01, upper=0.3, log scale] applying random search with 5 trials | CAT (CATBoost) : iterations : 100, depth : [lower=6, upper=10], learning_rate  : [lower=0.01, upper=0.3, log scale] applying random search with 5 trials | 0.48714 |

### Create a line plot showing the top model score for the three (or more) training runs during the project.
![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.
![model_test_score.png](img/model_test_score.png)

## Summary
In conclusion, this project underscored the significance of both feature engineering and hyperparameter optimization in the machine learning workflow. It highlighted the iterative nature of this process, where we alternate between extracting new features from the available data, conducting exploratory data analysis (EDA), and experimenting with different models using the newly engineered features. This iterative cycle continues until we achieve satisfactory validation and test error values.