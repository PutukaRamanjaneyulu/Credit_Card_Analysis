# Credit_Card_Analysis
# Day 1


### 📊 **Data Analysis Summary: Credit Card Dataset (Python)**

#### ✅ 1. **Importing Required Libraries**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

#### 📂 2. **Loading the Dataset**

```python
df = pd.read_csv("/content/creditcard.csv")
```

* Loaded the dataset into a DataFrame named `df`.

#### 🔍 3. **Initial Data Exploration**

```python
df.head()
df.tail()
df.sample(3)
```

* Previewed the first few, last few, and random rows to understand the structure.

#### 🧩 4. **Checking for Null Values**

```python
df.isnull().sum()
```

* Identified columns with missing (null) values.

#### 🧼 5. **Handling Null Values**

* **Filled null values** in `MonthlyIncome` and `MonthlyIncome.1` with their respective column means:

  ```python
  df['MonthlyIncome'] = df['MonthlyIncome'].fillna(df['MonthlyIncome'].mean())
  df['MonthlyIncome.1'] = df['MonthlyIncome.1'].fillna(df['MonthlyIncome.1'].mean())
  ```
* **Dropped remaining null rows**:

  ```python
  df = df.dropna(axis=0)
  ```

#### 🧹 6. **Data Cleaning**

* Dropped an unnecessary column:

  ```python
  df_ = df.drop(['MonthlyIncome.1'], axis=1)
  ```

#### 🔄 7. **Replaced Specific Values (attempt)**

```python
df_new = df_.replace(to_replace="0.0,(df_['MonthlyIncome'].mean())")
```

> ⚠️ Note: This line may have an error in syntax. It seems like an incorrect attempt to replace values. Review needed.

#### 💾 8. **Saving the Cleaned Data**

```python
df_new.to_csv("Credit.csv", index=False)
```

#### 📊 9. **Visualization: Age Distribution**

```python
plt.hist(df_new['age'], bins=5, rwidth=0.7, color='black')
plt.title("Age Wise Count")
plt.xlabel("Age")
plt.show()
```

* Generated a histogram of the `age` column and saved it as an image.

---

### ✅ **Final Result**

* Missing values in `MonthlyIncome` were filled with the mean.
* Null rows were removed.
* Cleaned data was saved to a new CSV file `Credit.csv`.
* Data is now ready for further analysis or modeling.

