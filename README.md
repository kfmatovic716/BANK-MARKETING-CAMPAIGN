## Practical Application of Machine Learning Algorithms - Classification Task
<h2><a href="https://github.com/kfmatovic716/BANK-MARKETING-CAMPAIGN.git">PORTUGUESE BANK MARKETING CHURN</h2></a></h2>

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

## FEATURE ENGINEERING
<ul>
    <li>Utilized LabelEncoder to transform the binary columns into numerical data</li>
    <li>Utilized OneHotEncoder to transform the categorical variables to numerical data</li>
    <li>Split the data and use StandardScale to scale the data</li>
</ul>

## SUMMARY OF MODEL EVALUATION


## MODELING RESULTS & EVALUATION
<ul>
    <li><strong>Baseline Model: Logistic Regression</strong></li>
        <ul>
            <li>Training and test accuracy are approximately 80%, which means that the model does not overfit and gneneralize to new data well.</li>
            <li>Based on the confusion matrix, the model caught many subscribers (true positives - 699) but missed some subscribers where model predicted a "no" but actually a "yes" (false negatives- 299). It also correctly predicted non-subscribers (true negatives - 5924) and predicted “yes” but actually “no” (false positive - 1384) </li>
            <li>With AUC = 0.87, the model is good at ranking positives higher than negatives</li>
            <li>With a recall of 0.75, the model is great at identifying subscribers, which is very important for marketing purposes. However, precision of 0.34 is low, where a large portion of predicted “yes” are actually “no”, which also means many unnecessary calls.</li>
             <li>It provides a balanced baseline that captured most of potential subscribers but also at the cost of contacting uninterested clients. If precision is crucial to business, which is reducing wasted effort, then threshold should be adjusted or explore a different model would be the next step.</li>
        </ul>
    <li><strong>K Nearest Neighbors</strong></li>
        <ul>
            <li>On the default n_neighbors=5 (without weights=balance), the model has good training performance (~87%) but test performace is low (~79%), a noticeable gap which suggests some overfitting. The model memorized the training data but generalizes less on new data. </li>
            <li>Speed of training is fast but not the best choice for high-dimensional, imbalanced data</li>
            <li>For heavily imbalanced data, applied SMOTE along with weighting strategies to improve minority-class recall. Using distance-based weights gave more power to closer neighbors compared to farther ones. However, after applying weights, the model achieved ~100% training accuracy but only about ~80% test accuracy, indicating that the model is overfitting. When tuning the number of neighbors to 20, training accuracy again was at ~100%, while test accuracy dropped further to around 79%, reinforcing the overfitting issue. Clearly, this model is not the best for this dataset. </li>
    <li><strong>Decision Tree Model</strong></li>
        <ul>
            <li>The training accuracy was ~100%, which indicated strong overfitting. The test accuracy was ~84%, way lower than the training accuracy. This means that the model does not generalize well with new data.</li>
            <li>Decision trees tend to create deep trees and memorize the training data, when not pruned, which explains the 100% training accuracy.</li>
            <li>Applied the class weight=balance and SMOTE to pay more attention to the minority class (subscription = yes)</li>
            <li>Applied hyperparameter tuning to improve model performance. The best parameter setting was ccp_alpha = 0.001, which introduced light pruning to prevent overfitting and remove weak branches. As a result, the pruned tree generalized much better than the unpruned version.</li>
            <li>It handles the majority class well but less with the minority class. It recovers more clients who agree to subscribe than before (recall=~54) at the cost of precision</li>
            <li>Overall accuracy is strong but majority class dominates. The model also has a good capability in ranking positives over negative (AOC ROC = ~84%)</li>
        </ul>
    <li><strong>Support Vector Machine</strong></li>
        <ul>
            <li>The training and test accuracy (~78%) are very close which means that there's no significant overfitting and the model generalizes well.</li>
            <li>With a recall of 81%, the model is great at finding actual subscribers, however at the cost of precision, which is low at ~32%.</li>
            <li></li>
        </ul>
</ul>


## RECOMMENDATIONS TO CLIENT
<ul>
    <li></li>
    <li></li>
    <li></li>
</ul>

## FUTURE RECOMMENDATIONS REGARDING DATA QUALITY
<ul>
    <li></li>
    <li></li>
    <li></li>
</ul>
