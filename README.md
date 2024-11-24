Auto MPG Analysis and Linear Regression

This project involves the analysis of the Auto MPG dataset, which provides data on the fuel efficiency of cars along with their specifications. The analysis includes cleaning, visualization, and building a linear regression model to predict fuel efficiency (miles per gallon, mpg).

Project Overview

This project demonstrates:

Data Cleaning: Handling missing and incorrect values.
Exploratory Data Analysis (EDA): Using visualization techniques to identify trends and outliers.
Feature Engineering: Standardizing features for machine learning models.
Linear Regression: Implementing a linear regression model from scratch and comparing its performance with Scikit-learn's implementation.
Table of Contents

Installation
Dataset
Project Workflow
Key Insights
Conclusion
License
Installation

To run this project, ensure you have the following libraries installed:

pip install numpy pandas matplotlib seaborn scikit-learn
Dataset

The Auto MPG dataset includes the following attributes:

mpg: Miles per gallon (fuel efficiency).
cylinders: Number of engine cylinders.
displacement: Engine displacement.
horsepower: Engine horsepower.
weight: Vehicle weight.
acceleration: Acceleration from 0-60 mph.
model_year: Year of manufacture.
origin: Country of origin.
car_name: Name of the car (not used in regression analysis).
Project Workflow

Data Cleaning:
Replaced invalid horsepower values ("?") with the median value after converting the column to numeric.
Checked for missing values and handled them appropriately.
Removed the car_name column, as it is non-numeric and not useful for regression.
Exploratory Data Analysis (EDA):
Visualized outliers in numerical columns using boxplots.
Analyzed feature correlations using a heatmap to identify relationships between variables.
Feature Engineering:
Standardized features using StandardScaler for better performance in regression models.
Linear Regression:
Built a custom linear regression model using gradient descent.
Evaluated the custom model using Mean Squared Error (MSE).
Compared performance with Scikit-learn's LinearRegression model.
Evaluation:
Compared MSE of custom and Scikit-learn implementations:
Custom implementation MSE: 8.52
Scikit-learn implementation MSE: 7.91
Key Code Snippets
Correlation Heatmap:
plt.figure(figsize=(10, 8))
sns.heatmap(df[numerical_cols].corr(), cmap="coolwarm", annot=True)
plt.title("Correlation Matrix")
plt.show()
Custom Linear Regression Implementation:
def linear_reg(X, y, alpha, Iteration):
    X["bias"] = 1
    theta = np.zeros(X.shape[1])
    X = X.values
    y = y.values
    m = len(X)
    cost_list = []
    for i in range(Iteration):
        h_theta = np.dot(X, theta)
        cost = (1/(2*m)) * np.sum((h_theta - y)**2)
        gradient = (1/m) * np.dot(X.T, (h_theta - y))
        theta -= alpha * gradient
        cost_list.append(cost)
    return theta, cost_list
Key Insights

Correlations:
Weight and displacement are negatively correlated with mpg, indicating heavier cars tend to have lower fuel efficiency.
Horsepower and mpg also show a negative correlation.
Linear Regression Model:
Both the custom and Scikit-learn models performed well, with Scikit-learn achieving slightly lower MSE.
Gradient descent was successfully implemented and visualized using the cost function over iterations.
Conclusion

This project showcases end-to-end handling of a regression problem:

Cleaning and preparing data for machine learning.
Implementing a linear regression model from scratch.
Comparing custom implementation with Scikit-learn for validation.
Future improvements could involve:

Exploring additional features or interactions between variables.
Applying advanced regression techniques such as Ridge or Lasso regression.
License

This project is licensed under the MIT License.
