INTRODUCTION

The telecommunications company Telco finds itself facing a pressing challenge – a significant 26% of its customer base has opted to discontinue services in the last month. Recognising the critical need to address this surge in customer churn, Telco has decided to leverage data science in understanding and mitigating this trend.

Telco provided a data set with the following information:

* Customers who left within the last month 
* Services that each customer has signed up for
* Customer account information: How long they have been a customer, contract, payment method, paperless billing, monthly charges, and total charges
* Demographic info: Gender, age range, and if customers have partners and dependents

The mission is clear: develop predictive models to understand which customers are more likely to switch to competitors and what factors contribute to it. This data-driven approach will empower Telco to make informed decisions, implement targeted strategies, and proactively engage with customers to address their concerns and increase customer satisfaction.

The contributions of the customer churn prediction models will play a pivotal role in not only reshaping Telco's customer retention strategies but also building a more resilient and customer-centric telecommunications ecosystem.

SEGMENTATION ANALYSIS

In the context of a customer churn prediction project, clustering can be relevant for several reasons:

- Identifying Customer Segments: Clustering can help identify distinct groups or segments of customers with similar behavior, preferences, or characteristics. Understanding these segments can provide valuable insights into the different types of customers Telco has.

- Feature Engineering: Clustering can be used to create new features for predictive modeling. For example, assigning a cluster label to each customer can serve as an additional feature that captures the inherent patterns within the data.

- Targeted Marketing Strategies: Once customer segments are identified, businesses can tailor their marketing strategies and retention efforts to address the specific needs and preferences of each cluster. This can improve the effectiveness of retention campaigns.

- Risk Assessment: Clustering can help in assessing the risk of churn for different customer segments. Some segments may be more prone to churn than others, and this information can be valuable in prioritizing efforts to retain high-risk customers.

- Model Calibration: By incorporating cluster information into predictive models, the model's accuracy in predicting customer churn may be improved. The distinct characteristics of each cluster can be used to fine-tune model parameters and enhance its predictive power.

- Anomaly Detection: Clustering can help identify outliers or anomalies within the data, which may represent unusual customer behavior. Detecting these anomalies early on can be crucial in predicting and preventing customer churn.

K-Means algorithm has been used for clustering analysis in this project given its simplicity, efficiency, scalability, versatility and intuitiveness. However, it's essential to note that K-Means has some limitations. It assumes spherical clusters of similar sizes, and its performance may degrade with non-linear or irregularly shaped clusters. The number of clusters (K) needs to be specified in advance. We have selected three clusters considering both inertia plots and silhouette diagrams.

The 3 clusters identified are the following:

| Cluster 0: Long-term Enthusiasts                                    | Cluster 1: Value-Oriented Traditionalists                    | Cluster 2: Dynamic Explorers                               |
| ----------------------------------------------------------------    | ------------------------------------------------------------ | -------------------------------------------------------- |
| **Description:** Long-term customers with higher spending.          | **Description:** Customers with moderate tenure and preference for lower-cost options. | **Description:** Customers with short tenure and high likelihood of churning. |
| **Key features:**<br>- DSL (38%) or Fiber optic (62%) services.<br>- Active users of various additional services.<br>- Engaged in longer-term contracts of 1 or 2 years (76%).<br>- Prefer automatic payment methods (Bank transfer and Credit card).<br>- Generally, have a higher probability of being loyal customers.                          | **Key features:**<br>- Customers who use only phone services (63%) or DSL (37%).<br>- Prefer Month-to-month contracts (49%).<br>- Show a preference for Mailed check payment methods (46%).<br>- Low likelihood of churning. | **Key features:**<br>- DSL (28%) or Fiber optic (72%) services.<br>- Less likely to have partners or dependents.<br>- Prefer Month-to-month contracts (89%).<br>- Lower use of additional services.<br>- High likelihood of churning (49% churned last month). |
| **Customer Profile:**<br>- Segmentation: Established and loyal customers.<br>- Behavior: Prefer stable and reliable services with a commitment to longer contracts.<br>- Potential Strategies: Offer loyalty rewards, promote additional services or upgrades. | **Customer Profile:**<br>- Segmentation: Moderate-term customers with basic service needs, particularly phone services.<br>- Behavior: Prefer flexibility with short-term commitments, cost-conscious.<br>- Potential Strategies: Offer promotions for extended contracts, upsell additional services for internet usage. | **Customer Profile:**<br>- Segmentation: Short-term tenure and highest level of Fiber optic usage.<br>- Behavior: Seek high-speed internet but with a tendency to churn.<br>- Potential Strategies: Focus on customer retention efforts, personalized offers to reduce churn. |

