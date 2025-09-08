# PANDAS library
Pandas is a popular Python library for data manipulation and analysis.  
It excels at working with structured data, and its two primary data structures are the Series and the DataFrame.

## Series
A Series is a one-dimensional array-like object that can hold any data type.

```python
import pandas as pd

# Create a Series from a list
series = pd.Series([10, 20, 30, 40])
print(series)

$ 0    10
  1    20
  2    30
  3    40
  dtype: int64

# Create a Series from a numpy array
my_np_array = np.array([1.5, 2.5, 3.2, 4.8])
series = pd.Series(my_np_array)
print(series)

$ 0    1.5
  1    2.5
  2    3.2
  3    4.8
  dtype: float64

# Create a Series from a list, with indexes A, B, C, D
series = pd.Series([10, 20, 30, 40], index=['A', 'B', 'C', 'D'])
print(series)

$ A    10
  B    20
  C    30
  D    40
  dtype: int64
```

## Dataframe
The DataFrame is the most commonly used pandas object. A DataFrame is a two-dimensional, tabular data structure with labeled axes (rows and columns), similar to an Excel datasheeet.

```python
import pandas as pd
my_dictionary = {
        'col_A' : [1,2,3],
        'col_B' : [25,23,12],
        'col_C' : ['mon','tue','wed']
        }

# Create dataframe from dictionary
df = pd.DataFrame(my_dictionary)
print(df)

$     col_A  col_B col_C
   0      1     25   mon
   1      2     23   tue
   2      3     12   wed

# Import DataFrame from Excel
file_path = 'sales_data.xlsx'

# Import the specific sheet from the Excel file into a DataFrame
try:
    df = pd.read_excel(file_path, sheet_name='Q1_sales')
    print("DataFrame successfully imported:")
    print(df)
except FileNotFoundError:
    print(f"Error: The file '{file_path}' was not found.")
except Exception as e:
    print(f"An error occurred: {e}")
```

### Get information from the DataFrame

```python
# Get basic statistics about the dataframe, min, max etc.
df.describe()

$          col_A  col_B
     count   3.0    3.0
      mean   2.0   20.0
       std   1.0    7.0
       min   1.0   12.0
       25%   1.5   17.5
       50%   2.0   23.0
       75%   2.5   24.0
       max   3.0   25.0

# Get first N rows in dataframe
df.head(2)

$     col_A  col_B col_C
   0      1     25   mon
   1      2     23   tue

# Get last N rows in dataframe
df.tail(2)

$     col_A  col_B col_C
   1      2     23   tue
   2      3     12   wed

# Shape returns tuple with (#rows, #columns)
df.shape

$ (3, 3)

# Return all column names as a list	
df.columns

$ Index(['col_A', 'col_B', 'col_C'], dtype='object')
```

```
## Selection
df['col_a']		-- Select coloumn based on name
df[['col_a','col_b']]	-- Select several columns based on name
del df['col_a']		-- Delete coloumn
df.loc['row_a']		-- Locate row based on row name
df.iloc[int]		-- Locate row based on row index
df[0:5]			-- Select rows based on index ( :5 is first 5 rows, -5: is last 5 rows)

## Search
df[ df['col_a']>=10 ]			-- Select all rows where col_a>=10
df[ df['col_a']==df['col_a'].max() ]	-- Select all rows where col_a==col_a.max()

# Count
df.nunique()		-- Count the number of unique elements in every col
```
