<h1>Project Overview</h1>

In this repository, you'll find the code, analysis, and findings that contribute to Telco's journey in reshaping its customer retention strategies and securing a more sustainable future in the telecommunications market. If you don't have time to delve into the details immediately, please see a quick overview of the project below.

**INTRODUCTION**

What if a telecommunications company could predict and prevent customer churn, saving millions in potential lost revenue? This was the challenge faced by Telco as a staggering 26% of its customer base chose to discontinue services in the last month. 

**The Problem:**

![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/d5cc8aad-121d-4d76-8977-02b268729446)

Around 30% of future revenue, equivalent to approximately $1.7 million annually, has been lost due to customer churn. If this trend persists, the annual churn rate could reach a critical 97%, endangering the financial viability of the company. Fortunately, the industry benchmark for churn is 22%, providing Telco with the opportunity to realign and compete effectively.

**The Mission:**

To address this pressing issue, Telco has decided to leverage data science to understand and mitigate the surge in customer churn. Armed with a comprehensive dataset encompassing customer details, services, and demographics, the mission is clear: develop predictive models to identify customers likely to switch and understand the contributing factors.

**The Impact:**

These data-driven models will empower Telco to make informed decisions, implement targeted strategies, and proactively engage with customers. By reshaping customer retention strategies, Telco aims not only to meet the industry benchmark but also to build a more resilient and customer-centric telecommunications ecosystem.

The following section explores the outcomes of the segmentation analysis, which leverages clustering techniques to categorise Telco's customer base. The identified clusters offer valuable insights into customer behavior, preferences, and characteristics, laying the foundation for targeted and effective retention strategies.

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
| **Customer Profile** |<br>- Segmentation: Established and loyal customers with Internet services.<br>- Behavior: Prefer stable and reliable services with a commitment to longer contracts.<br>- Potential Strategies: Offer loyalty rewards, provide personalised offers. | <br>- Segmentation: Moderate-term customers with basic service needs, particularly phone services.<br>- Behavior: Prefer flexibility with short-term commitments, cost-conscious.<br>- Potential Strategies: Offer promotions for extended contracts, upsell additional services for internet usage. | <br>- Segmentation: Short-term tenure and highest level of Fiber optic usage.<br>- Behavior: Seek high-speed internet but with a tendency to churn.<br>- Potential Strategies: Focus on customer retention efforts, promote additional services or upgrades to reduce churn. |

For simplicty, the clusters can be visualised with two dimensions, monthly charges and tenure:

![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/f5a03706-ff15-4b95-8446-f20826a27b14)

The subsequent section delves into the churn prediction models, providing a comprehensive toolkit for Telco to combat customer churn effectively and make informed, data-driven decisions.

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

To construct the models, we have splitted the data into 80% and 20% for training and testing purposes, respectively. Testing data in machine learning is like giving a final exam to check if a computer program has really learned from its training and can handle new information accurately. Cross-validation has been implemented to optimise hyperparameters and reduce the likelihood of overfitting. Regularisation techniques and feature selection have been used when relevant. Multiple evaluation metrics have been considered when selecting the best model for each one of the algorithms.

To see how our models perform, we have evaluated them from both a statistical and business impact perspective.

1) Statistical Evaluation

Statistical evaluation of models is crucial in assessing the performance, reliability, and effectiveness of machine learning algorithms. It provides a quantitative basis for understanding how well a model generalises to new, unseen data. 

We plotted Precision-Recall (PR) curves for each optimised model within the testing data. These curves effectively visualise the trade-off between precision and recall for different models. Precision measures how many customers predicted to churn genuinely churned whereas Recall measures how many churned customers were accurately identified among all the churned customers. PR curves are useful in evaluating machine learning models, especially in scenarios where the class distribution is imbalanced, as it is in this case where one class (loyal customers) significantly outnumbers the other (churned customers). 

![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/593ccee3-dceb-445d-8233-4b203ab5715b)

PR curves help in selecting an appropriate decision threshold based on the specific needs of an application. The primary goal in churn prediction is to identify customers who are actually at risk of churning. Maximising recall ensures that you capture as many true positives (actual churners) as possible. This is crucial for implementing effective retention strategies and preventing customer churn.

While recall is important, precision should not be completely ignored. Precision is crucial for resource efficiency. In a telecommunications context, a false positive may lead to unnecessary and potentially costly retention efforts. Furthermore, incorrectly targeting non-churning customers as potential churners can lead to customer frustration and dissatisfaction.

In short, maximising recall is important for capturing as many true churners as possible but a balance between precision and recall needs to be considered to ensure a well-rounded and effective churn prediction model.
 
2) Business Impact Assessment (BIA)

Business Impact Assessment is crucial to ensure that machine learning models are aligned with the overarching goals and objectives of the organisation. It provides tools for Cost-Benefit Analysis, resource optimisation, risk mitigation and strategic decision-making.
  
This project includes a BIA framework that decision-makers can use to test different marketing strategies and retention campaigns. This BIA framework allows to use a wide range of scenarios and assumptions, simulating real-world conditions given it uses testing data that represents unseen and independent samples that the model has not encountered during training.

  Let's have a look at this BIA framework with an example that considers the following retention strategies for customers likely to churn according to our models:

  - Long-term Enthusiasts: Personalised offers for extended contracts
  - Value-Oriented Traditionalists: Offer promotions for extended contracts
  - Dynamic Explorers: Offer additional services for extended contracts

  For simplicity, we will  assume the following:
  
  - Retention conversion rate: From those customers who were going to churn and have been approached by our initiatives (i.e. True Positives), only 35% accept our offers, the other 65% leave the company.
  - Retention strategy costs: Equivalent to 10% of the monthly fees paid by the customers targeted by our initiatives, regardless the cluster they belong to.
  - Customer lifetime: The 35% of customers who accept the offers extend the contract for 2 years.
  - Budget: The company wants to spend a maximum of $85k in retention efforts, which represents a 15% of its annual marketing budget.

 Following this example, we can visualise the impact of our proposed retention campaign.

 The first subplot illustrates the estimated net income and retention costs for each model and target recall rate. A budget line is included in the plot, indicating the financial threshold that the business is willing to spend on retention efforts.

 The second subplot visualises the Return On Investment (ROI) for each model at different target recall rates. This will help us to measure the profitability of the investment, which is the estimated profit generated for true positives that have been convinced to stay, relative to its cost, which is the retention cost paid for these customers and the false positives. A ROI of 150% means that for every dollar you invested, you got 1.50 USD back.

 ![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/7bff1c49-91ce-4f9c-82ac-ba20e81fd59b)

A recall rate between 70% and 80% seems to be optimal in this scenario according to our estimations, generating strong financial results under the proposed budget. Beyond a recall rate of 80%, the trade-off between revenue generated and retention costs does no longer justify targeting new customers with our retention campaigns.

But what about the opportunity cost of not approaching those customers that could be retained if approached with our campaigns? Let's have a look at this.

The following plot aims to visualise the impact of false negatives on net income for each model. This will ensure that decision-makers consider the opportunity cost of not retaining customers and understand the trade-offs between reducing false negatives, lowering missed revenue but increasing retention costs, and reducing false positives, which would lead to the opposite outcome. 

![image](https://github.com/asanzribas/Customer-Segmentation-and-Churn-Prediction/assets/143028834/bb01f3b4-d1c9-41be-bcb0-4a2fc95e486d)


Considering the impact of false negatives highlights the urgency of developing retention campaigns. Under the current scenario, a 50% recall rate is needed to avoid losing money. Considering both adjusted Net Income and ROI with the impact of opportunity costs, an 80% recall rate is the optimal point.

However, the higher the retention conversion rate (assumed to be 35% in this scenario), the more incentive the business will have to take risks and target more members whereas the opposite is true if the retention conversion rate is assumed to be lower.

**CONCLUSIONS**

- The implementation of K-Means clustering yielded three distinct customer segments: Long-term Enthusiasts, Value-Oriented Traditionalists, and Dynamic Explorers.
- Each cluster presents unique characteristics, behaviors, and churn likelihoods, allowing Telco to tailor retention efforts to the specific needs of each group.
- The churn prediction models, emphasising on interpretability and model performance, provide decision-makers with a comprehensive toolkit to combat customer churn.
- The financial evaluation framework introduces a business-oriented dimension to the project, allowing Telco to not only identify effective retention strategies but also to gauge their financial viability.
- By aligning marketing strategies with the identified customer clusters and optimising retention campaigns based on the proposed evaluation framework, Telco is in a strong position to reverse the alarming trend of customer churn.

**NEXT STEPS AND RECOMMENDATIONS**

- Exploration of data sources: Incorporate more data sources to enhance the models. 
- Continuous model monitoring: Implement a robust monitoring system for the churn prediction models to ensure their ongoing accuracy. Regularly assess model performance using fresh data to identify any potential degradation in predictive power.
- Dynamic cluster adaptation: Periodically reevaluate and adapt the customer clusters based on the latest data to ensure that retention strategies remain aligned with the current customer landscape.
- Feature importance updates: Monitor and update the feature importance analysis regularly.
- Integration with customer interaction platforms: Integrate the predictive models with Telco's customer interaction platforms to enable real-time decision-making.
- Feedback loop implementation: Establish a feedback loop between the data science team and customer service teams. Collect feedback on the effectiveness of implemented retention strategies and use this information to refine and improve the models over time.
- Scenario-based sensitivity analysis: Conduct sensitivity analyses on key parameters, such as retention conversion rates and retention strategy costs, to understand the impact of variations in these factors on the financial outcomes.
- Customer feedback surveys: Implement customer feedback surveys to gather direct insights into the reasons behind churn. This qualitative information can complement the quantitative analysis, offering a more holistic understanding of customer motivations.
- Investment in customer experience: Consider investing in initiatives such as improved support services, user interface enhancements, or additional features to enhance overall customer experience.
- Collaboration across departments: Foster collaboration between the data science team, marketing, and customer service departments. This interdisciplinary approach ensures that insights from data science are effectively translated into actionable strategies.
