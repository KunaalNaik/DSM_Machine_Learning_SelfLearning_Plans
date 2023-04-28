# Objective
Using the CRISP DM process to execute a Data Science project plan. 
Specific questions that needs to be asked by each stage so I can execute my project effectively.

# CRISP-DM Questions

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

## Example Project - Predict Insurance Claim Fraud

### Business Understanding

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

### Data Understanding

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

### Data Preparation

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

