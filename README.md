# Egypt_Houses_Price_Project
# Egyptian Real Estate Price Prediction: A Regression Analysis

##  Overview

This project focuses on developing a robust Machine Learning model to **predict the sale price of real estate properties** (Apartments, Villas, Chalets, etc.) across various cities in Egypt. By leveraging key attributes such as size, location, type, and finishing status, we aim to provide an accurate predictor for potential buyers and sellers in the dynamic Egyptian housing market.

---

##  Project Pipeline

The analysis followed a comprehensive data science methodology:

1.  **Data Acquisition & Cleaning:** Initial data inspection, handling of missing values (replacing 'Unknown' with $\text{NaN}$), and removal of duplicates.
2.  **Data Preprocessing & Feature Engineering:**
    * Standardizing categorical values (e.g., unifying 'Standalone Villa' types).
    * **Advanced Feature Handling:** Logically inferring and mapping property **'Level'** (Floor) based on **'Type'** (e.g., Penthouses are 'Highest', Villas are 'Ground').
    * Converting categorical features (Type, City, Delivery Term) into numerical formats using **One-Hot Encoding**.
3.  **Outlier Treatment:** Applied the **Interquartile Range (IQR)** method specifically tailored for price analysis **per city** to ensure removal of unrealistic prices based on local market norms.
4.  **Exploratory Data Analysis (EDA):** Visualizing price distribution, feature correlation, and key market trends.
5.  **Model Training & Evaluation:** Training five different regression models and comparing performance metrics ($\text{R}^2$, $\text{MAE}$).

---

##  Key Features

The models were trained on the following property attributes:

| Feature | Data Type | Description |
| :--- | :--- | :--- |
| **Area** | Numerical | Property size in square meters. |
| **Bedrooms** | Numerical | Number of bedrooms. |
| **Bathrooms** | Numerical | Number of bathrooms. |
| **City** | Categorical | The property's geographical location. |
| **Type** | Categorical | Apartment, Villa, Chalet, Duplex, etc. |
| **Furnished** | Categorical | Furnished or Not Furnished. |
| **Delivery\_Term** | Categorical | Finishing status (Finished, Semi Finished, Core & Shell). |
| **Payment\_Option** | Categorical | Cash or Installment. |

---

##  Model Performance and Results

Five regression algorithms were benchmarked on the test data. The results confirm that ensemble tree-based models outperformed simpler linear models due to the non-linear complexity of real estate pricing.

| Model | $R^2$ Score (Test) | Mean Absolute Error (MAE) |
| :--- | :--- | :--- |
| Linear Regression | $0.514$ | $\sim 1.22$ Million EGP |
| Random Forest | $0.602$ | $\sim 964$ Thousand EGP |
| **XGBoost Regressor (Champion)** | **$0.644$** | **$\sim 973$ Thousand EGP** |

The **XGBoost Regressor** was selected as the final model, demonstrating the highest predictive power ($\mathbf{R^2 = 0.644}$) and a strong balance of performance and computational efficiency.

---

##  Key Market Insights (from EDA)

* **Location Dominance:** The **New Cairo - El Tagamoa** area and the **North Coast** collectively account for the largest volume of listings in the dataset.
* **Price Premium:** **Stand Alone Villas** and **Town Houses** consistently exhibit the highest average prices compared to other property types.
* **Finishing Value:** Properties designated as **'Finished'** maintain a significant price premium over properties in 'Semi Finished' or 'Core & Shell' states.

---

##  Future Work

Potential steps to further refine and deploy this project:

1.  **Hyperparameter Optimization:** Conduct thorough tuning (using techniques like $\text{GridSearchCV}$) on the **XGBoost** model to maximize its $\text{R}^2$ score.
2.  **Feature Importance Analysis:** Use the $\text{XGBoost}$ results to identify the **top 5 drivers** of property price, providing valuable market insight.
3.  **Deployment:** Develop a simple web application (using Flask or Streamlit) to allow users to interact with the trained model.
