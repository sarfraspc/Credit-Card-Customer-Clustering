# Research Paper: Credit Card Customer Segmentation Using Clustering

## Abstract

This research paper presents a comprehensive analysis of credit card customer segmentation using unsupervised machine learning techniques, specifically focusing on clustering algorithms. Leveraging a dataset containing various credit card usage behaviors and payment patterns, this study aims to identify distinct customer segments to provide actionable insights for targeted marketing strategies, credit risk management, and customer retention campaigns. The methodology involves data preprocessing, dimensionality reduction using Principal Component Analysis (PCA), and clustering with K-Means. An attempt was also made to use DBSCAN, but K-Means proved more effective in yielding interpretable and actionable segments. The findings reveal four unique customer segments: Loyal Spenders, Low-Engaged Users, Installment Spenders, and Cash Advance Seekers, each characterized by specific behavioral traits. These insights can significantly enhance business decision-making by enabling more personalized customer engagement and risk assessment.

## 1. Introduction

In today's highly competitive financial landscape, understanding customer behavior is paramount for credit card companies to maintain a competitive edge and foster sustainable growth. Customer segmentation, the process of dividing a broad customer base into distinct groups based on shared characteristics, is a powerful analytical tool that enables businesses to tailor their strategies to the specific needs and preferences of different customer cohorts. This approach moves beyond a one-size-fits-all model, allowing for more efficient resource allocation, improved customer satisfaction, and enhanced profitability.

Traditional customer segmentation often relies on demographic information or simple transactional data. However, with the proliferation of digital transactions and advanced data collection capabilities, there is an increasing opportunity to leverage more sophisticated analytical techniques to uncover deeper, more nuanced patterns in customer behavior. Unsupervised machine learning algorithms, particularly clustering methods, are well-suited for this purpose as they can identify inherent groupings within complex datasets without prior knowledge of the group structures.

This paper details a project that applies clustering techniques to a real-world credit card usage dataset. The primary objective is to segment credit card customers based on their spending habits, payment frequencies, cash advance usage, and other relevant financial metrics. By identifying these segments, credit card companies can develop highly targeted interventions, such as personalized product offerings, customized marketing campaigns, and proactive risk management strategies. The project explores the application of Principal Component Analysis (PCA) for dimensionality reduction, followed by K-Means clustering for segment identification. The effectiveness and interpretability of the resulting clusters are critically evaluated, and practical business implications are derived. This research contributes to the growing body of literature on data-driven customer relationship management (CRM) in the financial sector, offering a practical framework for implementing advanced analytical solutions.




## 2. Methodology

This section outlines the systematic approach undertaken to perform credit card customer segmentation. The methodology encompasses data acquisition, preprocessing, dimensionality reduction, and the application of clustering algorithms.

### 2.1. Data Acquisition and Description

The dataset utilized for this study is `CC GENERAL.csv`, obtained from the user's repository. It contains 8950 rows and 18 features, each representing a distinct aspect of credit card usage and customer behavior over a period of 12 months. Key features include:

*   **BALANCE**: Monthly average balance amount.
*   **BALANCE_FREQUENCY**: How frequently the balance is updated.
*   **PURCHASES**: Total amount of purchases made.
*   **ONEOFF_PURCHASES**: Total amount of one-off purchases.
*   **INSTALLMENTS_PURCHASES**: Total amount of installment purchases.
*   **CASH_ADVANCE**: Amount of cash advanced by the user.
*   **PURCHASES_FREQUENCY**: How frequently purchases are being made.
*   **ONEOFF_PURCHASES_FREQUENCY**: How frequently one-off purchases are made.
*   **PURCHASES_INSTALLMENTS_FREQUENCY**: How frequently installment purchases are made.
*   **CASH_ADVANCE_FREQUENCY**: How frequently cash advances are being taken.
*   **CASH_ADVANCE_TRX**: Number of cash advance transactions.
*   **PURCHASES_TRX**: Number of purchase transactions.
*   **CREDIT_LIMIT**: Credit limit of the user.
*   **PAYMENTS**: Amount of payments made by the user.
*   **MINIMUM_PAYMENTS**: Minimum amount of payments due.
*   **PRC_FULL_PAYMENT**: Percentage of full payment paid by the user.
*   **TENURE**: Tenure of credit card service for the user.

### 2.2. Data Preprocessing

Before applying clustering algorithms, the raw data underwent several preprocessing steps to ensure data quality and suitability for analysis:

1.  **Handling Missing Values**: The dataset contained missing values, particularly in the `MINIMUM_PAYMENTS` and `CREDIT_LIMIT` columns. Missing values in `MINIMUM_PAYMENTS` were imputed using the median of the column, as its distribution was observed to be skewed. For other numerical columns with missing values, the mean imputation strategy was applied. The `CUST_ID` column was dropped as it serves as a unique identifier and does not contribute to the clustering process.
2.  **Feature Scaling**: To prevent features with larger numerical ranges from dominating the clustering process, all numerical features were scaled using `StandardScaler`. This transformation standardizes features by removing the mean and scaling to unit variance, ensuring that each feature contributes proportionally to the distance calculations in clustering algorithms.

### 2.3. Dimensionality Reduction: Principal Component Analysis (PCA)

Given the relatively high dimensionality of the dataset (17 features after `CUST_ID` removal), Principal Component Analysis (PCA) was employed for dimensionality reduction. PCA is a linear dimensionality reduction technique that transforms the data into a new coordinate system such that the greatest variance by any projection of the data lies on the first coordinate (called the first principal component), the second greatest variance on the second coordinate, and so on. For this project, PCA was used to reduce the data to two principal components. This reduction facilitates visualization of the clusters in a 2D space and can also improve the efficiency and performance of clustering algorithms by removing noise and multicollinearity.

### 2.4. Clustering Algorithms

Two distinct clustering algorithms were explored in this project:

#### 2.4.1. K-Means Clustering

K-Means is a centroid-based, unsupervised learning algorithm that partitions `n` observations into `k` clusters, where each observation belongs to the cluster with the nearest mean (centroid). The algorithm iteratively assigns data points to clusters and updates the cluster centroids until convergence. To determine the optimal number of clusters (`k`), the silhouette score was calculated for a range of `k` values (2 to 10). Although higher silhouette scores were observed for fewer clusters (e.g., 2 or 3), `k=4` was ultimately chosen for K-Means. This decision was driven by the objective of deriving more granular and actionable business insights, even if it meant a slightly lower silhouette score compared to a simpler two or three-cluster solution. The K-Means model was then trained with `n_clusters=4` on the PCA-transformed data.

#### 2.4.2. DBSCAN Clustering

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is a density-based clustering algorithm that groups together data points that are closely packed together, marking as outliers those points that lie alone in low-density regions. Unlike K-Means, DBSCAN does not require the number of clusters to be specified beforehand and can discover clusters of arbitrary shapes. The key parameters for DBSCAN are `eps` (the maximum distance between two samples for one to be considered as in the neighborhood of the other) and `min_samples` (the number of samples in a neighborhood for a point to be considered as a core point). A knee plot was used to estimate the optimal `eps` value. Despite its theoretical advantages for certain data distributions, DBSCAN did not yield meaningful or interpretable clusters for this dataset, with many points being classified as noise or forming very few, large, and uninformative clusters. Consequently, the insights derived from DBSCAN were not considered suitable for business strategy planning, and the focus remained on the K-Means results.




## 3. Results and Findings

This section presents the outcomes of the clustering analysis, focusing on the K-Means algorithm's ability to segment credit card customers and the characteristics of each identified cluster.

### 3.1. K-Means Clustering Results

After applying PCA to reduce the dimensionality of the dataset to two principal components, K-Means clustering was performed. The silhouette score analysis was conducted to evaluate the optimal number of clusters. While 2 or 3 clusters showed slightly higher silhouette scores, a decision was made to proceed with **4 clusters** (`k=4`). This choice was primarily driven by the desire to achieve more granular and actionable business insights, allowing for a more nuanced understanding of customer behavior patterns. The K-Means model successfully partitioned the credit card customers into four distinct groups.

### 3.2. Cluster Characteristics and Interpretation

The four identified customer segments, based on their spending and payment behaviors, are:

#### Cluster 0 – Loyal Spenders

*   **Characteristics**: This segment is defined by high purchase activity, including both one-off and installment purchases, and a strong tendency towards making full payments. They maintain a moderate balance and have a high credit limit. Their consistent engagement and responsible payment behavior make them highly valuable customers.
*   **Key Metrics (Average)**:
    *   Balance: ~3102
    *   Credit Limit: ~9512
    *   High Purchases and Full Payments

#### Cluster 1 – Low-Engaged Users

*   **Characteristics**: This segment exhibits very low purchase activity and frequency, indicating minimal engagement with their credit cards for transactions. They tend to carry a high balance relative to their low activity, suggesting they might be utilizing their credit line without active spending. Their low engagement makes them a potential target for reactivation efforts.
*   **Key Metrics (Average)**:
    *   Balance: ~4764
    *   Credit Limit: ~3120
    *   Very Low Purchase Activity and Frequency

#### Cluster 2 – Installment Spenders

*   **Characteristics**: Customers in this cluster show a higher propensity for installment purchases over one-off transactions. They demonstrate consistent purchasing habits, indicating a preference for structured repayment plans. They carry a moderate balance and have a reasonable credit limit.
*   **Key Metrics (Average)**:
    *   Balance: ~4571
    *   Credit Limit: ~4233
    *   Higher Usage of Installment Purchases

#### Cluster 3 – Cash Advance Seekers

*   **Characteristics**: This segment is characterized by very high usage of cash advances and a low purchase frequency. They often have a low percentage of full payments, suggesting financial strain or a reliance on cash advances for liquidity. They typically have a moderate balance and a relatively high credit limit, which they utilize for cash withdrawals rather than purchases.
*   **Key Metrics (Average)**:
    *   Balance: ~864
    *   Credit Limit: ~7480
    *   Very High Cash Advance Usage

### 3.3. Visual Representation of Clusters

The PCA-reduced 2D scatter plot visually confirms the separation of these four customer segments, illustrating how K-Means effectively grouped customers with similar behavioral patterns. While some overlap exists, the distinct centroids and general distribution of points within each cluster support the interpretability of the segmentation.

### 3.4. DBSCAN Evaluation

DBSCAN was also explored as an alternative clustering method. However, the results from DBSCAN were not considered meaningful for business interpretation. The algorithm tended to classify a significant number of data points as noise and did not form clearly defined or interpretable clusters that could be readily translated into actionable business strategies. This outcome reinforced the decision to focus on the K-Means clustering results for deriving practical insights.




## 4. Discussion and Future Work

### 4.1. Business Implications and Strategic Recommendations

The customer segmentation derived from this study offers significant value for credit card companies seeking to optimize their business strategies. By understanding the distinct behaviors and needs of each segment, companies can implement highly targeted and effective interventions:

*   **Cluster 0 – Loyal Spenders**: These customers are highly engaged and financially responsible. Strategies for this segment should focus on **retention and reward programs**. This includes offering exclusive benefits, higher-tier loyalty points, premium services, and personalized offers that reinforce their positive spending and payment habits. The goal is to deepen their loyalty and encourage continued high-value engagement.

*   **Cluster 1 – Low-Engaged Users**: This segment represents an opportunity for **reactivation and increased engagement**. Companies should investigate the reasons for their low activity, which could range from holding multiple cards to dissatisfaction. Strategies might include targeted reactivation campaigns with attractive introductory offers, personalized communication highlighting underutilized card benefits, or even financial advisory services to help them manage their balances more effectively and encourage active usage.

*   **Cluster 2 – Installment Spenders**: These customers prefer structured payment options. Strategies should focus on **promoting EMI (Equated Monthly Installment) offers and flexible repayment plans**. This segment is receptive to products that allow them to manage larger purchases over time. Tailored marketing for installment-based products, clear communication about repayment terms, and seamless integration of installment options at the point of sale can drive further engagement.

*   **Cluster 3 – Cash Advance Seekers**: This segment poses a higher credit risk due to their reliance on cash advances and lower full payment ratios. Strategies for this group should prioritize **credit risk assessment and education on alternative financial solutions**. Companies might consider offering personal loan alternatives at more favorable rates than cash advances, providing financial literacy resources, or implementing stricter controls on cash advance limits. The aim is to mitigate risk while guiding these customers towards healthier financial behaviors.

Overall, this segmentation enables a shift from mass marketing to a **precision marketing approach**, leading to improved customer satisfaction, reduced churn, and enhanced profitability through optimized resource allocation.

### 4.2. Limitations and Future Work

While this study provides valuable insights, it is subject to certain limitations that also open avenues for future research:

*   **Data Scope**: The analysis was based on a single dataset. Future work could involve integrating additional data sources, such as demographic information, external credit scores, or online browsing behavior, to enrich the customer profiles and potentially uncover more granular segments.

*   **Clustering Algorithm Selection**: Although K-Means proved effective, other advanced clustering techniques (e.g., hierarchical clustering, Gaussian Mixture Models, or self-organizing maps) could be explored to compare their performance and interpretability. Further fine-tuning of DBSCAN parameters or exploring other density-based methods might also yield better results for outlier detection.

*   **Dynamic Segmentation**: Customer behavior is not static. Future research could explore dynamic segmentation models that track changes in customer behavior over time, allowing for real-time adjustments to marketing and risk management strategies. This could involve time-series clustering or incorporating supervised learning models for churn prediction, as suggested in the original project's future work.

*   **Deployment and Monitoring**: The current project focuses on analysis. A practical extension would involve deploying the segmentation model into a production environment, building interactive dashboards (e.g., using Plotly/Dash) for business users, and establishing a robust monitoring system to track segment performance and model drift.

*   **Causal Inference**: This study identifies correlations and groupings. Future research could delve into causal inference to understand *why* certain behaviors lead to specific segment memberships, which could inform even more proactive and preventative strategies.




## 5. Conclusion

This research successfully demonstrated the application of unsupervised machine learning, specifically K-Means clustering combined with Principal Component Analysis, to segment credit card customers based on their behavioral data. By identifying four distinct customer segments—Loyal Spenders, Low-Engaged Users, Installment Spenders, and Cash Advance Seekers—this study provides a robust framework for credit card companies to move beyond generic marketing and risk management strategies. The detailed characterization of each segment offers actionable insights, enabling the development of personalized product offerings, targeted marketing campaigns, and more effective risk mitigation strategies. While the project successfully achieved its primary objective, the identified limitations and proposed future work highlight the continuous evolution of customer analytics and the potential for even more sophisticated and dynamic segmentation approaches. Ultimately, this research underscores the significant value of data-driven insights in fostering stronger customer relationships and driving sustainable growth in the competitive financial services industry.


