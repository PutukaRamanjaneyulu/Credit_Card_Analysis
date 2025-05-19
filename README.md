# Credit_Card_Analysis
# Day 1


# 📊 Credit Card Data Analysis

This project performs **Exploratory Data Analysis (EDA)** and **data cleaning** on a credit card dataset to prepare it for further machine learning applications, such as risk prediction and customer segmentation.

---

## 📁 Dataset Overview

- **Original Size:** 150002 rows × 18 columns  
- **Final Cleaned Size:** 149980 rows × 17 columns  
- **Missing Data:** Handled in key columns like `MonthlyIncome` and `NumberOfDependents`  
- **Duplicate Records:** Removed

---

## 🔑 Key Features

- `NPA Status`: Indicates Non-Performing Asset (1 = default, 0 = non-default)
- `RevolvingUtilizationOfUnsecuredLines`: Unsecured line usage
- `age`, `Gender`, `Region`, `MonthlyIncome`
- `Rented_OwnHouse`, `Occupation`, `Education`
- Credit behavior columns:
  - `DebtRatio`
  - `NumberOfTime30-59DaysPastDueNotWorse`
  - `NumberOfTimes90DaysLate`
  - `NumberOfTime60-89DaysPastDueNotWorse`
  - `NumberRealEstateLoansOrLines`
  - `NumberOfOpenCreditLinesAndLoans`
  - `NumberOfDependents`
  - `Good_Bad`: Target column for classification

---

## 🧹 Data Cleaning Summary

- ✅ Removed duplicates using `.drop_duplicates()`
- ✅ Dropped redundant column: `MonthlyIncome.1`
- ✅ Handled missing values:
  - `MonthlyIncome`: filled using **mean**
  - `NumberOfDependents`: filled using **mode**
  - `Gender`: rows with missing values dropped
- ✅ Verified absence of nulls using `.isnull().sum()`

---

## 📊 Exploratory Data Analysis (EDA)

- Structure and Dimensions:
  - `.shape`, `.columns`, `.info()`
- Data Preview:
  - `.head()`, `.tail()`, `.sample()`
- Summary Statistics:
  - `.describe()`
- Null value detection and handling:
  - `.isnull().sum()`
- Statistical Overview:
  - Mean Monthly Income ≈ 6670.42  
  - Mode of `NumberOfDependents` = 0.0

---






**Target Variable:**  
- `Good_Bad` or `NPA Status`

**Evaluation Metrics:**
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

---

## 🧰 Technologies Used

- **Python** (Google Colab Notebook)
- **Pandas** for data manipulation
- **NumPy** for numerical operations
- **Matplotlib**, **Seaborn** (to be added) for visualization


---

Here is a **cell-by-cell breakdown** of the notebook content from your `Credit_card.ipynb` file, organized in a clear and structured way:

---

### 📘 **Cell-by-Cell Summary of the Notebook**
[Credit_card.ipynb - Colab.pdf](https://github.com/user-attachments/files/20278130/Credit_card.ipynb.-.Colab.pdf)

---

#### 📦 **Cell 1–3: Import Libraries**

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

* Loaded necessary libraries for data manipulation and visualization.

---

#### 📥 **Cell 4: Load Dataset**

```python
df = pd.read_csv('/content/creditcard.csv')
```

* Loaded the dataset into a Pandas DataFrame.
* Warning noted about mixed data types in one column.

---

#### 🧾 **Cell 5–8: Basic Dataset Info**

* **`df.shape`** → Returns `(150002, 18)` → 150002 rows, 18 columns
* **`df.columns`** → Lists all feature names
* **`df.size`** → Returns `2700036` → total elements in the dataset

---

#### 📊 **Cell 9: Dataset Info**

```python
df.info()
```

* Details data types and null counts.
* Noted missing values in:

  * `MonthlyIncome` (\~29k missing)
  * `MonthlyIncome.1` (duplicate column)
  * `NumberOfDependents` (\~3.9k missing)

---

#### 📐 **Cell 10: Descriptive Statistics**

```python
df.describe()
```

* Summary statistics for numeric columns like mean, std, min, max.

---

#### 🧾 **Cell 11–13: View Data**

* `df.head(20)` → Displays first 20 rows
* `df.tail(20)` → Displays last 20 rows
* `df.sample(20)` → Displays 20 random rows

---

#### 🧹 **Cell 14: Drop Duplicates**

```python
df = df.drop_duplicates()
```

* Removed duplicate rows.

---

#### 🧺 **Cell 15: Drop Redundant Column**

```python
df = df.drop('MonthlyIncome.1', axis=1)
```

* Removed the unnecessary duplicate column `MonthlyIncome.1`.

---

#### 📋 **Cell 16: Info After Column Drop**

```python
df.info()
```

* Dataset reduced to 17 columns.

---

#### 🔍 **Cell 17: Check Null Values**

```python
df.isnull().sum()
```

* Checked for null values again after dropping a column.

---

#### 🧼 **Cell 18: Drop Rows with Null `Gender`**

```python
df.dropna(subset='Gender', inplace=True)
```

* Removed rows with missing `Gender` values.

---

#### 📉 **Cell 19–20: Fill Missing MonthlyIncome**

```python
df['MonthlyIncome'].mean()
df['MonthlyIncome'] = df['MonthlyIncome'].fillna(df['MonthlyIncome'].mean())
```

* Filled missing values in `MonthlyIncome` using the mean (\~6670.42).

---

#### 👨‍👩‍👧 **Cell 21–22: Fill Missing `NumberOfDependents`**

```python
df['NumberOfDependents'].mode()[0]
df['NumberOfDependents'] = df['NumberOfDependents'].fillna(df['NumberOfDependents'].mode()[0])
```

* Filled missing `NumberOfDependents` using the mode (0.0).

---

#### ✅ **Cell 23: Final Null Check**

```python
df.isnull().sum()
```

* Confirmed all null values have been handled.

---

#### 👁️ **Cell 24–25: Final Data Preview**

```python
df.head(20)
df.tail(20)
```

* Displayed the top and bottom rows of the cleaned dataset.

---

#### 🎲 **Cell 26: Final Sample Check**

```python
df.sample(20)
```

* Displayed random rows to ensure data integrity.

---



## 📎 Author

Credit Card Data Analysis Project | EDA, Cleaning & Preparation for Modeling
