# Customer Segmentation Using Clustering

This project explores unsupervised learning techniques to segment credit card users based on their spending behavior and payment patterns. The main goal is to derive actionable business insights and targeted strategy suggestions using clustering methods.

## Project Structure

* `refined_df.csv`: Cleaned dataset with PCA components & clustering labels
* `note.ipynb`: Exploratory Data Analysis with visual trends, KMeans, DBSCAN, and PCA implementation
* `findings.ipynb`: Business insights, strategy mapping, cluster interpretation

## Methods Used

* **Principal Component Analysis (PCA)** – For dimensionality reduction
* **KMeans Clustering** – To identify optimal customer segments
* **DBSCAN** – Attempted, but did not yield meaningful groupings
* **Seaborn/Matplotlib** – For informative visualizations

## Key Findings

* Identified **4 unique customer segments** based on transaction and behavior metrics
* Segments include:
   * *Loyal Spenders*
   * *Low-Engaged Users*
   * *Installment Spenders*
   * *Cash Advance Seekers*
* Business strategies recommended for each segment based on usage & risk

----

Clustering helped me break down a large pool of users into meaningful categories. These insights can power:


* **Targeted marketing**
* **Credit risk management**
* **Customer retention campaigns**

----

## Future Work

* Integrate supervised models for churn prediction
* Deploy dashboards with Plotly/Dash
* Real-time customer segmentation with streaming data

## Note

This project is for **analytical storytelling and strategy planning**. No personally identifiable information (PII) is used.
