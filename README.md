## Problem Statement

The Ames Housing Data Set is a compilation of house sale prices from the Ames Assessor's Office designed for use in determining the value of area homes.  The problem here is one of modeling.  How accurately can we determine the prospective sale price of a novel home given only a set of characteristics that describe the house?  In this project we will simulate this by using a portion of the Ames Housing Data Set as a test set for us to evaluate the predictive success of the models we build.

## Executive Summary

Please find two notebooks pertaining to initial data processing, cleaning, basic editing/engineering, and initial exploratory data analysis, and finally loading changes to the test file.

Please find four notebooks demonstrating iterations of a GridSearch ElasticNet model for the data (Models 1-4).  Model 1 is basic Gridsearch ElasticNet, Model 2 implements a log transform on the price data.  Model 3 attempts unsuccessfully to perform a comprehensive polynomial features implementation of GridSearch ElasticNet and includes some follow-up experimentation.  Model 4 represents a consolidation of the previous models and the first decently serviceable model, in my opinion.

Please find a notebook in which I attempt to predict price by a new method, the K Nearest Neighbors Regressor.  

Please find a final notebook in which I return to the GridSearch ElasticNet model and establish a functional workflow, allowing me to iteratively feature engineer and finally make real, stable improvements on the model.  

## Data Dictionary

The Data Dictionary can be found at:
http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

## Conclusions and Recommendations

In conclusion, it is certainly possible to meaningfully predict sale price from the available training data.  I found that an ElasticNet GridSearch was the most effective model available, particularly given that I was working down from a large set of variables rather than building out from a small set.  Both of these approaches have some validity, but I think that the next modeling attempt I make, I may try and build out a set of variables instead because it seems like it may provide more control for the modeler, observing what contributes and what does not accretively.  A counter-argument is that working from a large set of variables can immediately and holistically identify the influence of variables that may have otherwise been counter-intuitive as factors.

Logarithmic transform of price was particularly effective in improving the model, due to the right skew of sale prices, and the fact we were working with a linear model, this both reduced and normalized residuals.

KNN Regressor did not seem very successful in this case.  RMSE was significantly larger than my best Elastic models despite optimization. In particular the log transform with the KNN regressor no longer seemed to damp the underprediction issue in the original data.  One interesting thing that I did note was that there were several significant outliers by price/area that were affecting my residual plot.  The KNN regressor did a much better job of bringing these values to the mean, due to the way the KNN averages a group of neighbors to generate its predictions.  This does not involve as much error sensitivity to individual points.

In iterating through my ElasticNet model, I was able to fine-tune it by removing mathematically irrelevant features, engineering key polynomial features to add, and consolidating certain variables into higher correlated composite scores.

Ultimately, this was an engaging exercise and a fantastic introduction to the optimization problems and toolsets involved in regression modeling
