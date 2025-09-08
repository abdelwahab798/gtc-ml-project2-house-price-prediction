# 🏡 California Housing Price Prediction  

## 📌 Objective  
Build a machine learning model to predict **California house prices** using demographic and geographic features from the California Housing dataset.  

---

## 📂 Dataset  
The dataset used is `housing.csv` and contains the following columns:  

- `longitude`, `latitude` → Geographic location  
- `housing_median_age` → Median age of houses  
- `total_rooms`, `total_bedrooms` → Total rooms / bedrooms  
- `population` → Total population  
- `households` → Number of households  
- `median_income` → Median income  
- `median_house_value` → House value (target variable)  
- `ocean_proximity` → Proximity to the ocean  

---

## 🔧 Data Preprocessing  

1. **Handling Missing Values**  
   - Missing values were found in `total_bedrooms`.  
   - Filled missing values with the **median** of each `ocean_proximity` group.  

2. **Data Cleaning**  
   - Converted negative values in `longitude` to positive using `.abs()`.  

3. **Encoding**  
   - Converted the categorical column `ocean_proximity` into numeric values using **one-hot Encoding**.  

---

## 📊 Exploratory Data Analysis (EDA)  

- Used **Boxenplots** to detect outliers across features.  
- Created **Scatter plots** between `median_house_value` and:  
  - `latitude`, `longitude`, `housing_median_age`, `total_rooms`, `total_bedrooms`, `population`, `households`, `median_income`.  
- Created a **Countplot** to show the distribution of `ocean_proximity`.  

---

## 🏗️ Feature Engineering  

New features were created to improve model performance:  

- `width&length = longitude * latitude`  
- `rooms_without_bedrooms = total_rooms - total_bedrooms`  
- `population_per_household = population / households`  
- `bedrooms_per_room = total_bedrooms / total_rooms`  

---

## 🤖 Modeling  

Several models were trained and compared:  

### 🔹 Linear Regression  
- MAE: **50,781**  
- MSE: **5.16e9**  
- R²: **0.606**  

### 🔹 XGBoost (Default Parameters)  
- MAE: **30,957**  
- MSE: **2.21e9**  
- R²: **0.831**  

### 🔹 XGBoost (Tuned Parameters)
- MAE: **29,351**  
- MSE: **2.02e9**  
- R²: **0.846**  
Hyperparameters:  
```python
n_estimators=500,
learning_rate=0.05,
max_depth=6,
subsample=0.8,
colsample_bytree=0.8,
random_state=42
