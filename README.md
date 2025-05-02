# 🏡 Airbnb Price Prediction and Classification

This project implements both regression and classification models for Airbnb data analysis. The regression models predict listing prices based on various features, while the classification models categorize listings into different classes. The project showcases a complete end-to-end machine learning pipeline.

---

## 📂 Dataset Description

The dataset contains information on Airbnb listings in New York City. Each row represents a listing with the following features:

| Column Name | Description |
|-------------|-------------|
| `id` | Unique identifier for each listing |
| `name` | Name/title of the listing |
| `host_id` | Unique identifier for the host |
| `host_name` | Name of the host |
| `neighbourhood_group` | Broad area or district |
| `neighbourhood` | Specific neighborhood |
| `latitude` | Geographical latitude |
| `longitude` | Geographical longitude |
| `room_type` | Type of accommodation (Entire home/apt, Private room, etc.) |
| `price` | Price per night |
| `minimum_nights` | Minimum required nights per stay |
| `number_of_reviews` | Total reviews received |
| `last_review` | Date of the last review |
| `reviews_per_month` | Average number of reviews per month |
| `calculated_host_listings_count` | Total listings managed by the host |
| `availability_365` | Availability in days per year |

---

## ⚙️ Feature Engineering

The following transformations were applied:

- Converted `last_review` to datetime and extracted `year` and `month` features
- Filled missing values in `reviews_per_month` with 0
- Removed outliers based on thresholds in `price`, `minimum_nights`, and `availability_365`
- One-hot encoded categorical features: `neighbourhood_group`, `room_type`
- Created price category labels for classification models
- Dropped high-cardinality and ID fields such as `id`, `name`, `host_id`, and `host_name`

---

## 🧪 Regression Modeling Pipeline

1. **Preprocessing**:
   - Missing value imputation
   - One-hot encoding
   - Outlier removal
   - Feature selection

2. **Train-Test Split**:
   - Data was split into training and testing sets using `train_test_split` from scikit-learn

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

## 🎯 Classification Modeling Pipeline

1. **Data Preparation**:
   - Created discrete price categories for classification
   - Balanced class distribution using resampling techniques
   - Applied feature scaling

2. **Models Tested**:
   - Logistic Regression (LR)
   - K-Nearest Neighbors (KNN)
   - Decision Tree (CART)
   - Random Forest (RF)
   - Support Vector Machine (SVM)
   - Gradient Boosting Machine (GBM)
   - Naive Bayes (NB)
   - XGBoost
   - LightGBM
   - CatBoost

3. **Evaluation Metrics**:
   - Accuracy
   - Precision
   - Recall
   - F1-Score
   - Confusion Matrix

---

## 🏆 Regression Model Results

After testing several regression models, **XGBoost Regressor** outperformed all others in both accuracy and efficiency:

| Model | RMSE | R² Score | MAE | MSE | Time (s) |
|-------|------|----------|-----|-----|----------|
| **XGBoost** | **0.1068** | **0.9545** | 0.0429 | **0.0182** | 9.76 |
| RandomForest | 0.1066 | 0.9506 | **0.0272** | 0.0198 | 67.17 |
| CART | 0.1472 | 0.9382 | 0.0331 | 0.0248 | 1.34 |
| GBM | 0.1436 | 0.9325 | 0.0873 | 0.027 | 27.69 |
| Linear (LR) | 0.1754 | 0.9084 | 0.1012 | 0.0367 | 0.22 |
| Ridge | 0.1754 | 0.9084 | 0.1012 | 0.0367 | 0.14 |
| KNN | 0.3456 | 0.712 | 0.2297 | 0.1154 | 1.15 |
| Lasso | 0.6501 | -0.0004 | 0.494 | 0.4009 | 0.13 |
| ElasticNet | 0.6501 | -0.0004 | 0.494 | 0.4009 | 0.17 |

> 📌 **Final Regression Model**: `XGBoost Regressor`  
> 🎯 **Best R² Score**: `0.9545`  
> ⚡ **RMSE**: `0.1068`  
> ⏱️ **Execution Time**: `9.76 seconds`

---

## 🏆 Classification Model Results

The multi-class classification task yielded the following accuracy scores:

| Model | Accuracy |
|-------|----------|
| XGBoost | 0.67 |
| LightGBM | 0.67 |
| CatBoost | 0.68 |
| Random Forest | 0.66 |
| GBM | 0.66 |
| SVM | 0.64 |
| Logistic Regression | 0.65 |
| KNN | 0.62 |
| CART | 0.58 |
| Naive Bayes | 0.34 |

> 📌 **Final Classification Model**: `CatBoost`  
> 🎯 **Best Accuracy**: `0.68`  
> 📊 **Top Performing Models**: `CatBoost`, `LightGBM`, and `XGBoost`

---

## 🖥️ Sample Output

### Regression Output
```
Predicted Price: $134.67
Actual Price: $130.00
```

### Classification Output
```
Predicted Class: Premium
Actual Class: Premium
Confidence: 0.87
```

---

## 🛠️ Technologies Used

- **Programming Language**: Python 3.8+
- **Key Libraries**:
  - pandas, numpy - Data manipulation
  - scikit-learn - Machine learning algorithms
  - XGBoost, LightGBM, CatBoost - Advanced gradient boosting
  - matplotlib, seaborn - Data visualization
  - jupyter - Interactive development

---

## 📈 Future Improvements

- Implement neural network models for both regression and classification
- Add geospatial features using neighborhood data
- Create a web application for real-time predictions
- Incorporate natural language processing for listing descriptions
- Expand the model to other cities and regions

---

## 👥 Contributors

- Mustafa Samy (@mustafasamy28)

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
