# SOME POINTS TO NOTE:

**I**
The features used for the random forest cannot be the high, close, low , open values directly without any transformation 
because what the model is essentially doing is creating a overfit of non linear decisions to certain prices ranges.
It is basically memorizing that when the close was above X value and open below Y value predict 1 or 0. 
You need to normalize the predictors in some way so that the model can use them independently of how high the value the stock is and truly create generalizable rules. 
Ratios are good since they use percentage instead of using absolute values and allow the model to use information of multiple candles as well.

**II**
When you split the data into training and testing datasets, you're essentially performing Simple Random Sampling. 
This means the training data will share similar elements and characteristics with the testing dataset. 
If you were to calculate the means of each predictor variable in both datasets, they would roughly be the same due to this random sampling.

The key point here is that claiming the model hasn't "seen" the testing data isn't entirely accurate.
Through simple random sampling, the model captures many properties of the testing data.

Instead, consider training the model using the first 70% of the data and then keeping the remaining 30% aside for predictions.
This approach ensures that the model has no prior exposure to the prediction data, although there are considerations to be made about this method as well.

I've used simple random sampling in the past and achieved seemingly accurate results. 
However, it wasn't until I adopted this alternative approach that I noticed slightly higher errors. 
Therefore, I believe this method offers a more realistic evaluation of model performance.

**III**
the model without hyperparameter tuning. if hyperparamter tuning is done, when backtesting we no longer need to look for the best parameters. 
In contrast to cross-validation which requires more tuning
