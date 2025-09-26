

📊**Big Data Processing & Machine Learning on S&P 500 Dataset**

This repository contains the code, preprocessing pipeline, analysis, and machine learning experiments performed on the S&P 500 historical dataset. The project is organized into two main parts: Big Data Processing and Machine Learning.

**Part 1: Big Data Processing
Task 1: Data Cleaning and Exploration**

Load Data: The dataset is imported into a Pandas DataFrame, with metadata printed to inspect columns.

Duplicates Handling: Both row-level duplicates and duplicate dates were identified and removed using drop_duplicates().

Missing Values: Missing values in Dividend and Real Price (~10%) were handled using forward fill (ffill) and backward fill (bfill), ensuring temporal continuity.

Statistical Summary: Computed min, max, mean, median, and standard deviation for all numeric columns.

Visualization: A scatter plot between Consumer Price Index (CPI) and S&P 500 was created to highlight long-term growth patterns and CPI correlation.

**Task 2: Feature Engineering**

Year-over-Year CPI Change: Added a new column for CPI rate change and identified the top 5 spikes.

12-Month Moving Average: Smoothed Earnings data with a rolling window (12 months). The first 11 months were left as NaN to avoid bias.

Normalization: Applied Min-Max scaling to the S&P 500 column for better comparability across periods.

**Task 3: Data Visualization**

Histogram of S&P 500: Showed right-skewed distribution, reflecting historical market growth.

Boxplot of PE10: Identified outliers during periods of high market valuation.

Correlation Heatmap: Revealed strong correlations between CPI and S&P 500, and between Earnings and Real Earnings, while other variables showed weaker independence.

**Part 2: Machine Learning
Task 1: Clustering with KMeans**

Feature Selection: Chose numeric features (SP500, Dividend, Earnings, CPI, Long Interest Rate, Real Price, Real Dividend, Real Earnings, PE10).

Scaling: Standardized features with zero mean and unit variance using StandardScaler.

Optimal Clusters: Applied the Elbow Method, finding k ≈ 3.

Clustering Results:

Cluster 1 – Early market periods (low CPI, low S&P 500).

Cluster 2 – Transitional economic periods (moderate CPI and S&P 500).

Cluster 3 – Modern market era (high CPI, high S&P 500).

Scatter plots confirmed clear separation along CPI and S&P 500 dimensions.

**Task 2: Predictive Modeling
(a) S&P Price Prediction**

Trained a Linear Regression model using economic indicators.

Achieved:

RMSE ≈ 1573 (small relative to S&P 500 scale).

R² = 0.98, showing excellent explanatory power.

Interpretation: Linear regression captures strong linear relationships effectively, making it a solid baseline model.

**(b) CPI Trend Classification**

Binary target CPI_Up created (1 = CPI increased, 0 = CPI decreased).

Used Logistic Regression with standardized features.

Achieved ~72% accuracy (well above random baseline).

Performance summary:

For CPI decreases: precision = 0.65, recall = 0.82, F1 = 0.72.

For CPI increases: precision = 0.81, recall = 0.64, F1 = 0.72.

Conclusion: Model is more confident when predicting increases but stronger at recall for decreases.

⚙️ **Tech Stack**

Python 3.10+

Pandas, NumPy — Data cleaning, transformation, and statistics

Matplotlib, Seaborn — Visualization

scikit-learn — Preprocessing, clustering, and ML models

**📌 Key Learnings**

Data cleaning: Removing duplicates and handling missing values is critical before analysis.

Scaling: Normalization and standardization greatly improve convergence and comparability.

Visualization: Histograms, scatter plots, boxplots, and heatmaps provide deep insights into financial patterns.

Clustering & ML: KMeans successfully grouped data into economic eras; Linear and Logistic Regression gave strong baselines for predictive tasks.

**📚 References**

Pandas Documentation

Matplotlib Documentation

Seaborn Documentation

scikit-learn Documentation

Palmer et al., “S&P 500 Historical Data” (dataset source)
