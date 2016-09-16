After you've created the training datasource, you use it to create an ML model, train the model, and then evaluate the results. The ML model is a collection of patterns that Amazon ML finds in your data during training. You use the model to create predictions.

Splits the training datasource into two sections, one containing 70% of the data and one containing the remaining 30%

Trains the ML model on the section that contains 70% of the input data

Evaluates the model using the remaining 30% of the input data

A batch prediction is a set of predictions for a group of observations. Amazon ML processes the records in a batch prediction together, so processing can take some time. Use batch predictions for applications that require predictions for sets of observations or predictions that don't use results interactively.

How the ML picks up patterns in videos and text and where the tagging occurs?

The target attribute is a special attribute in the training data that contains the information that Amazon Machine Learning attempts to determine. For example, let’s say you want to build a model that predicts whether a call is legitimate or not. Your training data contains metadata on a past transaction that has a target attribute of “1” if the call was bad or “0” otherwise. You use Amazon Machine Learning to discover patterns that connect the target attribute with the transaction metadata (all other attributes). You use ML models based on these patterns to make a prediction without the target attribute present. In this example, it means predicting whether a transaction is fraudulent based on its metadata, before knowing whether the bank will reject it or not.


How does one "teach" it or how does deep learning occur?
Evolutionary learning using positive and negative connections.
The more neurons, the more complicated the models can be. We train the networks for fitness using human augmented feedback. Genetic algorithms.

Need to explain how the tagging works during ingestion
We're answering 


Need to explain how the deep learning occurs


How does the user interface w/the machine learning engine to correct any predictions
The user interfaces with the model using a web interface that allows the user to clip the data and adjust thresholds based on the training and prediction engine testing model.

How are the predictions accessed
The predictions are delivered in CSV format to an S3 bucket, which can be consumed by other applications or viewed.


Take a single game where the ref has done a particularly poor job in spotting field misconduct. We review the footage of the game and manually tag each time an event happens in the dataset that we know is an error on the referre's part. This data is fed to our model which has watched many many games already and understand the rules of football.
