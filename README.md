# BodyFat_Prediction - Tried out 2 different model (Linear and Random Forest)

Linear Regression Model considering different aspect of ML in EDA, Feature Engineering, Hyperparameter Tuning, Serializing model for application

	EDA:
			1.) pandas_profiling import ProfileReport - Get the Basic Idea of the data and different relation
				Inference: Features and Body Fat are related Linearly. 

			2.)VIF - Checking for Multi Collinearity
				Inference: Weight , Abdomen, Hip are having high collinearity with Density.

			3.)PCA check the Variance Spread
				Inference: 5 Principle component account for 85% of Variance.
				
			4.)Hypothesis Testing Feature Identification by Checking Slope in Population
				Inference: Density satisfies the 5% signficance value. Age, Chest, Weight though they are not satisfying the Required confidence interval of 95% they are having relatively better T value
				
			5.)New Feature from  different combination of the existing feature are tried but no good result during the hypothesis Testing.

	Feature Engineering:

			1.) Top 4 Feature of T-Test [ 'Age', 'Chest', 'Density', 'Weight']. 
			
			2.) Weight is highly correlated with Density we will ignore the Weight. 
			
			3.) 'Age' and 'Chest' does not satisfy 95% confidence interval during the Population slope check. Still they are used. Depending only on the Density will cause model to have high variance.

	Learning Model:

			1.)Scalar Transformation Class with Standard Normalization. (class scalartransform)
			2.)Ridge Regressor with an Adjustment for Non Zero Prediction.(class AdjRidgeRegres) 
			3.)Hyper Parameter Alpha Tuning with GridSearchCV (scoring='explained_variance')
			4.)Performance on Test Set
					Regression R^2 Value : 0.9966821070102583
					MSE = 0.20101665727756052
			5.)Deeper Look into High Error Samples. Proper Gaussian Distribution is observed in Erro with 95% samples less than 1.5 BodyFat error
			6.)Serialization of class scalartransform, class AdjRidgeRegres using pickle

Random Forest Regressor Hyperparameter Tuning


	1.)All the Feature are used for the model
	2.)Hyper Parameter Tuning with RandomSearchCV and then GridSearchCV
	3.)Performance on Test Set
			MSE: 1.3983152692307526
	4.)Visualization of Tree
    
