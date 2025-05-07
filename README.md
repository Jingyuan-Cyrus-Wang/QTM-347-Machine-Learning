# QTM-347-Machine-Learning

## Introduction
Keeping talents in the team is crucial for organizational stability and firm growth.
Employee attrition data offers a unique view into the interplay between company organizational culture and employee’s individual performance.
By using data-driven methods to forecast attrition, companies can proactively identify risk factors, implement targeted interventions, and ultimately build a more resilient workforce.

## Set-up: Dataset/Test 1
Dropping useless Features/Removing null values
Mapping categorical predictors into Numeric
Split the data randomly to Train/Test (20%)
Building Pipelines for different supervised learning approaches: OLS/Ridge/Lasso/Random Forest/Gradient Boosting
7000*16, using all columns as predictors

Result:
The derived MSEs are super-close, and the R^2s are all negative, which indicate that the models fit the data very bad.
Solution:
Performing feature engineering to select the truly valuable predictors.


<img width="721" alt="截屏2025-05-07 上午12 57 11" src="https://github.com/user-attachments/assets/2d342ee4-61c8-4c78-a34f-f4db53166a0a" />


By performing various feature engineering methods, i.e. LassoCV, permutation importance, etc, we manually kept several features and ran through the same models again.

Unfortunately-these values still show P-value over 0.05, which rejects the null, meaning these factors doesn’t show stats significance with attrition rate.

This could be explained in multiple ways:
The models aren’t powerful enough to catch the complexities between the data points.
The relationship may exist between the intersections.
The predictors collected couldn’t capture the whole landscape of the attrition rate.


<img width="463" alt="截屏2025-05-07 上午12 57 23" src="https://github.com/user-attachments/assets/c2bc5bda-e39e-4ef5-be0e-d09667a9d934" />


## Set-Up: Dataset/Test2
Data: Used the IBM HR “Employee Attrition” CSV, ~1,470 rows, ~30 columns of demographic, work‐history, and satisfaction metrics.
Map Attrition: Yes/No to 1/0
Dropped ID‐like fields (EmployeeNumber, EmployeeCount, Over18, StandardHours).
Split into train (80%) / test (20%) with stratification on the binary target.
Convert all categorical variables to dummy variable, and apply standard scale to all numerical variables.

Results:
Building Pipelines for different supervised learning approaches: OLS/Ridge/Lasso/Random Forest/Gradient Boosting
All model has similar MSE and R square value. Ridge regression model is the best among all
Even the best model (Ridge) explains only 17.2% of the variation in attrition.


<img width="328" alt="3" src="https://github.com/user-attachments/assets/f23b6834-a858-4e8b-ac76-69e8bf8a5cb7" />


<img width="1319" alt="1" src="https://github.com/user-attachments/assets/ae4f4075-feee-4280-a7ab-93a151e40bb8" />


<img width="875" alt="2" src="https://github.com/user-attachments/assets/8e5526fe-e2ac-4679-a0f4-1080562614dc" />


At the end we used a logistic regression model for classification. we used the train group to predict attrition = 1 and obtained 88% accuracy.


<img width="309" alt="4" src="https://github.com/user-attachments/assets/50f0d6df-d6a0-4d71-9387-868776429b27" />


Best Model: 
Ridge Regression achieved the best performance by controlling overfitting and handling multicollinearity.

Key Finding:
Simpler regularized models can outperform more complex algorithms when data is properly preprocessed.

In this project, we address the problem of predicting employee attrition — whether an employee is likely to leave a company — using structured HR data. Employee turnover can cause significant disruptions, increase operational costs, and lower team morale. By predicting attrition risk early, organizations can design better retention strategies and allocate resources more efficiently. Our motivation stems from the importance of workforce stability in driving company success, and attrition prediction has broad applications in human resources, organizational planning, and employee engagement initiatives.
To solve this problem, we transform it into a binary classification task and build machine learning models on a cleaned and encoded dataset. We apply a preprocessing pipeline involving top-category encoding for categorical variables and standardization for numeric features. After testing several models, including Ordinary Least Squares (OLS) regression and Ridge regression, we found that Ridge regression produced the best results in terms of predictive performance. Ridge regression was particularly effective because it balances model complexity and generalization by penalizing large coefficients, helping avoid overfitting — a common issue in high-dimensional data. While our approach performed well, limitations include potential loss of detailed category information during encoding and the assumption that relationships between features and attrition risk are relatively linear.
