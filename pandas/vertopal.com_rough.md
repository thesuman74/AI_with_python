---
jupyter:
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
  language_info:
    codemirror_mode:
      name: ipython
      version: 3
    file_extension: .py
    mimetype: text/x-python
    name: python
    nbconvert_exporter: python
    pygments_lexer: ipython3
    version: 3.11.5
  nbformat: 4
  nbformat_minor: 2
---

 
Creating a column
 

   
``` python
import pandas as pd 

df = pd.DataFrame() #empty data frame 

```
 

 
creating a column
 

   
``` python
df = pd.DataFrame(columns=['Name', 'Age'])  # creating a column with name and age 
df
```
 

 
adding values into columns - with column name (COlumn & ADD)
 

   
``` python
# Assigning single values
# df['Name'] = ['Suman']
# df['Age'] = [23]

# # Assigning Multiple values at once
df['Name'] = ['Alice', 'Bob', 'Charlie']  
df['Age'] = [22, 23, 24]



df
```
 

 
inserting column at specific index
 

   
``` python
# Create a date range
date_range = pd.date_range(start='2020-12-01', periods=len(df))

# Insert the "dates" column after the "Name" column
# df.insert(1, 'dates', date_range)       # index, colum_name, column_data
df
```
 

 
adding values into columns - with loc - (ROW & Replace )
 

   
``` python
df.loc[0] = ['Ram', 23] #addn value at first row by replacing 
df.loc[1] = ['Hari', 23] #addn value at second row by replacing 
df
```
 

 
Creating a dataframe and filling the dataframe with name and age
 

   
``` python
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age' : [21, 22, 23]
}
df = pd.DataFrame(data)
df
```
 

 
Locate row Pandas use the loc attribute to return one or more specified
row(s)
 

   
``` python
df.loc[1] # for single row 
df.loc[[1,2]] # returns multiple rows (from-to)
# df.loc['index_name'] # locating using named index for eg day1 | x 
```
 

 
Modify the index of data frame
 

   
``` python
df.index = ['X', 'Y', 'Z'] #modifying index name of existing dataframe 
print(df)

# # Specifying index name while creation of data frame 

# data = {
#   "calories": [420, 380, 390],
#   "duration": [50, 40, 45]
# }

# df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

# print(df) 
```
 

 
## Read Operation
 

   
``` python
df = pd.read_csv('data.csv') # loading csv data i.e csv ==> seperated by commas
df.head() # to display top 5 rows
print(df.to_string())  # to display all data 

# df = pd.read_json('data.json') #  json data sample ==> {"Duration":{"0":60,},   "Pulse":{"5":102},
```
 

 
## Data Cleaning

Data cleaning means fixing bad data in your data set.

Bad data could be:

Empty cells

-   Data in wrong format
-   Wrong data
-   Duplicates
 

 
identifying if null value exisits
 

   
``` python
df.head(10) #  true means null value exists 
```
 

   
``` python
# Count null values in the entire DataFrame
total_nulls = df.isnull().sum() #retruns no of empty value with column name
# total_nulls = df.isnull().sum().sum() #retruns no of empty value in total without column name 
print(f"Total null values in the DataFrame: {total_nulls}")
```
 

 
Removing rows with empty cells
 

   
``` python
new_df = df.dropna() # removes rows with empty values and creates a new data frame calle new_df 
# df.dropna(inplace = True)  # modifies the original data frame insted of creating new data frame 
print(new_df.to_string())
# new_df.isnull().sum()
```
 

 
Replacing empty cells with other values
 

   
``` python
replaced_df = df.fillna(130) # 130 is stored at all empty cells 
specific_rep_df = df["Calories"].fillna(130) # 130 is stored at empty cells in calories column
```
 

 
Replace Using Mean, Median, or Mode

-   Mean = the average value (the sum of all values divided by number of
    values).
-   Median = the value in the middle, after you have sorted all values
    ascending.
-   Mode = the value that appears most frequently.
 

   
``` python
# x = df["Calories"].mean()
# after_mean_df = df['Calories'].fillna(x)

# or 
after_mean_df = df["Calories"].fillna(df["Calories"].mean()) # replace empty strings with mean value in calories column

#similarly 
after_median_df = df["Calories"].fillna(df["Calories"].median()) # replace empty strings with median value in  calories column

after_mode_df = df["Calories"].fillna(df["Calories"].mode()[0]) # [0] returns the first mode value , sometimes multiple can exists

# for replacing empty cells with mean of their respective columns
after_meadian_df_all = df.fillna(df.mean())

after_meadian_df_all
```
 

 
## convert data of wrong format to correct format

To fix it, you have two options: remove the rows, or convert all cells
in the columns into the same format.
 

   
``` python
# for correcting wrong date format to correct one we can use 
df["date"] = pd.to_datetime(df['Date'])
```
 

   
``` python
# Create a date range
date_range = pd.date_range(start='2020-12-01', periods=len(df))

# Insert the "dates" column after the "Duration" column
# df.insert(1, 'dates', date_range)
# df.to_csv('data_with_dates.csv', index=False)

new_df = pd.read_csv('data_with_dates.csv')
new_df.to_string
```
 

 
Remove wrong data using loop, replacing every value from duration that
is greater than 110 with 104
 

   
``` python
for x in new_df.index:
  if new_df.loc[x, "Duration"] >= 110:
    new_df.loc[x, "Duration"] = 104

new_df
```
 

 
Removing Rows where we Delete rows where \"Duration\" is higher than 120:
 


``` python
for x in df.index:
  if df.loc[x, "Duration"] > 120:
    df.drop(x, inplace = True)
    
```

