# 🏡 Airbnb Price Prediction using Regression

This project builds a regression model to predict Airbnb listing prices based on various features such as location, room type, and availability. It showcases a complete end-to-end pipeline: from loading the dataset to feature engineering, model selection, and evaluation.

---

## 📂 Dataset Description

The dataset contains information on Airbnb listings. Each row represents a listing with the following features:

| Column Name                        | Description |
|-----------------------------------|-------------|
| `id`                              | Unique identifier for each listing |
| `name`                            | Name/title of the listing |
| `host_id`                         | Unique identifier for the host |
| `host_name`                       | Name of the host |
| `neighbourhood_group`            | Broad area or district |
| `neighbourhood`                  | Specific neighborhood |
| `latitude`                       | Geographical latitude |
| `longitude`                      | Geographical longitude |
| `room_type`                      | Type of accommodation (Entire home/apt, Private room, etc.) |
| `price`                          | Price per night |
| `minimum_nights`                 | Minimum required nights per stay |
| `number_of_reviews`              | Total reviews received |
| `last_review`                    | Date of the last review |
| `reviews_per_month`              | Average number of reviews per month |
| `calculated_host_listings_count`| Total listings managed by the host |
| `availability_365`              | Availability in days per year |

---

## ⚙️ Feature Engineering

The following transformations were applied:

- Converted `last_review` to datetime and extracted `year` and `month`.
- Filled missing values in `reviews_per_month` with 0.
- Removed outliers based on thresholds in `price`, `minimum_nights`, and `availability_365`.
- One-hot encoded categorical features: `neighbourhood_group`, `room_type`.
- Dropped high-cardinality and ID fields such as `id`, `name`, `host_id`, and `host_name`.

---

## 🧪 Modeling Pipeline

1. **Preprocessing**:
   - Missing value imputation
   - One-hot encoding
   - Outlier removal
   - Feature selection

2. **Train-Test Split**:
   - Data was split into training and testing sets using `train_test_split` from scikit-learn.

3. **Models Tested**:
   - Linear Regression
   - Ridge Regression
   - Lasso Regression
   - ElasticNet Regression
   - K-Nearest Neighbors
   - Decision Tree Regressor (CART)
   - Random Forest Regressor
   - Gradient Boosting Regressor
   - XGBoost Regressor

4. **Evaluation Metrics**:
   - MAE (Mean Absolute Error)
   - RMSE (Root Mean Squared Error)
   - R² Score
   - Execution Time

---

## 🏆 Model Selection & Results

After testing several regression models, **XGBoost Regressor** outperformed all others in both accuracy and efficiency:

| Model        | RMSE   | R² Score | MAE    | MSE    | Time (s) |
|--------------|--------|----------|--------|--------|----------|
| **XGBoost**  | **0.1068** | **0.9545** | 0.0429 | **0.0182** | 9.76     |
| RandomForest | 0.1066 | 0.9506   | **0.0272** | 0.0198 | 67.17    |
| CART         | 0.1472 | 0.9382   | 0.0331 | 0.0248 | 1.34     |
| GBM          | 0.1436 | 0.9325   | 0.0873 | 0.027  | 27.69    |
| Linear (LR)  | 0.1754 | 0.9084   | 0.1012 | 0.0367 | 0.22     |
| Ridge        | 0.1754 | 0.9084   | 0.1012 | 0.0367 | 0.14     |
| KNN          | 0.3456 | 0.712    | 0.2297 | 0.1154 | 1.15     |
| Lasso        | 0.6501 | -0.0004  | 0.494  | 0.4009 | 0.13     |
| ElasticNet   | 0.6501 | -0.0004  | 0.494  | 0.4009 | 0.17     |

> 📌 **Final Model Chosen**: `XGBoost Regressor`  
> 🎯 **Best R² Score**: `0.9545`  
> ⚡ **RMSE**: `0.1068`  
> ⏱️ **Execution Time**: `9.76 seconds`

---

## 🖥️ Sample Output

```python
Predicted Price: $134.67
Actual Price: $130.00
