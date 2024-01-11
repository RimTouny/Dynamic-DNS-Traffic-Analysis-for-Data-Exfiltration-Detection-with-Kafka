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
      - Employed histograms, QQ plots, and boxplots for a comprehensive analysis of numerical features.
      - Examined the count of attack and non-attack cases for categorical features through count plots.

   2. Feature Engineering and Data Cleaning:
      - Analyzed the dataset for string variables and performed necessary transformations.
      - Addressed missing values within the dataset , duplicate rows , drop unnecessary features.
      - Applied embedding techniques to encode categorical variables, maintaining interpretability.
        
   3. Feature Filtering/Selection:
      - Employed different statistical techniques, including Mutual Information, ANOVA F-values, Chi-squared scores, and           - RandomForest-based Recursive Feature Elimination (RFE).
      - Selected relevant features based on the results of the feature selection techniques.

    4.  Model Selection:
      - Splitting data to train ,test.
      - Apply Normalization using StandardScaler.
      - Chose three machine learning models for evaluation: Random Forest, Logistic Regression, and XGBoost.
      - Configured each model with default parameters.
        
    5.  Evaluation performance:
       - Using F1-score, get the  Best Feature Selection/ Model

    6. Hyperparameter Tuning & Model evaluation
    7. Champion Static Model
    8. Save the Champion Model
