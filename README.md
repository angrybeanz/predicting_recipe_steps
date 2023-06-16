# predicting_recipe_steps
Thie is an exploratory data analysis project for DSC80 at UCSD.

---

## Framing the Problem
For this project, I am predicting the number of steps (n_steps) in a recipe. Understanding the number of steps involved in a recipe can show how complex or difficult a recipe is, which is particualrly helpful for users when they're deciding whether or not they shouold try a new recipe. Because the number of steps is a continuous variable, I will treat this as a regression problem, and the primary metric I will use is the root mean squared error, or RMSE. Aside from the RMSE being a standard measure for regression problems and allowing for easier comparisons between different models, the RMSE is also measured in the number of steps your predictions are away from the true value, on average, which are the same units as the number of steps or our target variable. The RMSE also punishes larger errors in my predictions, which is helpful because the number of steps in a recipe are limited within a range (it is intuitively unlikely for the number of steps to range by a large amount), so it's important to avoid large errors in our predictions. The mean absolute error is also feasible, but it doesn't penalize large errors as much, and mean squared log error would only be a better metric if we were more concerned with getting lower number of step predictions correct. The RMSE gives us an idea of the average magnitude of prediction errors.

For the features that I will use in the baseline model, I could approach it the users' point of view as looking at this complete dataframe of other users' reviews, and picking a recipe based on all the information, and therefore keeping all columns as there aren't any features we wouldn't already know at the time of prediction. On the other hand, I could say that ratings and reviews come after the cooking process and thus shouldn't be included in the model, because it wouldn't be available to users until they actually cook it. For my project, the former approach seems more intuitigvely sound to me, so I will go with that.

---

## Baseline Model
For my baseline model, I used the features minutes and number of ingredients (n_ingredients), which are both quantitative variables. Intuitively, these features may impact the number of steps in the recipe because they would affect the complexity of the recipe itself. I use a simple linear regression using the two features because linear regression is a good base model to build on later on and good to compare with other more complex models. Linear regression is also simpler to interpret. I used 5-fold cross validation technique and the RMSE as an evaluation metric. From the results, I obtained an average rmse across the 5 folds as 5.8765900119831755, which means when training, the model's training predictions were off by 5.8765900119831755 steps. However, when tested on unseen data, the RMSE was 5.886873187360149. This means that, on average, our model's predictions were off by about 6 steps on new, unseen recipes. 

The difference of 6 steps seems to not amazing for the purposes of our model due to distribution of counts of number of steps to be right tailed, and most of the recipes have a range of between 2-30 steps, meaning there is room for improvement to decrease the difference. 6 steps could be quie significant for that small range of steps. The consequences of on average 6 extra or fewer steps could be significant because it could be considered a lot of extra or fewer steps in a range of 2-30 total steps. Therefore, I think the current model is not good, but it isn't terrible.

<iframe src="assets/distribution_of_steps.html" width=800 height=600 frameBorder=0></iframe>

---

## Final Model

---

## Fairness Analysis
