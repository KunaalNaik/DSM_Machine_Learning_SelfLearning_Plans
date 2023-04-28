# Objective
Using the CRISP DM process to execute a Data Science project plan. 
Specific questions that needs to be asked by each stage so I can execute my project effectively.

## CRISP-DM Questions

1. Business Understanding:
   - What is the main objective of the project?
   - Who are the stakeholders involved in this project?
   - What are their expectations or requirements?
   - Are there any business constraints or limitations?
   - How will the results of this project be used to support business decisions?

2. Data Understanding:
   - What data sources are available for this project?
   - What is the quality of the data (completeness, accuracy, consistency)?
   - Are there any legal or ethical considerations in using the data?
   - What features are relevant to the project's objective?
   - Do the data sources require any preprocessing or cleaning?

3. Data Preparation:
   - What data cleaning steps are necessary (e.g., handling missing values, outlier detection)?
   - How will the data be transformed or aggregated for analysis?
   - What feature engineering or selection techniques will be used?
   - How will the data be split into training, validation, and testing sets?
   - Are there any additional data sources needed to enrich the dataset?

4. Modeling:
   - What machine learning algorithms or statistical techniques are suitable for this project?
   - How will model performance be evaluated (e.g., accuracy, precision, recall, F1-score)?
   - Are there any hyperparameters that need to be tuned?
   - What model validation techniques will be used (e.g., cross-validation, holdout method)?
   - How will the final model be selected?

5. Evaluation:
   - How does the model perform on the validation and testing sets?
   - Are the results aligned with the business objectives and stakeholder expectations?
   - Are there any biases or fairness concerns with the model's predictions?
   - How can the model's performance be further improved?
   - What are the key insights or findings from the analysis?

6. Deployment:
   - How will the model be deployed into a production environment?
   - What infrastructure and resources are needed to support the deployment?
   - How will the model be monitored and maintained over time?
   - What is the plan for updating the model as new data becomes available?
   - How will the results be communicated to stakeholders and integrated into business processes?

By answering these questions during each stage of the CRISP-DM process, you will have a comprehensive project plan that can be effectively executed.

# *Example Project* 
## Predict Insurance Claim Fraud

## 1/ Business Understanding

In this example, we will answer the questions for the Business Understanding stage of the CRISP-DM process to address the machine learning problem of predicting insurance claim fraud for a fictitious company called Acme Inc.

1. Main objective of the project:
   - The primary objective of this project is to develop a machine learning model that can accurately predict fraudulent insurance claims, enabling Acme Inc. to reduce financial losses and improve claim processing efficiency.

2. Stakeholders involved in this project:
   - Acme Inc.'s executive leadership
   - The insurance claim processing department
   - The fraud investigation team
   - IT and data science teams

3. Stakeholder expectations or requirements:
   - Executive leadership: expects a reduction in financial losses due to fraud (e.g., 20% reduction in one year) and a positive return on investment for the project.
   - Claim processing department: anticipates improved efficiency in identifying and handling potential fraudulent claims, reducing manual review workload by 30%.
   - Fraud investigation team: seeks a reliable tool for prioritizing and validating suspicious claims, improving their success rate by 25%.
   - IT and data science teams: require clear project objectives, manageable timelines, and resource allocation to build, deploy, and maintain the model.

4. Business constraints or limitations:
   - Limited access to historical claim data with confirmed fraud cases for model training.
   - Legal and privacy concerns related to the use of policyholder information.
   - Time and resource constraints to build, deploy, and maintain the model.
   - Ensuring fairness and avoiding biases in the model's predictions.

5. How the results of this project will be used to support business decisions:
   - The machine learning model's predictions will be integrated into the claim processing workflow to flag potentially fraudulent claims for further investigation.
   - The insights gained from the model can be used to improve fraud detection strategies and target fraud prevention efforts.
   - The model's performance metrics will be monitored and reported to stakeholders to support data-driven decision-making and demonstrate the project's impact on reducing financial losses due to fraud.

By answering these questions, we have established a clear understanding of the business context and objectives for the project, which will help guide the subsequent stages of the CRISP-DM process.

## Data Understanding

1. Data sources available for this project:
   - ClaimData: A database containing historical insurance claims with details such as claim ID, policy number, date of claim, claim amount, and claim status (fraudulent or legitimate).
   - PolicyData: A dataset of policyholder information, including policy number, policyholder name, address, age, gender, policy type, policy start date, and policy end date.
   - ExternalFraudData: An external dataset from a fraud detection agency containing known fraudulent claims and associated policyholder details.

2. Quality of the data:
   - ClaimData: Mostly complete and accurate but may contain some inconsistencies due to manual data entry errors.
   - PolicyData: High quality and complete information about policyholders, with few missing or inconsistent records.
   - ExternalFraudData: Complete and accurate, but only a limited number of cases are available for training the model.

3. Legal or ethical considerations in using the data:
   - Ensure proper data handling and storage to maintain policyholder privacy and comply with data protection regulations.
   - Obtain necessary permissions to use ExternalFraudData for model training.
   - Make sure the model does not introduce biases or unfairly discriminate against specific groups of policyholders.

4. Relevant features for the project's objective:
   - From ClaimData: claim ID, policy number, date of claim, claim amount, and claim status.
   - From PolicyData: policy number, policyholder age, gender, policy type, and policy duration (calculated from policy start and end dates).
   - From ExternalFraudData: All features, as they provide valuable information about known fraudulent claims.

5. Data sources requiring preprocessing or cleaning:
   - ClaimData: May need cleaning to address inconsistencies and missing values.
   - PolicyData: Requires minimal preprocessing, mainly to calculate policy duration.
   - ExternalFraudData: May need preprocessing to align with the format and structure of ClaimData and PolicyData.

By answering these questions, we have gained an understanding of the data sources, their quality, and the necessary preprocessing steps, which will help inform the Data Preparation stage of the CRISP-DM process.

## Data Preparation

1. Data cleaning steps necessary:
   - Missing values:
     * ClaimData: Impute missing claim amounts with the average claim amount by policy type. For missing claim dates, consider using the median date for that policy type.
     * PolicyData: Impute missing policy start and end dates using the median dates for the corresponding policy type.
     * ExternalFraudData: No missing values identified.

   - Outlier detection:
     * ClaimData: Identify and analyze outliers in claim amounts using techniques like the IQR method or Z-score. Investigate the causes and decide whether to keep, adjust, or remove the outliers.
     * PolicyData: Check for unrealistic values in age and policy duration, and investigate the causes. Consider adjusting or removing these records if they appear to be errors.
     * ExternalFraudData: No significant outliers identified.

   - Categorical encoding:
     * ClaimData: No categorical features identified that require encoding.
     * PolicyData: One-hot encode the policy type feature to convert it into a numerical format suitable for machine learning algorithms.
     * ExternalFraudData: No categorical features identified that require encoding.

2. Data transformation or aggregation for analysis:
   - Merge ClaimData and PolicyData on the policy number to create a single dataset with all relevant features for each claim.
   - Calculate additional features, such as time since the policy was issued or time until policy expiration, to potentially improve model performance.

3. Feature engineering or selection techniques:
   - Use domain knowledge to create new features that might be relevant to predicting fraudulent claims, such as claim frequency for a policyholder.
   - Apply feature selection techniques, such as recursive feature elimination or LASSO regularization, to identify the most important features for the model.

4. Data split into training, validation, and testing sets:
   - Divide the merged dataset into three subsets: 70% for training, 15% for validation, and 15% for testing.
   - Ensure that the distribution of fraudulent and legitimate claims is similar across all three subsets using stratified sampling.

5. Additional data sources needed to enrich the dataset:
   - Consider obtaining additional external datasets with more known fraudulent cases to improve model performance.
   - Explore the possibility of incorporating data from other sources, such as social media or customer reviews, to provide additional context for detecting fraudulent claims.

By addressing these questions, we have outlined the data preparation steps necessary to clean, preprocess, and transform the data for modeling in the insurance claim fraud prediction project.

## Modeling

1. Suitable machine learning algorithms or statistical techniques:
   - Experiments conducted with the following algorithms:
     * Logistic Regression
     * Decision Trees
     * Random Forest
     * Support Vector Machines
     * Neural Networks

   - Challenges faced with advanced models:
     * Overfitting: Complex models like Neural Networks and Random Forest may be more prone to overfitting, especially when working with a limited number of known fraudulent cases.
     * Interpretability: Advanced models can be more challenging to interpret and explain to stakeholders, which may reduce trust in the model's predictions.

2. Model performance evaluation:
   - Metrics used to evaluate model performance:
     * Precision: Measures the proportion of true positive predictions among all positive predictions.
     * Recall: Measures the proportion of true positive predictions among all actual positive instances.
     * F1-score: Harmonic mean of precision and recall, balancing both metrics.
     * AUC-ROC: Area under the Receiver Operating Characteristic curve, which measures the model's ability to distinguish between fraudulent and legitimate claims.

3. Hyperparameters that need to be tuned:
   - For Logistic Regression:
     * Regularization strength (C): Controls the inverse of the regularization term to prevent overfitting.
     * Regularization type (L1 or L2): Determines the type of penalty applied to the coefficients during optimization.
   - Hyperparameters for other models were also tuned in the experiments, but Logistic Regression ultimately provided the best performance.

4. Model validation techniques:
   - k-fold cross-validation: Perform k-fold cross-validation with k=5 on the training dataset to estimate the performance of each model and select the best one. This technique helps to reduce overfitting and provides a more accurate estimate of model performance.

5. Final model selection:
   - Logistic Regression was chosen as the final model, as it provided the best balance between performance, simplicity, and interpretability.
   - The model's performance on the validation set was satisfactory, with a high F1-score and AUC-ROC, indicating its ability to accurately predict fraudulent insurance claims.

By addressing these questions, we have completed the Modeling stage, selecting Logistic Regression as the best model for our insurance claim fraud prediction project and understanding the challenges faced during the experimentation process.

## Evaluation

| Model               | Precision | Recall | F1-score | AUC-ROC | Performance | Simplicity | Interpretability | Selected Model |
|---------------------|-----------|--------|----------|---------|-------------|------------|------------------|----------------|
| Logistic Regression | 0.85      | 0.80   | 0.82     | 0.92    | High        | High       | High             | Yes            |
| Decision Trees      | 0.79      | 0.78   | 0.79     | 0.88    | Medium      | Medium     | Medium           | No             |
| Random Forest       | 0.83      | 0.76   | 0.79     | 0.90    | High        | Low        | Low              | No             |
| Support Vector Machines | 0.81   | 0.77   | 0.79     | 0.89    | Medium      | Low        | Low              | No             |
| Neural Networks     | 0.86      | 0.74   | 0.79     | 0.91    | High        | Low        | Very Low         | No             |

With the table above, we can now answer the Evaluation questions:

1. Model performance on the validation and testing sets:
   - The Logistic Regression model has performed well on both the validation and testing sets, with a precision of 0.85, recall of 0.80, F1-score of 0.82, and AUC-ROC of 0.92.
   - These performance metrics indicate that the model can accurately predict fraudulent insurance claims while minimizing false positives and false negatives.

2. Alignment of results with business objectives and stakeholder expectations:
   - The high F1-score of 0.82 indicates a good balance between precision and recall, which is important due to the imbalance in the dataset (i.e., a small number of fraudulent claims compared to legitimate claims). The model can effectively identify fraudulent claims without raising too many false alarms, meeting stakeholder expectations for efficiency and fraud reduction.
   - The high AUC-ROC of 0.92 demonstrates the model's ability to distinguish between fraudulent and legitimate claims, supporting the business objective of reducing financial losses due to fraud.

3. Biases or fairness concerns with the model's predictions:
   - The high performance metrics suggest that the model is not introducing significant biases or unfairly discriminating against specific groups of policyholders. However, continuous monitoring and assessment of the model's predictions should be performed to ensure fairness and avoid potential biases.

4. Improvements to the model's performance:
   - To further improve the model's performance, consider obtaining additional data on fraudulent claims, fine-tuning hyperparameters, or experimenting with other feature engineering techniques.
   - Regularly retrain the model with new data to ensure it remains accurate and up-to-date as the patterns of fraudulent behavior evolve.

5. Key insights or findings from the analysis:
   - Logistic Regression outperformed more advanced models, proving that simplicity and interpretability can be more effective in certain scenarios, especially when dealing with imbalanced datasets.
   - The high performance of the model indicates a strong relationship between the selected features and the likelihood of a claim being fraudulent, providing valuable insights for future fraud prevention strategies.

By evaluating the model's performance and alignment with business objectives, we can conclude that the Logistic Regression model is a suitable choice for the insurance claim fraud prediction project.

## Deployment

We recommend presenting the results of the Logistic Regression model to stakeholders to secure their buy-in before proceeding with deployment. This presentation should include a summary of the project's objectives, the model's performance metrics, and the benefits of implementing the model in the insurance claim processing workflow.

Once stakeholder approval is obtained, we can develop an action plan to deploy the model on a real-time basis:

1. Integrate the model with the existing claim processing system to flag potentially fraudulent claims automatically.
2. Set up a system for model monitoring and maintenance, including performance tracking and regular updates with new data.
3. Establish a clear process for the fraud investigation team to review and act upon the flagged claims.
4. Train claim processing and fraud investigation teams on how to use the model's predictions effectively.
5. Conduct periodic reviews of the model's impact on business objectives, such as reducing financial losses and improving claim processing efficiency.

Now, let's create a before and after table to illustrate the changes brought by implementing the model:

| Scenario  | Manual Review Workload | Fraud Detection Success Rate | Financial Losses due to Fraud | Time to Identify Fraudulent Claims |
|-----------|------------------------|------------------------------|-------------------------------|------------------------------------|
| Before    | High                   | Low                         | High                          | Long                               |
| After     | Reduced                | Improved                    | Reduced                       | Shorter                            |

With this table in mind, we can answer the questions about the before and after scenario of implementing the model:

1. How has the model impacted the claim processing workflow?
   - By implementing the model, the claim processing workflow has become more efficient, as the manual review workload is reduced due to the automatic flagging of potentially fraudulent claims.

2. What improvements have been observed in the fraud detection process?
   - The fraud detection success rate has improved, as the model's high performance enables the fraud investigation team to prioritize and validate suspicious claims more effectively.

3. How has the model affected financial losses due to fraud?
   - The model has helped reduce financial losses due to fraud by accurately identifying fraudulent claims and allowing the company to take appropriate action.

4. How has the time taken to identify fraudulent claims changed after implementing the model?
   - The time to identify fraudulent claims has become shorter, as the model quickly flags suspicious claims for further investigation, enabling the fraud investigation team to act promptly.

By deploying the model and integrating it into the insurance claim processing workflow, we have achieved improvements in efficiency, fraud detection success rate, and financial outcomes for the company.

### Business Impact

A table illustrating the quantitative impact of implementing the model for Acme Inc.:

| Metric                          | Before Model Implementation | After Model Implementation | Improvement |
|---------------------------------|-----------------------------|----------------------------|-------------|
| Number of Claims Reviewed       | 10,000                      | 10,000                     | N/A         |
| Manual Reviews                  | 3,000                       | 1,200                      | 60%         |
| Fraudulent Claims Detected      | 150                         | 240                        | 60%         |
| False Positives                 | 200                         | 80                         | 60%         |
| Financial Losses due to Fraud   | $1,500,000                  | $900,000                   | 40%         |
| Average Time to Detect Fraud (days) | 30                       | 15                         | 50%         |

With this table, we can observe the quantitative improvements that resulted from implementing the Logistic Regression model for Acme Inc:

1. The number of manual reviews has decreased by 60%, reducing workload and allowing the fraud investigation team to focus on higher priority claims.
2. The model has increased the number of fraudulent claims detected by 60%, improving the overall fraud detection success rate.
3. The number of false positives (i.e., legitimate claims incorrectly flagged as fraudulent) has decreased by 60%, reducing unnecessary workload and potential customer dissatisfaction.
4. Financial losses due to fraud have been reduced by 40%, which translates into significant savings for Acme Inc.
5. The average time to detect fraudulent claims has been reduced by 50%, allowing for faster action against fraud and minimizing potential financial losses.

This table demonstrates the considerable positive impact that implementing the model has had on Acme Inc.'s claim processing workflow and fraud detection capabilities.
