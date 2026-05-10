Predicting Pulsar Stars


For this project, I will be building a classification model that will predict whether a star is a pulsar star or not, based on radio emissions collected. A pulsar is a highly magnetic, rotating, neutron star, formed from the collapsed core of a star after it’s gone supernova. It emits beams of electromagnetic radiation that sweep across space, similar to a lighthouse beacon. The dataset that will be used is “Predicting Pulsar Star” from Dr Robert Lyon on Kaggle.


A wrangle function was used to import and clean the dataset. Column names were standardized by removing extra whitespace to ensure consistency. Duplicate rows were removed to maintain data integrity, and missing values were handled using row-wise deletion. No variables were identified with more than 50% missing values. Additionally, no high-cardinality, redundant, or leakage variables were present in the dataset. Outliers were removed using a quantile-based approach, where values outside the 1st and 99th percentiles were excluded for each feature.

The dataset shows strong class imbalance, with approximately 5% of the samples belonging to the pulsar class. Several features exhibit high variance and significant skewness, particularly the DM-SNR-related variables, suggesting the presence of outliers and extreme values. Additionally, feature scales vary significantly, indicating that standardization will be required prior to modeling.

The feature distributions are highly right-skewed, particularly the DM-SNR related variables. The dataset also shows a strong class imbalance, with non-pulsars dominating the target variable. Several features appear to contain discriminative structure, and will likely require scaling and possibly transformation before modeling.

The correlation matrix shows that several DM-SNR features and integrated profile statistics are strongly correlated with the target variable, indicating good predictive potential. However, there is also noticeable multicollinearity among features, particularly between skewness and kurtosis-based variables, suggesting redundancy in the dataset.

Boxplots show clear separation between pulsar and non-pulsar classes for kurtosis, skewness, and DM-SNR mean, suggesting strong predictive power.

The dataset was split into training and testing sets to evaluate the model performance. Stratified sampling was applied to preserve the original class distribution due to the imbalance.

A Random Forest classifier was selected due to its ability to capture non-linear relationships and handle complex feature interactions. Class weights were set to ‘balanced’ to address class imbalance.

The model achieved high overall accuracy (98%), but due to class imbalance, performance on the pulsar class is better assessed using precision, recall, and F1-score. For the pulsar class, precision is high (0.95), indicating that positive predictions are generally reliable, while recall is lower (0.66), meaning that some actual pulsars are missed. The resulting F1-score of 0.78 reflects this trade-off, indicating moderate overall performance for the minority class.