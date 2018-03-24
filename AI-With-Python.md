# Artificial Inteligence with Python


### Supervised learning

Building a machine learning model that is based on labeled training data.

### Unsupervised learning

Building a model that does not rely on labeled training data.


### Classification

A classification model assigns a class to a new piece of data based on the patterns observed in the training dataset. eg. *Hot dog / Not hot dog*

A good classification model makes it easy to find and retrieve data.

We need to provide a large enough number of samples as training data for the algorithm to generalise the problem.
If there is an insufficient number of samples, then the algorithm will **overfit** to the training data, meaning it won't perform well on unknown data because it fine tuned itself to the patterns found in the training data.


### Preprocessing

In order to prepare the raw data to be used for training it must first be preprocessed into the right format for the model.
Preprocessing techniques include:
- Binarization
- Mean removal
- Scaling
- Normalization

#### Binarization

Converting numerical values into boolean values.
`sklearn.preprocessing` module provides a `Binarizer` class to do so. eg:
```python
data_binarized = preprocessing.Binarizer(threshold=2.1).transform(input_data)
```
This will turn the values above 2.1 to a 1, and everything else to a 0.

#### Mean removal

Moving the mean as close to 0 as possible.

It's useful to remove the mean from the feature vector, so that each feature is centered on zero. This is done to remove bias from the features. eg:
```python
data_scaled = preprocessing.scale(input_data)
```

#### Scaling

It is important to scale features to that there is a level playing field for the algorithm to train on. We don't want a feature to become an outlier just because of the nature of the measurement.
This can be done using
```python
data_scaled_minmax = preprocessing.MinMaxScaler(feature_range=(0, 1)).fit_transform(input_data)
```
