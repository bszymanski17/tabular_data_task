# Movie Project: Gross and Rating Prediction

## Project Overview
This project involves conducting Exploratory Data Analysis (EDA) and building models for two separate tasks.
The first is a regression task to predict movie revenue (gross),
and the second is a classification task to predict if a movie will get a high score (IMDB score of 7.5 or more).

## Data Preprocessing
The data preparation process included:
* Removing duplicate rows and cleaning outliers.
* Conducting correlation analysis.
* Encoding categorical variables and creating new features and applying variable transformation.
* Analyzing data consistency to ensure reliable model training.

## Task 1: Predicting Gross Revenue (Regression)
Several models were tested for this task. The best performance was achieved by **HistGradientBoosting**.

* **Results:** The model reached an **RMSLE of 1.3** and a **MAE of 22.4 million**.
* 
* **Most important variable:** The budget was identified as the most important variable for predicting revenue.
* 
* **Analysis and conclusions:** In some cases, the model significantly overestimated the gross revenue. However, most of these errors were caused by data issues rather than the model itself—for example, the gross value only reflected the opening weekend or belonged to another movie with the same title. This issue primarily affected movies with smaller budgets. To improve the model, several next steps were proposed,such as adding a binary variable for budgets under $10 million to better handle these observations, or increasing the weights of observations for correct rows that show large errors.
---

## Task 2: Predicting High Ratings (Classification)
The goal was to predict if a movie is a "hit" (IMDB score > 7.5). The final model used was **LightGBM**.

* **Results:** The model achieved an F1-score of 66%, which means precision and recall are relatively high and well-balanced.
* 
* **Most important variables:** Movie popularity metrics*were the most influential variables for this task.
* 
* **Analysis and conclusions:**  The model performed very well when the actual IMDB score was far from the threshold. However, when the value was close to the threshold, the model occasionally made errors. These mistakes often occurred because the model associated high popularity with a high score, which was not always true for certain movies. Recommended next steps include adding a variable to better identify actual success, such as ROI (Gross / Budget). Additionally, using binning for the 'title_year' variable is suggested so the model can focus on longer time periods rather than specific years, which was sometimes a source of errors.

## Tech Stack
* Language: Python
* Libraries: Pandas, NumPy, Scikit-learn, LightGBM, XGBoost, Matplotlib
