# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Tanisha Bansal

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
 In my experiments, I conducted several trials, including the initial raw submission, added features through exploratory data analysis, and feature engineering. During these submissions, I realized that some models produced negative prediction values which caused Kaggle submission errors. To address this, I replaced all negative predictions with zero before submitting the results.

### What was the top ranked model that performed?
 The model created using added features (WeightedEnsemble_L3) delivered the best performance, achieving a validation RMSE score of 37.9800 and a Kaggle score of 0.44798. This model was developed through enhanced data processing and without employing hyperparameter optimization, outperforming others on unseen test data.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
 Exploratory data analysis identified opportunities to transform existing data for improved model performance. Features such as datetime were parsed to extract hour, weekday, etc. to capture temporal patterns. Features like season and weather were converted to categorical types, adding a new day_type feature derived from holiday and workingday.
### How much better did your model preform after adding additional features and why do you think that is?
 Model performance improved dramatically, about 138% better than the initial attempt. This was primarily due to addressing multicollinearity by dropping highly correlated features and transforming numeric categorical variables to actual categorical types, which helped the model leverage patterns more effectively.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
 Hyperparameter tuning enhanced model performance notably, though not always outmatching the feature-engineered model without tuning. Different configurations were tested, revealing the importance of time limits and presets in AutoGluon, as computational overhead can hinder model building with complex hyperparameter sets.

### If you were given more time with this dataset, where do you think you would spend more time?
 With more time, I’d explore deeper hyperparameter tuning with high-quality presets and extend time limits. Also, blending models at different ensemble stages or varying architectures could provide novel insights and improvements.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
| Model                   | HPO1                           | HPO2                           | HPO3                                   | Score  |
|-------------------------|-------------------------------|-------------------------------|----------------------------------------|--------|
| initial                 | prescribed_values              | prescribed_values              | presets: 'high quality (auto_stack)'   | 1.84484|
| add_features            | prescribed_values              | prescribed_values              | presets: 'high quality (auto_stack)'   | 0.44798|
| hpo (top-hpo-model: hpo2)| Tree-Based Models: GBM, XT, XGB, RF | KNN                           | presets: 'optimize_for_deployment'     | 0.49440|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![Model Train Score](https://github.com/BTANISHA11/cd0385-project-starter/raw/main/Screenshot%20(746).png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](https://github.com/BTANISHA11/cd0385-project-starter/raw/main/Screenshot%20(745).png))

## Summary
The project demonstrated the power of AutoGluon's AutoML capabilities in practical scenarios like predicting bike-sharing demand. Initial models served as a robust baseline, significantly improved by featuring engineering and exploratory analysis. While hyperparameter tuning provided benefits, feature engineering proved essential for this dataset. The study highlighted the importance of balancing resource constraints such as time and memory when deploying large-scale algorithms, optimizing exploration vs. exploitation, and employing model ensembling.
