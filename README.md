# House-Price-Prediction-Week6
House price prediction project focused on feature engineering, feature selection, model optimization, and performance evaluation using Python and Scikit-learn.

# 🏠 House Price Prediction — Week 6

This project is part of my **AnalystLab Africa Data Science Internship — Week 6**, where the focus was on **Feature Engineering & Model Optimization**.

For this project, I continued working with a House Price dataset to see how creating better features, selecting relevant variables, and tuning machine learning models could affect prediction performance.

## 🎯 Objective

The main goal was to improve house price prediction by:

* Creating meaningful features from existing variables
* Transforming categorical and numerical features
* Selecting relevant features using RFE
* Training and comparing different regression models
* Optimizing a Random Forest model using GridSearchCV
* Evaluating model performance before and after optimization

## 📊 Dataset

The dataset contains information about houses and their characteristics, including:

* Area
* Number of bedrooms
* Number of bathrooms
* Number of stories
* Parking spaces
* Road access
* Guest room
* Basement
* Air conditioning
* Hot water heating
* Furnishing status
* Preferred area

The target variable is the **house price**.

## 🛠️ Feature Engineering

I created additional features to capture relationships that may not be obvious from the original variables.

### Features created

* **`area_log`** — log transformation of area to reduce the effect of extreme values and handle skewness.
* **`Area_per_Bedroom`** — area divided by the number of bedrooms.
* **`Bed_Bath_ratio`** — relationship between the number of bedrooms and bathrooms.

Categorical variables were also converted into numerical form using **one-hot encoding**.

## 🔄 Feature Transformation

The project included:

* Log transformation of the area variable
* One-hot encoding of categorical variables
* Standardization where appropriate
* Preparation of the dataset for machine learning models

The transformations were applied to make the variables more suitable for modelling and to ensure that the models received numerical and properly prepared inputs.

## 🎯 Feature Selection with RFE

I used **Recursive Feature Elimination (RFE)** to identify the features that contributed most to the model.

### Selected features

RFE selected the following 10 features:

* `bathrooms`
* `stories`
* `parking`
* `area_log`
* `mainroad_yes`
* `airconditioning_yes`
* `hotwaterheating_yes`
* `basement_yes`
* `furnishingstatus_unfurnished`
* `prefarea_yes`

Some of the features that were not selected included:

* `bedrooms`
* `Area_per_Bedroom`
* `Bed_Bath_ratio`
* `guestroom_yes`
* `furnishingstatus_semi-furnished`

This helped reduce the feature set and identify the variables that were more useful for prediction.

## 🤖 Models Evaluated

I compared the performance of:

* Linear Regression
* Random Forest Regression
* Optimized Random Forest Regression

For the Random Forest model, I used **GridSearchCV with cross-validation** to search for better hyperparameter combinations.

### Best Random Forest Parameters

```text
max_depth = None
min_samples_leaf = 2
min_samples_split = 5
n_estimators = 100
```

The best cross-validation R² score from the GridSearch was approximately:

**0.5984**

## 📈 Model Performance

The models were evaluated using:

* RMSE
* MAE
* R² Score

| Model                   |      RMSE |       MAE |        R² |
| ----------------------- | --------: | --------: | --------: |
| Linear Regression       | 1,328,873 |   971,765 | **0.651** |
| Random Forest           | 1,377,069 | 1,014,394 |     0.625 |
| Optimized Random Forest | 1,416,485 | 1,042,056 |     0.603 |

### What happened?

Interestingly, the GridSearch optimization did **not** improve the Random Forest model on the test set.

The optimized Random Forest had a lower R² and higher RMSE and MAE than the original Random Forest.

**Linear Regression achieved the best test performance among the models evaluated.**

This suggests that, for this particular dataset and the features used, a relatively simple linear model was able to generalize better than the more complex tree-based models.

## 💡 Key Lessons

One of my biggest takeaways from this project is that **more complex does not always mean better**.

I also learned that feature engineering and feature selection should be guided by the data rather than simply creating as many features as possible.

The RFE process helped me understand which variables were more useful, while GridSearchCV showed me that hyperparameter tuning does not automatically guarantee better test performance.

Most importantly, I learned to look at the actual evaluation results rather than assuming that the most complex or optimized model must be the best one.

## 🧰 Tools Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Jupyter Notebook

## 📁 Project Contents

```text
House-Price-Prediction-Week6/
│
├── House_Price_Week6.ipynb
├── README.md
└── model file(s)
```

## 🚀 Next Steps

Possible improvements include further feature engineering, testing additional regression algorithms, exploring regularization techniques, and investigating ways to improve the generalization of the models.

---

**Part of my AnalystLab Africa Data Science Internship — Week 6.**
