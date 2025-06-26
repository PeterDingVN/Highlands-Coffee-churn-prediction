# Model evaluation
- Accuracy: 91%
- Precision: 86%
- Recall: 79%
Comparing to baseline model with accuracy at 76% only, the model outperforms randomness, meaning predictive value of the model itself.
Also, I conduct features analysis to find the features contributing most to churn behaviors and find out PPA (spend/visit) to be the most important factor.

![image](https://github.com/user-attachments/assets/582fcb6b-7941-42bf-8b65-fe39c443120a)

Therefore, Highlands Coffee should pay close attention to PPA in evaluating churns
Additionally, they should prioritize evaluating Frequency of visit over Spending when customers have quite similar PPA.

# Future improvements
There are several limitations to my model:
- Data:
  + The number of observations are limited, therefore the model might not be robust to future data as shown in the testing set.
  + The data is imbalanced with non-churn outnumbering churn. However, I did reduce the impact of this imnbalnce by using Stratified KFold. But future improvement in data collection can possibly help address this imblance
  + Choice of features: As in clustering part, the features used are mostly based on my understanding of FnB business. Future work could use statistical method in choosing features to improve its accuracy.

