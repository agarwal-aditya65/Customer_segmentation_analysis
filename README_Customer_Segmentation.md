# Customer Segmentation and Market Impact Strategy

## Overview

This project develops a customer segmentation framework for **Venture Creed** using customer characteristics and purchasing-related business attributes.

The objective is to identify statistically meaningful and interpretable customer groups and translate those groups into actionable marketing and sales strategies.

The analysis covers:

- Exploratory Data Analysis (EDA)
- Data quality and redundancy checks
- Rare-category analysis
- Multivariate outlier detection using Isolation Forest
- Customer clustering using **K-Modes**
- Selection of the optimal number of clusters using the K-Modes cost curve
- Cluster-size validation and profiling
- Business-oriented cluster interpretation
- 2-D visualization using PCA
- Validation of the final segmentation solution

## Dataset

The dataset contains **3,030 customers** and includes customer identifiers, geographic/address attributes, and business-related segmentation variables.

The final clustering model uses **12 business-related categorical features**:

- Seasonality Segment
- EA Segment
- Revenue Bucket
- Profit Bucket
- Market Share Segment
- Casino Size Segment
- Market Potential Segment
- Churn Segment
- Competitiveness Flag
- Volume Segment
- Density Segment
- Propensity


## Methodology

### 1. Data Audit and EDA

The dataset is examined for:

- Missing values
- Duplicate records
- Duplicate Customer IDs
- Category distributions
- Low-variability features
- Rare categories
- Potentially redundant or unsuitable clustering features

### 2. Outlier Detection

Because the clustering variables are categorical, traditional numerical methods such as Z-score and IQR are not directly applied.

Instead, the notebook uses:

- Rare-category detection
- **Isolation Forest** after encoding the categorical features

Isolation Forest flagged **91 of 3,030 customers (3.0%)** as potential outliers. These customers are retained because unusual customer profiles may represent genuine and strategically important accounts.

### 3. Customer Clustering

Since the final clustering variables are categorical, **K-Modes** is used instead of K-Means.

The K-Modes cost curve is evaluated for different values of K. Based on the cost reduction, cluster-size validation, and business interpretability, **K = 5** is selected as the final segmentation.

### 4. Cluster Profiling

The five resulting clusters are profiled according to their dominant business characteristics and translated into actionable customer segments.

The notebook identifies the following segment names:

1. Dormant Low-Activity Accounts
2. Profitable Developing Accounts
3. Competitive White-Space Accounts
4. Dormant Competitive Accounts
5. High-Potential Early-Adopter Accounts

### 5. Business Strategy

Each segment is associated with a differentiated marketing and sales strategy based on characteristics such as profitability, growth potential, customer adoption behavior, dormancy, and competitive environment.

## Results

The final solution contains **5 customer segments** across the **3,030-customer** dataset.

The segmentation provides a framework for:

- Prioritizing high-potential accounts
- Developing profitable customers
- Reactivating selected dormant accounts
- Identifying competitive white-space opportunities
- Designing differentiated marketing and sales strategies

## Validation

The final segmentation was checked for:

- Missing values
- Duplicate customer records
- Duplicate Customer IDs
- Constant clustering features
- Cluster sizes
- Rare categories
- Multivariate outliers
- Business interpretability of the resulting clusters

The detected outliers were retained rather than automatically removed because they may represent genuine business opportunities.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- K-Modes
- Jupyter Notebook / Google Colab

## Project Structure

```text
customer-segmentation-market-analysis/
│
├── Customer_Segmentation.ipynb
├── README.md
└── requirements.txt
```

## How to Run

### Google Colab

1. Open `Customer_Segmentation.ipynb` in Google Colab.
2. Run the notebook cells sequentially.
3. When prompted, upload the dataset file.
4. The notebook reads the uploaded Feather dataset and performs the complete analysis.

### Local Environment

Install the dependencies:

```bash
pip install -r requirements.txt
```

Then open the notebook using Jupyter:

```bash
jupyter notebook
```

Because the current notebook uses `google.colab.files.upload()`, the data-loading cell is intended for Google Colab. For local execution, replace that upload step with a local Feather-file path.

## Conclusion

The analysis develops an actionable customer segmentation framework using K-Modes clustering on 12 business-related categorical features. Five interpretable customer segments were identified and linked to differentiated marketing and sales strategies.

The resulting segmentation can help Venture Creed prioritize high-potential accounts, develop profitable customers, selectively reactivate dormant accounts, and improve penetration in competitive markets.
