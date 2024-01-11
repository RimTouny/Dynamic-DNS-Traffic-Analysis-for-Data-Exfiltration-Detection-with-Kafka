# **Enhanced Data Exfiltration Detection via Dynamic DNS Traffic Analysis usng Kafka**
Crafting static and dynamic models for data exfiltration detection via DNS traffic analysis using . Static model trained on batch data [Static_dataset.csv](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/files/13904748/Static_dataset.csv) while dynamic model simulates a continuous stream[Kafka_dataset.csv](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/files/13904759/Kafka_dataset.csv) [that should treat as a data stream (local Kafka Server) which will be used to evaluate the dynamic model]. Rigorous analysis, feature engineering, and model training conducted. Implementation part of AI for Cyber Security Master's assignment at the University of Ottawa, 2023.

- Required libraries: scikit-learn, pandas, matplotlib.
- Execute cells in a Jupyter Notebook environment.
- The uploaded code has been executed and tested successfully within the [Google Colab](https://colab.google/) environment.

## Bianry-class classification problem 
Task is to enhanced data exfiltration detection through DNS traffic analysis : 1 / 0.

### Independent Variables:
   +	'timestamp': The time at which the data was recorded.
   +	'FQDN_count': The count of fully qualified domain names.
   +	'subdomain_length': The length of the subdomain.
   +	'upper': The count of uppercase characters.
   +	'lower': The count of lowercase characters.
   +	'numeric': The count of numeric characters.
   +	'entropy': Entropy value.
   +	'special': The count of special characters.
   +	'labels': The count of labels.
   +	'labels_max': Maximum count of labels.
   +	'labels_average': Average count of labels.
   +	'longest_word': The longest word in the subdomain.
   +	'sld': Second-level domain.
   +	'len': Length of the subdomain.
   +	'subdomain': The subdomain.
  
### Target variable:
   +	'Target Attack: Target Attack label, where 1 indicates an attack and 0 indicates no attack


## **Key Tasks Undertaken**

+ **Static Model**
   1. Data Analysis:
      - Loaded and explored the "Static_dataset.csv."
      - Utilized various statistical tools and visualizations to understand feature distributions, identify imbalances, and          assess the characteristics of numerical and categorical variables.
        ![merge_from_ofoct](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/10001fe8-4d57-4c66-976b-239e0a89e4bc)
     
      - Employed histograms, QQ plots, and boxplots for a comprehensive analysis of numerical features.
        ![merge_from_ofoct](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/07581bba-53dc-4183-b629-80233c7d7d52)
          
      - Examined the count of attack and non-attack cases for categorical features through count plots.
        ![download](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/34cc2231-40d3-4f89-9aed-d721e0033f88)


   2. Feature Engineering and Data Cleaning:
      - Analyzed the dataset for string variables and performed necessary transformations.
      - Addressed missing values within the dataset , duplicate rows , drop unnecessary features.
      - Applied embedding techniques to encode categorical variables, maintaining interpretability.
        
   3. Feature Filtering/Selection:
      - Employed different statistical techniques, including Mutual Information, ANOVA F-values, Chi-squared scores, and             RandomForest-based Recursive Feature Elimination (RFE).
        ![merge_from_ofoct](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/7f40f32d-b48c-4539-a409-e1e37d6bb0df)
      - Selected relevant features based on the results of the feature selection techniques.

    4.  Model Selection:
      - Splitting data to train ,test.
      - Apply Normalization using StandardScaler.
      - Chose three machine learning models for evaluation: Random Forest, Logistic Regression, and XGBoost.
      - Configured each model with default parameters.
        ![merge_from_ofoct (2)](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/a67ffd1d-c289-4ac2-84b5-0b4fc2d00487)

    6.  Evaluation performance:
       - Using F1-score, get the  Best Feature Selection/ Model
        ![image](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/f175eced-0f99-4070-879d-c817ec3744bc)

           Number of Best Feature:
        
           ![image](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/08788240-dc08-41bc-8a28-d2b599e0fd64)

   - Best F1-score is using Mutual Information on Random Forest Model.
       ```python
      selected_features=['FQDN_count','entropy','labels','labels_average','longest_word','lower','sld','special']
      ```
    8. Hyperparameter Tuning & Model evaluation: using selected_features from Mutual Information.
       ```python
       Best hyperparameters for Random Forest: {'max_depth': None, 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 200}
       Best hyperparameters for Logistic Regression: {'C': 0.1, 'penalty': 'l2', 'solver': 'newton-cg'}
       Best hyperparameters for XGB Extreme X Gradient Boosting: {'colsample_bytree': 0.8, 'learning_rate': 0.3, 'max_depth': 5, 'min_child_weight': 1, 'n_estimators': 200, 'subsample': 1.0}```
  

    10. Champion Static Model :
        ![image](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/84cecf28-e6af-4cff-82e3-87b3acbc43c1)
        
        ![merge_from_ofoct (4)](https://github.com/RimTouny/Dynamic-DNS-Traffic-Analysis-for-Data-Exfiltration-Detection-with-Kafka/assets/48333870/0217333f-6526-4663-8b75-8fbaa2cfb51e)

    12. Save the Champion Model for the Dynamic phase.
