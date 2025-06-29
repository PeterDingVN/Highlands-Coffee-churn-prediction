# Few interesting update on my work!
## Some loopholes in my training and testing process so far
- Potential multi-collinearity:
  As described, my dataset contains "PPA", "Spending", "Fre#visit". Unluckily, PPA = Spending/Fre#visit.
  This relationship pose a risk of multicollinearity. So I decided to drop "Spending" and "Fre#visit" to maintain the lv of detail of my data
  while avoiding the risk of multicollinearity.
  Below is my data (numeric columns), after dropping. No high correlation detected (except for ID column, which might be deleted later).

  ![image](https://github.com/user-attachments/assets/beae6a4a-4269-405e-bedc-da578c1c1dc4)


- Update stratify split in train-test-split: This ensure the train and validation set will have the same ratio of churn/no-churn, making
  the final result more reliable.

- Use balanced_accuracy_score instead of accuracy_score: For imbalanced data, the former metric works better.

## Differences from previous run

![image](https://github.com/user-attachments/assets/35eecd2b-8cad-4c32-ac2a-bb6a0b0dd17e)

- Despite reduced accuracy, Gradient Boosting is still the optimal choice, with balanced_accuracy still above the accuracy of random guessing
  (all 0 - no churn)

- Interestingly, model performs better in test set than train test, the reason of which i'm still ignorant of.

Train set:

![image](https://github.com/user-attachments/assets/ef01f393-d73c-41fd-991b-8ea5ab45df6d)

![image](https://github.com/user-attachments/assets/0eb85466-af86-4f0f-ba03-2c92c7bfa95e)


Test set:

![image](https://github.com/user-attachments/assets/97ab52b5-569a-4200-b840-895b1441a159)

![image](https://github.com/user-attachments/assets/e29734b7-08c2-4faa-82ec-d141f63c9af0)






