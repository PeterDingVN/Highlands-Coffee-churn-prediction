# Highlands-Coffee-churn-prediction
The model aims to help Highlands Coffee effectively predict potential churns, hence better focusing resources on customers who would bring most value to the company.

  
# Training process

## Dataset description
The original data contains 9 tables, varying in features, such as competitors information, customer demographic, customer behavior, ...
So, from the original sets, I created a new dataset containing only key features, focusing on describing the customers' characteristics:
- Demographic: Age, MPI_Mean_use (monthly personal income) , Occupation group (customer's job)
- Psychology: Needstate#group (Specific needs of customer)
- Perception: NPS#P3M (the score reveals how likely a customer recommend the brand to others), Comprehension (how customers comprehend the brand)
- Behavior: Fre#Visit (visit frequency), PPA (spend per visit), Spending (total spending of each customer), Companion (who customers go with when visiting Highlands)
Note that:
- Using data from Business Intelligence season 9, I built a clustering model to segment the customers into 2 groups before predicting their churn risk.
For privacy, I will not publish the dataset here, but I'll provide a detail description of the dataset.
- I deleted all null values because filling NaN using KNN imputation, median was not effective (each observation is one customer, so interpolation was not valid)
- I did standardize the dataset and carried out one-hot encoding to convert all categorical variables into binary format.

## Segmentation
I chose between 4 well-known algorithms: DBSCAN, KMeans, Agglomerative, Gaussian Mixture and finally chose KMeans.
I used Silhouette score and Davious-Bourdin score to mark each model:

KMeans:

![image](https://github.com/user-attachments/assets/79bfbea4-060a-4058-8ce1-db6ee3e45f02)

Agglomerative:

![image](https://github.com/user-attachments/assets/b629f13d-d971-403e-a37f-9683bbe06e61)

Gaussian Mixture:

![image](https://github.com/user-attachments/assets/f2c21b35-cb63-429c-a2d7-17aa795a5b15)

DBSCAN:

![image](https://github.com/user-attachments/assets/8f8852da-732d-46d4-a906-4b999638e590)

![image](https://github.com/user-attachments/assets/c4858982-6153-4a47-9977-0dd0604e652c)

Looking at the scores, DBSCAN (at epsilon > 7.5) and KMeans (at k = 2) seem the best.
However, since DBSCAN divided the data into 5 groups, way larger than 2 groups divided by KMeans, I chose KMeans for simplification. Below is the result after clustering.

![image](https://github.com/user-attachments/assets/bb77395b-b8ad-4ed6-b47e-6e7bd7798f2a)

## Churn prediction
### Algorithm selection
Since the clustering returned 2 segments of customers, with segment 1 significantly larger than segment 0 in number of observations, I used Stratified K-Fold to conduct cross-validation. This helped preserved the ratio in each folds, testing accuracy of model using different algorithms more precisely.

![image](https://github.com/user-attachments/assets/f42dda0c-ce7e-4927-a324-cdeffbfe6b74)

The result showed that Gradient Boosting could best balance between Recall and Precision, with highest accuracy. At the same time, I baselined the model using GB by guessing all 0 (no churn), which returned accuracy of only 76%, way lower than GB's accuracy at 86%.
Therefore, I chose this algorithm for its reliability.

### Hyper-param fine-tuning
I focused on 3 main hyper-parameters of GB, and found the following as optimal result:
- n-estimator: 300
- learning_rate = 0.15
- max-depth = 3

### Result

# Discussions
There are, however, some limitations to my methodology, which could be further improved in future work:
- 










