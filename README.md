## Practical Application of Machine Learning Algorithms - Classification Task
<a href="https://github.com/kfmatovic716/BANK-MARKETING-CAMPAIGN.git"><h2>PORTUGUESE BANK MARKETING CHURN</h2></a>

<img src="/images/bank.png"/>

## MAIN OBJECTIVES
<ul>
    <li>To classify and predict whether the customer is to subscribe or not subscribe in a term deposit</li>
    <li>To compare the performance of several machine learning classifiers, specifically K-Nearest Neighbors, Logistic Regression, Decision Trees, and Support Vector Machines, in order to evaluate their effectiveness for the given task </li>
    <li>To enhance model performance and reliability by applying cross-validation techniques and conducting hyperparameter tuning using GridSearchCV</li>
</ul>

## DATA ACQUISITION
<ul>
    <li><strong>SOURCE:</strong> UCI Machine Learning repository from a Portuguese Bank institution ➡️ <a href="https://archive.ics.uci.edu/dataset/222/bank+marketing"><strong style="font-size: 16px;">BANK MARKETING</strong></a></li>
    <li><strong>DATA SIZE:</strong> There are 41,188 records and 21 features</li>
    <li><strong>DESCRIPTION:</strong> The dataset consists of the outcomes of 42 phone-based marketing campaigns conducted to promote term deposits. During these campaigns, clients were contacted by representatives to assess their interest, and their responses—indicating whether or not they subscribed—were recorded. </li>
</ul>

## DATA PREPARATION AND ANALYSIS
<ul>
    <li>There are no missing values in the dataset</li>
    <li>There were 12 duplicates removed; Therefore, <strong>new dataset count is 41,176</strong></li>
    <li>Dropped features that were not relevant to the modelling and renamed target variable name 'y' to 'subscription'</li>
    <li>Focusing on 9 feartures (age, job, marital, education, default, housing loan, personal loan, duration, campaign) and the target variable, subscription</li>
    <li>There is definitely an imbalance in the target variable (subscription) since there was only 11% in the data who have subscribed to term deposit and 89% who did not subscribe</li>
    <img src="/images/subscription_dist.png"/>
    <li>The age distribution in histogram between 30 and 40 are at the highest in participation of subscription to term deposit. Some outliers from age 79+ were also found to be subscribing in term deposit  </li>
    <img src="/images/age.png"/>
    <li>Most married and single people have the interest in subscribing in term deposit </li>
    <img src="/images/marital.png"/>
    <li>University and high school graduates and professionls are more likely to subscribe to term deposit. </li>
    <img src="/images/education.png"/>
    <li>Administrative, blue collar, technician and the retired are more likely to subscribe in term deposit than any other job. Other jobs might not have enough cushion to save money and use it for term deposits. </li>
    <img src="/images/job.png"/>
    <li>Most clients, regardless of housing loan status, did not subscribe to the term deposit. However, among those who did subscribe, a slightly higher proportion came from clients without housing loans compared to those with housing loans. Clients with unknown housing loan status were very few and showed almost no interest in subscription  </li>
    <img src="/images/housing.png"/>
     <li>Clients without a personal loan make up the largest share of the dataset, and while most of them did not subscribe, they still account for the majority of the subscriptions. Clients with a personal loan represent a much smaller group, and their subscription rate appears even lower. </li>
    <img src="/images/personal_loan.png"/>
    <li>Subscriptions are almost entirely concentrated among clients who are not in default. Clients who defaulted on their loans did not subscribe to the term deposit. </li>
    <img src="/images/default.png"/>
    <li>t appears that successful subscriptions occur in the first few contacts of the marketing campaigns. Clients who did not subscribe tended to receive more repeated contacts, with some extreme cases exceeding 40-50 calls. This suggests that additional campaign attempts beyond a few do not significantly increase the likelihood of subscription
</li>
    <img src="/images/campaign.png"/>
</ul>

## MODELING 


## COMPARISON OF CLASSIFICATION ALGORITHMS


## EVALUATION

## RECOMMENDATIONS TO CLIENT


## FUTURE RECOMMENDATIONS REGARDING DATA QUALITY
