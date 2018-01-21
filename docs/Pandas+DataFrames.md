
[TOC]

---

**Foreword**

Code snippets and excerpts from the tutorial. Python 3. From DataCamp.

---

# What are Pandas Data Frames?

- a Pandas `DataFrame`.
- a Pandas `Series`: a one-dimensional labeled array capable of holding any data type with axis labels or index. An example of a Series object is one column from a DataFrame.
- a Numpy `ndarray`, which can be a record or structured
- a two-dimensional `ndarray `
- dictionaries of one-dimensional `ndarrays`, lists, dictionaries or Series.

`np.ndarray` is the actual data type, while `np.array()` is a function.

Besides the data that a DataFrame needs to contain, we can also specify the index and column names. The index, on the one hand, indicates the difference in rows, while the column names indicate the difference in columns.


```python
%pylab inline
import numpy as np
import pandas as pd
```

    Populating the interactive namespace from numpy and matplotlib



```python
import os

os.chdir('/home/ugo/Documents/Notebooks/DataCamp, Pandas tutorial/')

print(os.getcwd())
```

    /home/ugo/Documents/Notebooks/DataCamp, Pandas tutorial



```python
# A structured array
my_array = np.ones(3, dtype=([('foo', int), ('bar', float)]))
# Print the structured array
print(my_array['foo'])
```

    [1 1 1]



```python
# A record array
my_array2 = my_array.view(np.recarray)
# Print the record array
print(my_array2.foo)
```

    [1 1 1]


# Create a Pandas DataFrame

First, select the values that are contained in the lists that start with `Row1` and `Row2`, then select the index or row numbers `Row1` and `Row2`, and then the column names `Col1` and `Col2`.


```python
data = np.array([['','Col1','Col2'],
                ['Row1',1,2],
                ['Row2',3,4]])
print(data)
```

    [['' 'Col1' 'Col2']
     ['Row1' '1' '2']
     ['Row2' '3' '4']]



```python
print(pd.DataFrame(data=data[1:,1:],
                  index=data[1:,0],
                  columns=data[0,1:]))
```

         Col1 Col2
    Row1    1    2
    Row2    3    4



```python
# Take a 2D array as input to a DataFrame 
my_2darray = np.array([[1, 2, 3], [4, 5, 6]])
print(pd.DataFrame(my_2darray))
```

       0  1  2
    0  1  2  3
    1  4  5  6



```python
# Take a dictionary as input to a DataFrame 
my_dict = {1: ['1', '3'], 2: ['1', '2'], 3: ['2', '4']}
print(pd.DataFrame(my_dict))
```

       1  2  3
    0  1  1  2
    1  3  2  4



```python
# Take a DataFrame as input to a DataFrame 
my_df = pd.DataFrame(data=[4,5,6,7], index=range(0,4), columns=['A'])
print(pd.DataFrame(my_df))
```

       A
    0  4
    1  5
    2  6
    3  7



```python
# Take a Series as input to a DataFrame
my_series = pd.Series({"United Kingdom":"London", "India":"New Delhi", "United States":"Washington", "Belgium":"Brussels"})
print(pd.DataFrame(my_series))
```

                             0
    Belgium           Brussels
    India            New Delhi
    United Kingdom      London
    United States   Washington



```python
df = pd.DataFrame(np.array([[1, 2, 3], [4, 5, 6]]))
print(df)
```

       0  1  2
    0  1  2  3
    1  4  5  6



```python
# header
list(df.columns.values)
```




    [0, 1, 2]




```python
# Use the `shape` property
print(df.shape)
```

    (2, 3)



```python
# Or use the `len()` function with the `index` property
print(len(df.index))
# length = rows
```

    2



```python
# exclude the NaN
df[0].count()
```




    2



# Fundamental DataFrame Operations

## Select an Index or Column from a Pandas DataFrame


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A','B','C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9


### Element


```python
# Using `iloc[]`
print(df.iloc[0][0])
```

    1



```python
# Using `loc[]`
print(df.loc[0]['A'])
```

    1



```python
# Using `at[]`
print(df.at[0,'A'])
```

    1



```python
# Using `iat[]`
print(df.iat[0,0])
```

    1



```python
# Using `get_value(index, column)`
print(df.get_value(0, 'A'))
```

    1


### Row, Column


```python
# Use `iloc[]` to select a row
print(df.iloc[0])
```

    A    1
    B    2
    C    3
    Name: 0, dtype: int64



```python
# Use `loc[]` to select a column
print(df.loc[:,'A'])
```

    0    1
    1    4
    2    7
    Name: A, dtype: int64


# Add an Index, Row or Column to a Pandas DataFrame

## Add an Index to a DataFrame


```python
# Print out the DataFrame `df` to check it out
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
# Set 'C' as the index of the DataFrame
df.set_index('C')
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>C</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>6</th>
      <td>4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>9</th>
      <td>7</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>



## Add Rows to a DataFrame

But before...

- `loc` works on labels of an index. This means with `loc[2]`, we look for the values of the DataFrame that have an index labeled 2.
- `iloc` works on the positions in the index. This means with `iloc[2]`, we look for the values of the DataFrame that are at index '2'.
- `ix` is a more complex case: when the index is integer-based, we pass a label to `ix`. `ix[2]` then means that we are looking in the DataFrame for values that have an index labeled `2`. This is just like `loc`! However, if the index is not solely integer-based, `ix` will work with positions, just like `iloc`.


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), index= [2, 'A', 4], columns=[48, 49, 50])
print(df)
```

       48  49  50
    2   1   2   3
    A   4   5   6
    4   7   8   9



```python
# Pass `2` to `loc`
print(df.loc[2])
```

    48    1
    49    2
    50    3
    Name: 2, dtype: int64



```python
# Pass `2` to `iloc`
print(df.iloc[2])
```

    48    7
    49    8
    50    9
    Name: 4, dtype: int64



```python
# Pass `2` to `ix`
print(df.ix[2])
```

    Format Type              text
    Data Description         HTML
    Reader              read_html
    Writer                to_html
    Name: 2, dtype: object


Add a row.


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), index= [2.5, 12.6, 4.8], columns=[48, 49, 50])
print(df)
```

          48  49  50
    2.5    1   2   3
    12.6   4   5   6
    4.8    7   8   9



```python
# There's no index labeled `2`, so change the index at position `2`
df.ix[2] = [60, 50, 40]
print(df)
```

          48  49  50
    2.5    1   2   3
    12.6   4   5   6
    4.8   60  50  40



```python
# This will make an index labeled `2` and ADD the new values
df.loc[2] = [11, 12, 13]
print(df)
```

          48  49  50
    2.5    1   2   3
    12.6   4   5   6
    4.8   60  50  40
    2.0   11  12  13


## Add a Column to a DataFrame


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
# Use `.index`
df['D'] = df.index

# Print `df`
print(df)
```

       A  B  C  D
    0  1  2  3  0
    1  4  5  6  1
    2  7  8  9  2


Tell the DataFrame that it should take column A as its index.


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6]]), columns=[1,2,3])
print(df)
```

       1  2  3
    0  1  2  3
    1  4  5  6



```python
# Append a column to `df`
df.loc[:, 4] = pd.Series(['5', '6'], index=df.index)

# Print out `df` again to see the changes
print(df)
```

       1  2  3  4
    0  1  2  3  5
    1  4  5  6  6


## Reset the Index of a DataFrame


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), index= [2.5, 12.6, 4.8], columns=[48, 49, 50])
print(df)
```

          48  49  50
    2.5    1   2   3
    12.6   4   5   6
    4.8    7   8   9



```python
# Use `reset_index()` to reset the values
df.reset_index(level=0, drop=True)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>48</th>
      <th>49</th>
      <th>50</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



# Delete Indices, Rows or Columns From a Pandas Data Frame

## Delete an Index from a DataFrame

Because DataFrames and Series always have an index.

- Reset the index of a DataFrame (go back to the previous section to see how it is done) or
- remove the index name, if there is any, by executing del df.index.name,
- remove duplicate index values by resetting the index, dropping the duplicates of the index column that has been added to a DataFrame and reinstating that duplicateless column again as the index,
- and lastly, remove an index, and with it a row. This is elaborated in one of the next sections.


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [40, 50, 60], [23, 35, 37]]), 
                  index= [2.5, 12.6, 4.8, 4.8, 2.5], 
                  columns=[48, 49, 50])
print(df)
```

          48  49  50
    2.5    1   2   3
    12.6   4   5   6
    4.8    7   8   9
    4.8   40  50  60
    2.5   23  35  37



```python
df.reset_index().drop_duplicates(subset='index', keep='last').set_index('index')
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>48</th>
      <th>49</th>
      <th>50</th>
    </tr>
    <tr>
      <th>index</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>12.6</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>4.8</th>
      <td>40</td>
      <td>50</td>
      <td>60</td>
    </tr>
    <tr>
      <th>2.5</th>
      <td>23</td>
      <td>35</td>
      <td>37</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

## Delete a Column from a DataFrame


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
# Drop the column with label 'A'                  
df.drop('A', axis=1, inplace=True)
print(df)
```

       B  C
    0  2  3
    1  5  6
    2  8  9



```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
df.drop('A', axis=1, inplace=False)
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
# Drop the column at position 1
df.drop(df.columns[[1]], axis=1)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



## Remove a Row from a DataFrame 


```python
df = pd.DataFrame(data=np.array([[1, 2, 3, 4], [4, 5, 6, 5], [7, 8, 9, 6], [23, 50, 60, 7], [23, 35, 37, 23]]), 
                  index= [2.5, 12.6, 4.8, 4.8, 2.5], 
                  columns=[48, 49, 50, 50])
print(df)
```

          48  49  50  50
    2.5    1   2   3   4
    12.6   4   5   6   5
    4.8    7   8   9   6
    4.8   23  50  60   7
    2.5   23  35  37  23



```python
# Drop the duplicates in `df`
df.drop_duplicates([48], keep='last')
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>48</th>
      <th>49</th>
      <th>50</th>
      <th>50</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2.5</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
    </tr>
    <tr>
      <th>12.6</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4.8</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2.5</th>
      <td>23</td>
      <td>35</td>
      <td>37</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
# Drop the index at position 1
print(df.drop(df.index[1]))
```

       A  B  C
    0  1  2  3
    2  7  8  9



```python
df.reset_index(level=0, drop=True)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



# Rename the Index or Columns of a Pandas DataFrame


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
# Define the new names of columns
newcols = {
    'A': 'new_column_1', 
    'B': 'new_column_2', 
    'C': 'new_column_3'
}

# Use `rename()` to rename columns
df.rename(columns=newcols, inplace=True)

print(df)
```

       new_column_1  new_column_2  new_column_3
    0             1             2             3
    1             4             5             6
    2             7             8             9



```python
# Rename the index
df.rename(index={1: 'a'})
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new_column_1</th>
      <th>new_column_2</th>
      <th>new_column_3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>a</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
# Define the new names of columns
newcols = {
    'A': 'new_column_1', 
    'B': 'new_column_2', 
    'C': 'new_column_3'
}

# Use `rename()` to rename columns
df2 = df.rename(columns=newcols, inplace=False)

print(df)
print(df2)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9
       new_column_1  new_column_2  new_column_3
    0             1             2             3
    1             4             5             6
    2             7             8             9


# Format The Data in a Pandas DataFrame

## Replace All Occurrences of a String in a DataFrame


```python
df = pd.DataFrame(data=np.array([['OK','Perfect','Acceptable'], ['Awful','Awful','Perfect'], ['Acceptable','OK','Poor']]), columns=['Student1','Student2','Student3'])
print(df)
```

         Student1 Student2    Student3
    0          OK  Perfect  Acceptable
    1       Awful    Awful     Perfect
    2  Acceptable       OK        Poor



```python
# Replace the strings by numerical values (0-4)
df.replace(['Awful', 'Poor', 'OK', 'Acceptable', 'Perfect'], [0, 1, 2, 3, 4]) 
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student1</th>
      <th>Student2</th>
      <th>Student3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>4</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = pd.DataFrame(data=np.array([['1\n',2,'3\n'], ['4',5 ,'6\n'], ['7','8\n','9']]), columns=[0,1,2])
print(df)
```

         0    1    2
    0  1\n    2  3\n
    1    4    5  6\n
    2    7  8\n    9



```python
# Replace strings by others with `regex`
df.replace({'\n': '<br>'}, regex=True)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1&lt;br&gt;</td>
      <td>2</td>
      <td>3&lt;br&gt;</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6&lt;br&gt;</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>8&lt;br&gt;</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



## Remove Parts from Strings in the Cells of a DataFrame


```python
df = pd.DataFrame(data=np.array([[1,2,'+3b'], [4,5,'-6B'], [7,8,'+9A']]), columns=['class','test','result'])
print(df)
```

      class test result
    0     1    2    +3b
    1     4    5    -6B
    2     7    8    +9A



```python
# Delete unwanted parts from the strings in the `result` column
df['result'] = df['result'].map(lambda x: x.lstrip('+-').rstrip('aAbBcC'))

# Check out the result again
print(df)
```

      class test result
    0     1    2      3
    1     4    5      6
    2     7    8      9


Use `map()` on the column `result` to apply the lambda function over each element or element-wise of the column. The function in itself takes the string value and strips the `+` or `-` that’s located on the left, and also strips away any of the six `aAbBcC` on the right.

## Split Text in a Column into Multiple Rows in a DataFrame


```python
df = pd.DataFrame(data=np.array([[34,0,'23:44:55'], [22,0,'66:77:88'], [19,1,'43:68:05 56:34:12']]), columns=['Age','PlusOne','Ticket'])
print(df)                    
```

      Age PlusOne             Ticket
    0  34       0           23:44:55
    1  22       0           66:77:88
    2  19       1  43:68:05 56:34:12



```python
# Split out the two values in the third row
# Make it a Series
# Stack the values
ticket_series = df['Ticket'].str.split(' ').apply(pd.Series, 1).stack()
print(ticket_series)
```

    0  0    23:44:55
    1  0    66:77:88
    2  0    43:68:05
       1    56:34:12
    dtype: object



```python
# Get rid of the stack:
# Drop the level to line up with the DataFrame
ticket_series.index = ticket_series.index.droplevel(-1)
```


```python
# Make a series a dataframe 
ticketdf = pd.DataFrame(ticket_series)
```


```python
# Delete the `Ticket` column from a DataFrame
del df['Ticket']
```


```python
# Check out the new `df`
print(df)
```

      Age PlusOne
    0  34       0
    1  22       0
    2  19       1



```python
print(ticketdf)
```

              0
    0  23:44:55
    1  66:77:88
    2  43:68:05
    2  56:34:12



```python
# Join the ticket DataFrame to `df`
df.join(ticketdf)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>PlusOne</th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>34</td>
      <td>0</td>
      <td>23:44:55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>22</td>
      <td>0</td>
      <td>66:77:88</td>
    </tr>
    <tr>
      <th>2</th>
      <td>19</td>
      <td>1</td>
      <td>43:68:05</td>
    </tr>
    <tr>
      <th>2</th>
      <td>19</td>
      <td>1</td>
      <td>56:34:12</td>
    </tr>
  </tbody>
</table>
</div>



First, inspect the DataFrame at hand. The values in the last row and in the last column are a bit too long. It appears there are two tickets because a guest has taken a plus-one to the concert.

Take the `Ticket` column from the DataFrame `df` and strings on a space. This will make sure that the two tickets will end up in two separate rows in the end. Next, take these four values (the four ticket numbers) and put them into a Series object. That still doesn’t seem quite right. There are `NaN` values in there! Stack the Series to make sure they don’t have any `NaN` values in the resulting Series.

Next, stack the Series.

That is not ideal either. Drop the level to line up with the DataFrame.

Transform a Series to a DataFrame to make sure we can join it back to the initial DataFrame. However, to avoid having any duplicates in the DataFrame, delete the original `Ticket` column.

## Apply a Function to a Pandas DataFrame’s Columns or Rows


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
# A lambda function
doubler = lambda x: x*2

# Apply the `doubler` function to the `A` DataFrame column
df['A'].apply(doubler)
```




    0     2
    1     8
    2    14
    Name: A, dtype: int64




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
df.loc[0].apply(doubler)
```




    A    2
    B    4
    C    6
    Name: 0, dtype: int64




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
df.iloc[0].apply(doubler)
```




    A    2
    B    4
    C    6
    Name: 0, dtype: int64




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
df['A'].apply(doubler)
```




    0     2
    1     8
    2    14
    Name: A, dtype: int64




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
df.applymap(doubler)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>4</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8</td>
      <td>10</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>14</td>
      <td>16</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])

def doubler(x):
    if x % 2 == 0:
        return x
    else:
        return x * 2

# Use `applymap()` to apply `doubler()` to a DataFrame
df.applymap(doubler)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>2</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>10</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>14</td>
      <td>8</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Check the DataFrame
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9


# Create an Empty DataFrame

`numpy.nan` has type float.


```python
df = pd.DataFrame(np.nan, index=[0,1,2,3], columns=['A'])
print(df)
```

        A
    0 NaN
    1 NaN
    2 NaN
    3 NaN


Add an attribute.


```python
df = pd.DataFrame(index=range(0,4),columns=['A'], dtype='float')
print(df)
```

        A
    0 NaN
    1 NaN
    2 NaN
    3 NaN


# Does Pandas Recognize Dates when Importing Data?


```python
df = pd.read_csv('date.csv', header=0, parse_dates=True)
print(df)
```

         unit      date
    0  6.1101  02/08/16
    1  5.5277  08/07/16
    2  8.5186  09/05/16
    3  7.0032  20/03/16



```python
# or this option:
df = pd.read_csv('date.csv', header=0, parse_dates=['date'])
print(df)
```

         unit       date
    0  6.1101 2016-02-08
    1  5.5277 2016-08-07
    2  8.5186 2016-09-05
    3  7.0032 2016-03-20


The second code succeeded.

# When, Why and How we should Reshape a DataFrame

## Pivot a DataFrame

- Values: this argument allows to specify which values of the original DataFrame we want to see in the pivot table.
- Columns: whatever is passed to this argument will become a column in the resulting table.
- Index: whatever is passed to this argument will become an index in the resulting table.


```python
products = pd.DataFrame({'category': ['Cleaning', 'Cleaning', 'Entertainment', 'Entertainment', 'Tech', 'Tech'],
                        'store': ['Walmart', 'Dia', 'Walmart', 'Fnac', 'Dia','Walmart'],
                        'price':[11.42, 23.50, 19.99, 15.95, 55.75, 111.55],
                        'testscore': [4, 3, 5, 7, 5, 8]})
print(products)
```

            category   price    store  testscore
    0       Cleaning   11.42  Walmart          4
    1       Cleaning   23.50      Dia          3
    2  Entertainment   19.99  Walmart          5
    3  Entertainment   15.95     Fnac          7
    4           Tech   55.75      Dia          5
    5           Tech  111.55  Walmart          8



```python
# Use `pivot()` to pivot the DataFrame
pivot_products = products.pivot(index='category', columns='store', values='price')

# Check out the result
print(pivot_products)
```

    store            Dia   Fnac  Walmart
    category                            
    Cleaning       23.50    NaN    11.42
    Entertainment    NaN  15.95    19.99
    Tech           55.75    NaN   111.55


Without specific values.


```python
products = pd.DataFrame({'category': ['Cleaning', 'Cleaning', 'Entertainment', 'Entertainment', 'Tech', 'Tech'],
                        'store': ['Walmart', 'Dia', 'Walmart', 'Fnac', 'Dia','Walmart'],
                        'price':[11.42, 23.50, 19.99, 15.95, 55.75, 111.55],
                        'testscore': [4, 3, 5, 7, 5, 8]})

# Use `pivot()` to pivot the DataFrame
pivot_products = products.pivot(index='category', columns='store')

# Check out the results
print(pivot_products)
```

                   price                testscore             
    store            Dia   Fnac Walmart       Dia Fnac Walmart
    category                                                  
    Cleaning       23.50    NaN   11.42       3.0  NaN     4.0
    Entertainment    NaN  15.95   19.99       NaN  7.0     5.0
    Tech           55.75    NaN  111.55       5.0  NaN     8.0


`pivot_table()` can add a function: `mean`.


```python
# The DataFrame
products = pd.DataFrame({'category': ['Cleaning', 'Cleaning', 'Entertainment', 'Entertainment', 'Tech', 'Tech'],
                        'store': ['Walmart', 'Dia', 'Walmart', 'Fnac', 'Dia','Walmart'],
                        'price':[11.42, 23.50, 19.99, 15.95, 19.99, 111.55],
                        'testscore': [4, 3, 5, 7, 5, 8]})

# Pivot the `products` DataFrame with `pivot_table()`
pivot_products = products.pivot_table(index='category', columns='store', values='price', aggfunc='mean')

# Check out the results
print(pivot_products)
```

    store            Dia   Fnac  Walmart
    category                            
    Cleaning       23.50    NaN    11.42
    Entertainment    NaN  15.95    19.99
    Tech           19.99    NaN   111.55


## Use `stack()` and `unstack()` to Reshape a Pandas DataFrame

When we stack a DataFrame, we make it taller. Move the innermost column index to become the innermost row index.

Much like `stack()`, use `unstack()` to move the innermost row index to become the innermost column index.


```python
from collections import OrderedDict
from pandas import DataFrame
import pandas as pd
import numpy as np

table = OrderedDict((
    ("Item", ['Item0', 'Item0', 'Item1', 'Item1']),
    ('CType',['Gold', 'Bronze', 'Gold', 'Silver']),
    ('USD',  ['1$', '2$', '3$', '4$']),
    ('EU',   ['1€', '2€', '3€', '4€'])
))
df = DataFrame(table)
print(df)
```

        Item   CType USD  EU
    0  Item0    Gold  1$  1€
    1  Item0  Bronze  2$  2€
    2  Item1    Gold  3$  3€
    3  Item1  Silver  4$  4€



```python
# Original DataFrame: Access the USD cost of Item0 for Gold customers
print(df[(df.Item=='Item0') & (df.CType=='Gold')].USD.values)
```

    ['1$']



```python
# Column pivot
p = df.pivot(index='Item', columns='CType')
print(p)
```

             USD                 EU            
    CType Bronze Gold Silver Bronze Gold Silver
    Item                                       
    Item0     2$   1$   None     2€   1€   None
    Item1   None   3$     4$   None   3€     4€



```python
# Pivoted DataFrame: p.USD gives a "sub-DataFrame" with the USD values only
print(p.USD[p.USD.index=='Item0'])
```

    CType Bronze Gold Silver
    Item                    
    Item0     2$   1$   None



```python
# more precise
print(p.USD[p.USD.index=='Item0'].Gold.values)
```

    ['1$']



```python
# Pivoting By Multiple Columns
p = df.pivot(index='Item', columns='CType')
print(p)
```

             USD                 EU            
    CType Bronze Gold Silver Bronze Gold Silver
    Item                                       
    Item0     2$   1$   None     2€   1€   None
    Item1   None   3$     4$   None   3€     4€



```python
# Pivoted DataFrame: p.USD gives a "sub-DataFrame" with the USD values only
print(p.USD[p.USD.index=='Item0'])
```

    CType Bronze Gold Silver
    Item                    
    Item0     2$   1$   None



```python
# more precise
print(p.USD[p.USD.index=='Item0'].Gold.values)
```

    ['1$']



```python
# Stack/Unstack
s = df.stack()
print(s)
```

    0  Item      Item0
       CType      Gold
       USD          1$
       EU           1€
    1  Item      Item0
       CType    Bronze
       USD          2$
       EU           2€
    2  Item      Item1
       CType      Gold
       USD          3$
       EU           3€
    3  Item      Item1
       CType    Silver
       USD          4$
       EU           4€
    dtype: object



```python
u = s.unstack()
print(u)
```

        Item   CType USD  EU
    0  Item0    Gold  1$  1€
    1  Item0  Bronze  2$  2€
    2  Item1    Gold  3$  3€
    3  Item1  Silver  4$  4€


## Reshape a DataFrame with `melt()`

When we have a data that has one or more columns that are identifier variables, while all other columns are considered measured variables.


```python
# The `people` DataFrame
people = pd.DataFrame({'FirstName' : ['John', 'Jane'],
                       'LastName' : ['Doe', 'Austen'],
                       'BloodType' : ['A-', 'B+'],
                       'Weight' : [90, 64]})
print(people)
```

      BloodType FirstName LastName  Weight
    0        A-      John      Doe      90
    1        B+      Jane   Austen      64



```python
# Use `melt()` on the `people` DataFrame
print(pd.melt(people, id_vars=['FirstName', 'LastName'], var_name='measurements'))
```

      FirstName LastName measurements value
    0      John      Doe    BloodType    A-
    1      Jane   Austen    BloodType    B+
    2      John      Doe       Weight    90
    3      Jane   Austen       Weight    64


# Iterate over a Pandas DataFrame


```python
df = pd.DataFrame(data=np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9



```python
for index, row in df.iterrows() :
    print(row['A'], row['B'])
```

    1 2
    4 5
    7 8


# Write a Pandas DataFrame to a File

## Output a DataFrame to CSV


```python
df.to_csv('myDataFrame.csv')
```


```python
df.to_csv('myDataFrame2.csv', sep='\t')
```


```python
df.to_csv('myDataFrame3.csv', sep='\t', encoding='utf-8')
```

## Write a DataFrame to [Excel](http://pandas.pydata.org/pandas-docs/stable/io.html#io-excel-reader)


```python
writer = pd.ExcelWriter('myDataFrame.xlsx')
df.to_excel(writer, 'DataFrame')
writer.save()
# startcol=
# startrow=
```


```python
import xlrd

xlsx = pd.ExcelFile('filetype.xlsx')
xlsx.sheet_names
```




    ['a']




```python
df = pd.read_excel(xlsx, 'a')
print(df)
```

       Format Type      Data Description          Reader        Writer
    0         text                   CSV        read_csv        to_csv
    1         text                  JSON       read_json       to_json
    2         text                  HTML       read_html       to_html
    3         text       Local clipboard  read_clipboard  to_clipboard
    4       binary              MS Excel      read_excel      to_excel
    5       binary           HDF5 Format        read_hdf        to_hdf
    6       binary        Feather Format    read_feather    to_feather
    7       binary               Msgpack    read_msgpack    to_msgpack
    8       binary                 Stata      read_stata      to_stata
    9       binary                   SAS        read_sas              
    10      binary  Python Pickle Format     read_pickle     to_pickle
    11         SQL                   SQL        read_sql        to_sql
    12         SQL      Google Big Query        read_gbq        to_gbq

