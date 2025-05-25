# Data Analysis with Python  
## Cheat Sheet: Data Wrangling

A quick reference for common Pandas-based data-wrangling tasks.

| **Task**                          | **Description**                                                                                             | **Code Example**                                                                                                                                                                                                                           |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Replace missing data with frequency** | Fill NaNs with the column’s most common (mode) value.                                                    | ```python<br># find most frequent entry<br>MostFrequentEntry = df['attribute_name'].value_counts().idxmax()<br># replace NaNs<br>df['attribute_name'].replace(np.nan, MostFrequentEntry, inplace=True)```                                       |
| **Replace missing data with mean**      | Fill NaNs with the column’s average.                                                                      | ```python<br>AverageValue = df['attribute_name'].astype(float).mean(axis=0)<br>df['attribute_name'].replace(np.nan, AverageValue, inplace=True)```                                                                                       |
| **Fix data types**                       | Cast one or more columns to the correct dtype (int, float, etc.).                                        | ```python<br>df[['col1','col2']] = df[['col1','col2']].astype('float')```                                                                                                                             |
| **Data normalization**                   | Scale a numeric column to the [0, 1] range by dividing by its max.                                      | ```python<br>df['attribute_name'] = df['attribute_name'] / df['attribute_name'].max()```                                                                                                                 |
| **Binning**                              | Bucket a continuous column into discrete intervals (bins).                                               | ```python<br>bins = np.linspace(df['attribute_name'].min(), df['attribute_name'].max(), n+1)<br>labels = ['Low','Mid','High']<br>df['binned_col'] = pd.cut(df['attribute_name'], bins, labels=labels, include_lowest=True)```              |
| **Change column name**                   | Rename one or more columns.                                                                              | ```python<br>df.rename(columns={'old_name':'new_name'}, inplace=True)```                                                                                                                                 |
| **Indicator variables**                  | Turn a categorical column into one-hot (dummy) variables.                                                | ```python<br>dummies = pd.get_dummies(df['attribute_name'], prefix='attr')<br>df = pd.concat([df, dummies], axis=1)```                                                                                                         |

---

### How to use

1. **Clone** this repository  
   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
