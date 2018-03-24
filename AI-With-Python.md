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

#### Normalization

- **L1 normalization** refers to Least Absolute Deviations, making sure the sum of absolute values is 1 in each row.
- **L2 normalization** refers to least squares, making sure that the sum of squares is 1.

L1 is more resistant to outliers in the data. Where outliers are important, L2 becomes a better choice.

```python
# L1 Normalization
l1_normalized = preprocessing.normalize(input_data, norm='l1')
# L2 Normalization
l2_normalized = preprocessing.normalize(input_data, norm='l2')
```

### Label encoding

In the real world, labels tend to be words. sklearn excepts labels to be numbers.
```python
encoder = preprocessing.LabelEncoder()
encoder.fit(input_labels)
```
To encode a set of labels
```python
test_labels = ['a', 'c', 'b']
encoder.transform(test_labels)
```
To decode a set of numbers
```python
encoded_values = [2, 3, 1]
encoder.inverse_transform(encoded_values)
```

### Logistic regression classifier

Technique to explain the relationship between input and output variables.
Input variables assumed to be independent.
Output variables referred to as dependent variables.
The dependent variable can only take a fixed set of values which correspond to the classes.

Goal: Identify the relationship between the independent and dependent variables by estimating the probabilities using a **sigmoid curve** (logistic function).

```python
classifier = linear_model.LogisticRegression(solver='liblinear', C=1)
```
**C** imposes a penalty on misclassification. if the C is set too high the model will overfit to the training data.

