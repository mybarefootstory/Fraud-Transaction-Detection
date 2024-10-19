# Fraudulent Transaction Identification System

<h2>Goal:</h2> 
The primary aim of this project is to build a system that can efficiently detect fraudulent transactions in financial activities. By applying machine learning models and sophisticated data analysis methods, we strive to create a strong solution that enhances the safety and reliability of financial operations.

<h2>Execution:</h2>
For the execution of this idea, we obtained a dataset of financial transactions that consists of various attributes such as transaction type, amount, time, origin, destination, and additional contextual details. The data underwent preprocessing, followed by feature engineering to extract key features, and a machine learning model was trained on this labeled data to detect fraudulent transactions.
We employed a mix of supervised learning algorithms like logistic regression, decision trees, and ensemble methods such as XGBoost to train our models. The model learned patterns and trends from historical fraudulent activities, allowing it to predict new, unseen transactions. We tested the model's effectiveness using appropriate metrics, including accuracy, precision, recall, and F1-score, and performed parameter tuning to optimize its output. XGBoost provided the highest accuracy.

<h2>Use Cases:</h2>
The fraud detection system developed through this project has applications across the financial sector, including banks, online payment platforms, insurance, and e-commerce companies. It can be integrated with current transaction processing platforms to enable real-time identification of suspicious transactions and prevent fraud immediately.
This system can help financial institutions detect and halt fraudulent transactions, safeguard customers from fraud, and reduce financial losses. Moreover, it aids in fraud investigations by identifying fraudulent behavior and tracking down offenders.

<h2>Results:</h2>
<b>Performance Evaluation:</b> 
We assessed the performance of our models across training, validation, and testing datasets using multiple evaluation metrics. The results are as follows:<br><br>

<li>For Model Trained on df:<br>
Test Set:<br>
o Accuracy: 0.9987<br>
o F1 Score: 0.9987<br>
o ROC AUC Score: 0.9987<br><br>

<li>For Model Trained on df2:<br>
Test Set:<br>
o Accuracy: 0.9977<br>
o F1 Score: 0.9977<br>
o ROC AUC Score: 0.9977<br><br>

<b>Interpretation:</b> 
From the results, it's clear that the model trained on df (which includes all transaction types) performed better than the model trained on df2 (which focuses on transfers and cash-outs only) in terms of accuracy and F1 score. This highlights that including additional transaction types enhanced the model’s accuracy.
Both models, however, exhibited high levels of accuracy and F1 scores across both validation and test datasets, showcasing their proficiency in identifying fraudulent activities. The ROC AUC scores also indicate that the models are effective at distinguishing between fraudulent and legitimate transactions.<br><br>

<b>Key Feature Insights:</b> 
By studying the feature importance using XGBoost, we derived the following observations:<br>

<li>The feature diffOrg emerged as the most critical in determining fraud, followed by oldbalanceOrg, transaction amount, and newbalanceDest.</li>
<li>Interestingly, the isFlaggedFraud feature had a minimal contribution to model predictions, likely due to the low number of flagged instances.</li>
<li>Although the feature diffDest had a broader sample coverage and higher weight compared to CASH_IN, its gain was unexpectedly lower.</li>
<li>The step feature held a relatively higher weight, though its gain was lower, possibly due to the even distribution of fraudulent activities across the steps.</li><br><br>

<h2>Future Enhancements:</h2>
To further improve the fraud detection system, the following strategies could be explored:

<li>Increase data collection: Acquiring more data, especially for fraudulent transactions, can help increase the robustness of the model.</li>
<li>Advanced Techniques: Delve into more advanced methodologies such as anomaly detection or deep learning models to potentially uncover more intricate fraud patterns and boost detection rates.</li>
<li>Continuous model updates: Regularly update the model with fresh data to ensure it stays effective against evolving fraud tactics. Periodic retraining and tuning can keep the model accurate and adaptable.</li>
<li>Collaborating with industry professionals: Engaging with industry leaders, financial institutions, and cybersecurity experts can add valuable domain-specific knowledge to the solution, further strengthening the model.</li><br><br>

The ultimate objective is to build a continuously evolving and adaptive fraud detection system that helps create a safer financial environment.

<h2>Dataset Information:</h2>
We utilized the following dataset for this project:

```python
df = pd.read_csv('/content/data/Fraud.csv')
# shape the data
df.shape
(6362620, 11)
```
The dataset consists of the following key columns:

step: Represents the time step in hours, ranging from 1 to 744 (30 days simulation).
type: The type of transaction, which includes CASH-IN, CASH-OUT, DEBIT, PAYMENT, and TRANSFER.
amount: The transaction amount in the local currency.
nameOrig: The identifier for the account initiating the transaction.
oldbalanceOrg: The balance of the originating account before the transaction.
newbalanceOrig: The balance of the originating account after the transaction.
nameDest: The identifier for the receiving account.
oldbalanceDest: The balance of the destination account before the transaction.
newbalanceDest: The balance of the destination account after the transaction.
isFraud: A binary indicator showing whether the transaction was fraudulent (1) or legitimate (0).
isFlaggedFraud: A binary flag for transactions that attempted to transfer over 200,000 in a single transaction.
<h3>Acknowledgments:</h3> This work was greatly influenced by the repository [FraudTransactionsDetection by Prerna Mittal](https://github.com/prernamittal/FraudTransactionsDetection). We appreciate their contribution, which served as a foundation for our project. ```
