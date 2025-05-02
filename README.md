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
   - Decision Tree Regressor
   - Random Forest Regressor
   - Gradient Boosting Regressor

4. **Evaluation Metrics**:
   - MAE (Mean Absolute Error)
   - RMSE (Root Mean Squared Error)
   - R² Score

---

## 🏆 Model Selection & Results

After testing several models, the **Random Forest Regressor** provided the best performance:

| Metric | Value |
|--------|-------|
| MAE    | 21.4  |
| RMSE   | 34.2  |
| R²     | 0.89  |

---

## 🖥️ Sample Output

```python
Predicted Price: $134.67
Actual Price: $130.00
