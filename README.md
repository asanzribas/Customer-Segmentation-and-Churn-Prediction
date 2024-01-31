**INTRODUCTION**

The telecommunications company Telco finds itself facing a pressing challenge – a significant 26% of its customer base has opted to discontinue services in the last month. Recognising the critical need to address this surge in customer churn, Telco has decided to leverage data science in understanding and mitigating this trend.

Telco provided a data set with the following information:

* Customers who left within the last month 
* Services that each customer has signed up for
* Customer account information: How long they have been a customer, contract, payment method, paperless billing, monthly charges, and total charges
* Demographic info: Gender, age range, and if customers have partners and dependents

The mission is clear: develop predictive models to understand which customers are more likely to switch to competitors and what factors contribute to it. This data-driven approach will empower Telco to make informed decisions, implement targeted strategies, and proactively engage with customers to address their concerns and increase customer satisfaction.

The contributions of the customer churn prediction models will play a pivotal role in not only reshaping Telco's customer retention strategies but also building a more resilient and customer-centric telecommunications ecosystem.

**SEGMENTATION ANALYSIS**

In the context of a customer churn prediction project, clustering can be relevant for several reasons:

- Identifying Customer Segments: Clustering can help identify distinct groups or segments of customers with similar behavior, preferences, or characteristics. Understanding these segments can provide valuable insights into the different types of customers Telco has.

- Feature Engineering: Clustering can be used to create new features for predictive modeling. For example, assigning a cluster label to each customer can serve as an additional feature that captures the inherent patterns within the data.

- Targeted Marketing Strategies: Once customer segments are identified, businesses can tailor their marketing strategies and retention efforts to address the specific needs and preferences of each cluster. This can improve the effectiveness of retention campaigns.

- Risk Assessment: Clustering can help in assessing the risk of churn for different customer segments. Some segments may be more prone to churn than others, and this information can be valuable in prioritizing efforts to retain high-risk customers.

- Model Calibration: By incorporating cluster information into predictive models, the model's accuracy in predicting customer churn may be improved. The distinct characteristics of each cluster can be used to fine-tune model parameters and enhance its predictive power.

- Anomaly Detection: Clustering can help identify outliers or anomalies within the data, which may represent unusual customer behavior. Detecting these anomalies early on can be crucial in predicting and preventing customer churn.

K-Means algorithm has been used for clustering analysis in this project given its simplicity, efficiency, scalability, versatility and intuitiveness. However, it's essential to note that K-Means has some limitations. It assumes spherical clusters of similar sizes, and its performance may degrade with non-linear or irregularly shaped clusters. The number of clusters (K) needs to be specified in advance. We have selected three clusters considering both inertia plots and silhouette diagrams.

The 3 clusters identified are the following:

| **Category** | Cluster 0: Long-term Enthusiasts | Cluster 1: Value-Oriented Traditionalists | Cluster 2: Dynamic Explorers |
| ------------ | -------------------------------- | ---------------------------------------- | ---------------------------- |
| **Description** | Long-term customers with higher spending. | Customers with moderate tenure and preference for lower-cost options. | Customers with short tenure and high likelihood of churning. |
| **Key features** |<br>- DSL (38%) or Fiber optic (62%) services.<br>- Active users of various additional services.<br>- Engaged in longer-term contracts of 1 or 2 years (76%).<br>- Prefer automatic payment methods (Bank transfer and Credit card).<br>- Generally, have a higher probability of being loyal customers. | <br>- Customers who use only phone services (63%) or DSL (37%).<br>- Prefer Month-to-month contracts (49%).<br>- Show a preference for Mailed check payment methods (46%).<br>- Low likelihood of churning. | <br>- DSL (28%) or Fiber optic (72%) services.<br>- Less likely to have partners or dependents.<br>- Prefer Month-to-month contracts (89%).<br>- Lower use of additional services.<br>- High likelihood of churning (49% churned last month). |
| **Customer Profile** |<br>- Segmentation: Established and loyal customers with Internet services.<br>- Behavior: Prefer stable and reliable services with a commitment to longer contracts.<br>- Potential Strategies: Offer loyalty rewards, promote additional services or upgrades. | <br>- Segmentation: Moderate-term customers with basic service needs, particularly phone services.<br>- Behavior: Prefer flexibility with short-term commitments, cost-conscious.<br>- Potential Strategies: Offer promotions for extended contracts, upsell additional services for internet usage. | <br>- Segmentation: Short-term tenure and highest level of Fiber optic usage.<br>- Behavior: Seek high-speed internet but with a tendency to churn.<br>- Potential Strategies: Focus on customer retention efforts, personalized offers to reduce churn. |

For simplicty, the clusters can be visualised with two dimensions, monthly charges and tenure:

![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/f5a03706-ff15-4b95-8446-f20826a27b14)

**CHURN PREDICTION**

In the context of a churn prediction project where interpretability and model performance are key priorities, three algorithms were chosen based on their unique strengths. 
<br>

**Logistic Regression** was selected for its high interpretability, as it provides clear insights into the impact of each feature on the likelihood of churn. This transparency can be crucial for understanding the driving factors behind customer attrition.
<br>

**Random Forest**, while sacrificing some interpretability compared to Logistic Regression, was chosen for its robustness and ability to handle non-linear relationships in the data. It also provides feature importance scores, aiding in the identification of key predictors. 
<br>

**Gradient Boosting** algorithms, such as XGBoost, strike a balance between interpretability and predictive power. Although not as interpretable as Logistic Regression, they offer strong performance in capturing complex patterns within the data. Feature importance scores and interpretability techniques contribute to understanding the model's decision-making process. 
<br>

All three algorithms are well-suited for handling imbalanced data, providing a comprehensive approach to churn prediction that aligns with the project's dual objectives of interpretability and performance.

1) Statistical Evaluation

The primary goal in churn prediction is to identify customers who are actually at risk of churning. Maximising recall ensures that you capture as many true positives (actual churners) as possible. This is crucial for implementing effective retention strategies and preventing customer attrition.

While recall is important, precision should not be completely ignored. Precision is crucial for resource efficiency. In a telecommunications context, a false positive may lead to unnecessary and potentially costly retention efforts. Furthermore, incorrectly targeting non-churning customers as potential churners can lead to customer frustration and dissatisfaction.

Maximising recall is important for capturing as many true churners as possible but a balance between precision and recall needs to be considered to ensure a well-rounded and effective churn prediction model.

 ![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/2f2b2410-3091-4510-a945-f5b8b1819886)
 
2) Financial Evaluation
  
  This project includes an evaluation framework that decision-makers can use to test different marketing strategies and retention campaigns. This evaluation framework allows to use a wide range of scenarios and assumptions.

  Let's have a look at this evaluation framework with an example that considers the following retention strategies for customers likely to churn according to our models:

  - Long-term Enthusiasts: Offer loyalty rewards
  - Value-Oriented Traditionalists: Offer promotions for extended contracts
  - Dynamic Explorers: Personalized offers

  For simplicity, we will  assume the following:
  
  - Retention conversion rate: From those customers who were going to churn and have been approached by our initiatives (i.e. True Positives), only 35% accept our offers, the other 65% leave the company.
  - Retention strategy costs: Equivalent to 10% of the monthly fees paid by the customers targeted by our initiatives, regardless the cluster they belong to.
  - Customer lifetime: The 35% of customers who accept the offers extend the contract for 2 years.

 Following this example, and using only a 20% of our data to make these estimations (this is the part of the data used for testing purposes in our modelling), we can visualise the impact of our proposed retention campaign.

 The first subplot illustrates the estimated net income and retention costs for each model and target recall rate. A budget line is included in the plot, indicating the financial threshold that the business is willing to spend on retention efforts.

 The second subplot visualises the ROI for each model at different target recall rates. This will help us to measure the profitability of the investment, which is the estimated revenue generated for true positives that have been convinced to stay, relative to its cost, 
 which is the retention cost paid for these customers and the false positives. A ROI of 150% means that for every dollar you invested, you got 1.50 USD back.

 ![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/7bff1c49-91ce-4f9c-82ac-ba20e81fd59b)

A recall rate between 70% and 80% seems to be optimal in this scenario according to our estimations, generating strong financial results under the proposed budget. Beyond a recall rate of 80%, the trade-off between revenue generated and retention costs does no longer justify targeting new customers with our retention campaigns.

But what about the opportunity cost of not approaching those customers that could be retained if approached with our campaigns? Let's have a look at this.

The following plot aims to visualise the impact of false negatives on net income for each model. This will ensure that decision-makers consider the opportunity cost of not retaining customers and understand the trade-offs between reducing false negatives, lowering missed revenue but increasing retention costs, and reducing false positives, which would lead to the opposite outcome. 

![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/b31d5a18-e21a-4bfb-b92f-f9c7c3e901e3)

Considering the impact of false negatives highlights the urgency of developing retention campaigns. Under the current scenario, a 50% recall rate is needed to don't loose money. Considering both adjusted Net Income and ROI with the impact of opportunity costs, an 80% recall rate is the optimal point.

However, the higher the retention conversion rate (assumed to be 35% in this scenario), the more incentive the business will have to take risks and target more members whereas the opposite is true if the retention conversion rate is assumed to be lower.
