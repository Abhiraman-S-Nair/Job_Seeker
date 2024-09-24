# Machine Learning: Classification and Regression

## 1. Supervised vs Unsupervised Learning
- **Supervised Learning**: Involves training a model on labeled data, where the output is known. The goal is to learn a mapping from inputs to outputs.
- **Unsupervised Learning**: Involves training a model on unlabeled data. The goal is to identify patterns or groupings within the data.

## 2. Classification Algorithms
- **Support Vector Machine (SVM)**: A powerful classifier that finds the hyperplane that best separates the data into different classes.
- **k-Nearest Neighbors (k-NN)**: A simple algorithm that classifies a data point based on the majority class of its k nearest neighbors.
- **Decision Trees**: A model that splits the data into branches to make decisions based on feature values.

### Example: SVM in Python
```python
from sklearn import datasets
from sklearn import svm

# Load dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

# Create a SVM classifier
clf = svm.SVC(kernel='linear')
clf.fit(X, y)
```

## 3. Regression Algorithms
- **Linear Regression**: Models the relationship between dependent and independent variables by fitting a linear equation.
- **Polynomial Regression**: Extends linear regression by fitting a polynomial equation to the data.
- **Ridge Regression**: A regularized version of linear regression that adds a penalty term to reduce overfitting.

### Example: Linear Regression in Python
```python
from sklearn.linear_model import LinearRegression
import numpy as np

# Sample data
X = np.array([[1], [2], [3], [4], [5]])
y = np.array([1, 2, 3, 4, 5])

# Create a Linear Regression model
model = LinearRegression()
model.fit(X, y)
```

## 4. Confusion Matrix and Evaluation Metrics
- **Confusion Matrix**: A table used to evaluate the performance of a classification algorithm by comparing predicted and actual values.
- **Accuracy**: The ratio of correctly predicted instances to the total instances.
- **Precision**: The ratio of true positive predictions to the total predicted positives.
- **Recall**: The ratio of true positives to the total actual positives.

### Example: Confusion Matrix in Python
```python
from sklearn.metrics import confusion_matrix

# True labels and predictions
y_true = [1, 0, 1, 1, 0]
y_pred = [1, 0, 1, 0, 0]

# Compute confusion matrix
cm = confusion_matrix(y_true, y_pred)
print(cm)
```

## 5. Overfitting vs Underfitting
- **Overfitting**: Occurs when a model learns noise and details in the training data to the extent that it negatively impacts the model's performance on new data.
- **Underfitting**: Occurs when a model is too simple to capture the underlying patterns in the data.

### Bias-Variance Tradeoff
- **Bias**: Error due to overly simplistic assumptions in the learning algorithm.
- **Variance**: Error due to excessive complexity in the learning algorithm.

## 6. Train-Test Split and Cross-Validation
- **Train-Test Split**: The dataset is divided into two parts: one for training the model and the other for testing its performance.
- **Cross-Validation**: A technique to evaluate a model's performance by partitioning the data into multiple subsets and training/testing multiple times.

### Example: Cross-Validation in Python
```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestClassifier

# Model
model = RandomForestClassifier()

# Cross-validation
scores = cross_val_score(model, X, y, cv=5)
print(scores)
```

## 7. Feature Scaling and Engineering
- **Feature Scaling**: Standardizing or normalizing feature values to bring them into a similar range, improving model performance.
- **Feature Engineering**: The process of using domain knowledge to create features that make machine learning algorithms work effectively.

### Example: Feature Scaling in Python
```python
from sklearn.preprocessing import StandardScaler

# Sample data
data = [[0, 0], [1, 1], [2, 2]]

# Scale features
scaler = StandardScaler()
scaled_data = scaler.fit_transform(data)
print(scaled_data)
```
