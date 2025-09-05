# PANDAS library
The Numerical Python library **numpy** typically shortened to **np** is a fundamental Python library for scientific computing.
It provides a powerful N-dimensional array object, to hold vectors and matrixes, and many useful tools for linear algebra.

```python
import pandas as pd
my_dictionary = {'col_A' : [1,2,3], 'col_B' : [25,23,12], 'col_C' : ['mon','tue','wed']}

# Create dataframe from dictionary
df = pd.DataFrame(my_dictionary)
print(df)

$     col_A  col_B col_C
   0      1     25   mon
   1      2     23   tue
   2      3     12   wed

## Pandas DataFrame

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

# COunt
df.nunique()		-- Count the number of unique elements in every col

```

## Creating
Numpy offers several functions to create arrays quickly


## Operations 
