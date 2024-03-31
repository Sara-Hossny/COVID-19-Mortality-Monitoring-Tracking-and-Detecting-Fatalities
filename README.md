# COVID-19-Mortality-Monitoring-Tracking-and-Detecting-Fatalities
### README: COVID-19 Mortality Monitoring, Tracking, and Detecting Fatalities

#### Dataset Overview:

The dataset contains information about COVID-19 cases, specifically focusing on mortality tracking. Each data entry includes whether the patient has been cured (0) or has deceased (1). 

Data Preprocessing steps:
1. Encoding gender to avoid bias towards any specific gender.
2. Standard scaling of the data.
3. 
#### Approach Considerations:
- Our primary goal is to minimize False Negatives (FN), thus emphasizing higher recall, especially for detecting fatalities. 
- We recognize the importance of not misclassifying patients who will eventually succumb to the disease as recovered. Hence, minimizing false negatives is prioritized.
- GridSearch was employed to fine-tune parameters, with `n_repeat = 5` to address data imbalance.

#### Machine Learning Algorithms and Parameter Tuning:

We applied various machine learning algorithms and fine-tuned them to achieve optimum performance. Here are the algorithms along with their respective optimized parameters:

1. **K-Nearest Neighbors (KNN):**
   - Parameters tuned:
     - `weights`: ['uniform', 'distance']
     - `metric`: ['euclidean', 'manhattan', 'minkowski']
     - `n_neighbors`: [3, 5, 7, 9, 11]
   - Best parameters: 
     - {'metric': 'manhattan', 'n_neighbors': 5, 'weights': 'distance'}
   - Mean recall: 0.553088
   - Mean Accuary:0.939420

2. **Logistic Regression:**
   - Parameters tuned:
     - `solver`: ['newton-cg', 'lbfgs', 'liblinear']
     - `penalty`: ['l1', 'l2', 'elasticnet']
     - `C`: [100, 10, 1.0, 0.1, 0.01]
     - `max_iter`: [10000, 20000]
   - Best parameters: 
     - {'C': 100, 'max_iter': 10000, 'penalty': 'l1', 'solver': 'liblinear'}
   - Mean recall: 0.722684
  - Mean Accuary:0.947395
    
3. **Naive Bayes classifier:**
   - Parameters tuned:
     - `var_smoothing`: [0.0004328761281083057]
   - Best parameter:
     - {'var_smoothing': 0.0004328761281083057}
   - Mean recall: 0.722684
   - Mean Accuary: 0.915072

4. **Decision Trees:**
   - Parameters tuned:
     - `max_depth`: range(3, 10, 1)
     - `min_samples_split`: [2, 5, 10]
     - `min_samples_leaf`: [4, 5, 6, 7]
     - `criterion`: ['gini', 'entropy']
   - Best parameters:
     - {'criterion': 'gini', 'max_depth': 4, 'min_samples_leaf': 7, 'min_samples_split': 2}
   - Mean recall: 0.790735
   - Mean Accuracy: 0.953623
   - 
5. **Support Vector Machine (SVM):**
   - Parameters tuned:
     - `kernel`: ['linear', 'poly', 'rbf', 'sigmoid']
     - `degree`: [3, 4, 5] (for poly kernel only)
     - `C`: [100, 10, 1.0, 0.1, 0.01]
   - Best parameters:
     - {'C': 1.0, 'degree': 3, 'kernel': 'linear'}
   - Mean recall: 0.778088
   - Mean accuracy: 0.956812


