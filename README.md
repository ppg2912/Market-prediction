# Market-prediction
In a perfectly efficient market, buyers and sellers would have all the agency and information needed to make rational trading decisions. As a result, products would always remain at their “fair values” and never be undervalued or overpriced. However, financial markets are not perfectly efficient in the real world.Developing trading strategies to identify and take advantage of inefficiencies is challenging. Even if a strategy is profitable now, it may not be in the future, and market volatility makes it impossible to predict the profitability of any given trade with certainty. As a result, it can be hard to distinguish good luck from having made a good trading decision. Therefore this project aims at building a quantitative trading model to maximize returns using market data from a major global stock exchange.
## Dataset
The dataset contains an anonymized set of features, feature_{0...129}, representing real stock market data. Each row in the dataset represents a trading opportunity, for which prediction of an action value: 1 to make the trade and 0 to pass on it is supposed to be done. Each trade has an associated weight and resp, which together represents a return on the trade.

## Process
### Handling the data
Trades with weight = 0 are included in the dataset for completeness, although such trades will not contribute towards the scoring evaluation. So we first remove the data points having weight 0.

We fill NAN values with a very low negative number so they aren’t considered to have much of an effect on the model learning. But also since the data should be numeric, it will preserve homogeneity. 

Next, we need to predict the value of resp. For that, I created the label prediction column which will contain 1 (Favorable outcome) if resp (return) is positive or 0 if it is negative. Then I created the X train and Y train data frames. X train consists of all the features and weights and Y trains consists of the label.

## Classificaion
### Dummy Classifier
I then used a dummy classifier to set up a baseline for the model. A dummy classifier is a type of classifier which does not generate any insight about the data and classifies the given data using only simple rules. 

Here I used the most frequent rule. So the model doesn’t learn anything but just outputs the most frequent data in training data. Then I found out the accuracy and displayed the false positives false negatives on a confusion matrix.

### XGBoost
I configured the GridSearchCV object to choose the best hyperparameters  for the model. A model hyperparameter is a characteristic of a model that is external to the model and whose value cannot be estimated from data. The value of the hyperparameter has to be set before the learning process begins. Grid search builds a model for every combination of hyperparameters specified and evaluates each model.

Having gotten the best hyper parameters for my model, I trained the XGBoost classifier and made predictions. Then I found out the accuracy and displayed the false positives false negatives on a confusion matrix.















