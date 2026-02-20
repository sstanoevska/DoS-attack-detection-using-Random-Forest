
I have used the Intrusion Detection Evaluation Dataset (CIC-IDS2017).
Before training the model, these steps have been performed:

1. Dataset Aggregation
Multiple CSV files were merged into a single dataset using glob and pandas.

2. Label Simplification
Attack labels were standardized and grouped into:
- BENIGN
- DoS
- DDoS
- PortScan
- WebAttack
- Infiltration
- Other
This ensured consistent classification targets.

3. Outlier Handling
Feature values were clipped between the 1st and 99th percentiles to reduce the impact of extreme outliers.

4. Infinite and Missing Value Handling
- Infinite values were replaced with NaN
- Missing values were removed

5. Low-Variance Feature Removal
VarianceThreshold was applied to remove near-constant features.

6. Feature Scaling
PowerTransformer (Yeo-Johnson) was used to:
- Reduce skewness
- Normalize feature distributions
- Standardize features

7. Dimensionality Reduction
Principal Component Analysis (PCA) was applied:
- Retained 90% of total variance
- Generated principal components (PC1, PC2, ...)

8. Final Dataset Export
The processed dataset was saved as:
`pca_with_labels.csv`

This dataset was then used for model training and evaluation.
