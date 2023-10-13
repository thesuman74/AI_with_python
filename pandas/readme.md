Sure, here's a structured list of CRUD operations in pandas using Markdown format:

**Create (C):**

- `pd.DataFrame(data)`: Create a DataFrame from a dictionary or other data structures.
```python
import pandas as pd

data = {'Name': ['Alice', 'Bob', 'Charlie'],
        'Age': [25, 30, 35]}

df = pd.DataFrame(data)
```

- `df.append(new_data)`: Add rows to an existing DataFrame.
```python
new_row = {'Name': 'David', 'Age': 28}
df = df.append(new_row, ignore_index=True)
```

- `df.insert(column, value)`: Add a new column to the DataFrame.
```python
df.insert(2, 'City', ['New York', 'San Francisco', 'Los Angeles', 'Chicago'])
```

**Read (R):**

- `pd.read_csv(file_path)`: Read data from a CSV file into a DataFrame.
```python
import pandas as pd

# Read data from a CSV file
df_csv = pd.read_csv('data.csv')
```

- `pd.read_excel(file_path)`: Read data from an Excel file into a DataFrame.
```python
import pandas as pd

# Read data from an Excel file
df_excel = pd.read_excel('data.xlsx')
```

- `df.head()`: Display the first few rows of the DataFrame.
```python
print(df.head())
```

- `df.tail()`: Display the last few rows of the DataFrame.
- `df.sample(n)`: Randomly sample 'n' rows from the DataFrame.
- `df.info()`: Display information about the DataFrame.
- `df.describe()`: Get summary statistics for numeric columns.
- `df.columns`: Get column labels.
- `df.shape`: Get dimensions (rows, columns) of the DataFrame.
- `df.dtypes`: Get data types of columns.
- `df.nunique()`: Get the number of unique values in each column.
- `df.isnull()`: Check for missing values in the DataFrame.

**Update (U):**

- `df.loc[row_indexer, column_indexer] = new_value`: Update specific cells in the DataFrame using row and column indexing.
- `df[column_name] = new_values`: Update an entire column with new values.
- `df.replace(old_value, new_value)`: Replace values in the DataFrame.
- `df.rename(columns=new_column_names)`: Rename columns in the DataFrame.

**Delete (D):**

- `df.drop(index)`: Remove rows by index.
- `df.drop(columns)`: Remove columns by name.
- `df.drop_duplicates()`: Remove duplicate rows.
- `df.dropna()`: Remove rows with missing values.
- `df.dropna(axis=1)`: Remove columns with missing values.

These functions and methods allow you to perform various CRUD operations on pandas DataFrames.