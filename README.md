# W7-Kaggle_competition

![portada](https://github.com/Ironhack-Data-Madrid-Enero-2021/W7-Kaggle_competition/blob/main/images/PORTADA.jpg)

## Description

- Find the best machine learning model and params for a given dataset. 

## Instructions

Find the Kaggle competition with your cohort name, i.e. **diamonds-datamad0122-part**, link [here](https://www.kaggle.com/competitions/diamonds-part-datamad0122/overview)

## Folder Structure
### In the main folder
* 1. **main.ipynb** processing and cleaning the dataset: duplicates, nulls and rows with values equal to 0 where drop. Also, columns x, y and z where not only highly correlated, but also used to calculate 'depth', so depth was recalculated using the formula 'depth = z / ((x + y)/2)' in order to have a more precise value and then columns 'x', 'y' and 'z' were dropped. Outliers were treated differently, only those way higher or lower than the max and min of the test.csv were dropped.
* 2. **encoding.ipynb** is where both train.csv and test.csv where encoded and standarized in order to find the best model. The most succesful one came up just doing a label encoding for the cathegorical values, with no normalization or standarization of any kind, of also OneHotEncoder and RobustScaler were tried trying to minimaze the effects of the outliers.
* 3. **model.ipynb** here is were most of the models were created. Although LinearRegression, DecisionTreeRegressor, KNeighborsRegressor and RandomForestRegressor, the best results were found using GradientBoostingRegressor, so this is the method used for most of the submits. The different cleanings and encodings described on the previous points were tried to find the best model, which was gradient_boost_2.pkl using train_enc_2.csv, having a RMSE of 0.095
* 4. **clustering.ipynb** from the analysis done in main.ipynb we could infer that the data was organized into two distinc sets and the clustering confirmit as we can see in the following graphs
![clusters](https://github.com/Origamologo/Kaggle_competition/blob/master/images/clusters.png)
Two different models were created, gradient_boost_4.pkl and gradient_boost_5.pkl, out of train_clustered_0.csv and train_clustered_1.csv Then they were tested on test_clustered_0.csv and test_clustered_1.csv and their results concatenated, but unfourtunately its results where slightly worse than those obtained with the GradientBoostingRegressor constructed 'by hand'.
* 5. **test.ipynb** here is where the prediction tests were done and saved to be submitted.
* 6. **auto_ml.ipynb** AutoML was also tried, although its results where slightly worse than those obtained with the GradientBoostingRegressor constructed 'by hand'.
* 7. **H2O.ipynb** H2O AutoML was also tried, although its results where slightly worse than those obtained with the GradientBoostingRegressor constructed 'by hand'.

### In the subfolders
* **data** contains the original train.csv and test.csv provided for this competiton and:
        - **clusters** a folder that contaings the csv generated in clustering.ipynb
        - **encodings** a folder that contaings the csv generated in encoding.ipynb
        - **models** a folder that contaings the pkl generated in model.ipynb, auto_ml.ipynb and H2O.ipynb
        - **predictions** a folder that contaings the csv generated in test.ipynb using the models that can be found in models folder
* **images** contains the images seen in this readme

## Tools
[pandas](https://pandas.pydata.org/)

[matplotlib](https://matplotlib.org/)

[scikit-learn](https://scikit-learn.org/stable/)

[auto-sklearn](https://automl.github.io/auto-sklearn/master/#)

[H2O](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/automl.html)
