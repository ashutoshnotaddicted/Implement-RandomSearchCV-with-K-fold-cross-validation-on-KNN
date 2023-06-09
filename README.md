# Implement-RandomSearchCV-with-K-fold-cross-validation-on-KNN

1. First, I generate 10 unique values using a uniform random distribution within the given range "param_range" (a tuple like (a,b) where a < b). These generated values are stored as "params".

2. Next, I divide the numbers ranging from 0 to the length of the x_train array into "folds" number of groups. For example, if folds=3 and the length of x_train is 100, I divide the numbers from 0 to 100 into 3 groups: group 1 (0-33), group 2 (34-66), and group 3 (67-100).

3. For each hyperparameter generated in step 1, I perform cross-validation using the groups created in step 2. Here's how the cross-validation is done:

   a. First, I combine group 1 and group 2 (0-66) as the training data and use group 3 (67-100) as the test data. I calculate the training and test accuracies.
   
   b. Next, I combine group 1 and group 3 (0-33, 67-100) as the training data and use group 2 (34-66) as the test data. Again, I calculate the training and test accuracies.
   
   c. Finally, I combine group 2 and group 3 (34-100) as the training data and use group 1 (0-33) as the test data. I calculate the training and test accuracies.
   
   I repeat this process based on the value of "folds" specified.

   For each hyperparameter, I find the mean of the training accuracies from the above three steps and store it in a list called "train_scores". Similarly, I find the mean of the test accuracies and store it in a list called "test_scores".

4. After performing cross-validation for all the generated hyperparameters, I return both the "train_scores" and "test_scores" lists.

5. Now, I call the function RandomSearchCV(x_train, y_train, classifier, param_range, folds) and store the returned values into variables called "train_scores" and "cv_scores".

6. I plot the hyperparameter values on the x-axis and the corresponding accuracy scores on the y-axis to create a hyperparameter vs. accuracy plot. This plot helps in visualizing the relationship between the hyperparameter values and the model's accuracy. From this plot, I can choose the best hyperparameter value.

7. Finally, I plot the decision boundaries for the model initialized with the best hyperparameter. This helps visualize how the model separates different classes or groups in the input data.
