# Tidy Data and Messy Data

**Foreword**

Notes. Python 3.

-----

[TOC]

-----

It is often said that data scientists spend only 20% of their time analyzing their data, and 80% of time cleaning it. Indeed, maintaining a tidy, easy-to-use dataset is crucial in our age of big data. In the paper Tidy Data, veteran statistician Hadley Wickham gives definitions of tidy and messy data so that all data scientists can keep their work organized. 

## 1, Loading

First, load all the datasets.

```python
import pandas as pd

messy = pd.read_csv('messy.csv')
df1 = pd.read_csv('df1.csv')
df2 = pd.read_csv('df2.csv')
eyes = pd.read_csv('eyes.csv')
```

## 2, Tidy vs. Messy Data

What exactly marks the difference between tidy data and messy data? It is not only how organized and intuitive the datasets look to our human eyes, but also how easily and efficiently they can be processed by computers. In his seminal paper [Tidy Data](https://www.jstatsoft.org/article/view/v059i10), Hadley Wickham proposed three standards for tidy data:

1. Each variable forms a column
2. Each observation forms a row
3. Each type of observation forms a unit.


To get started, execute `messy` in the shell. This dataset, which appears in Wickham's paper, shows the number of people who choose either of two treatments in a hospital. Observe its structure in comparison with Wickham's rules. This dataset is *messy* because it violates rule 2: it combines Treatment A and Treatment B, two distinct observations, in a single row.

```python
print(messy.head())
```

      First     Last  Treatment A  Treatment B
    0  John    Smith          NaN            2
    1  Jane      Doe         16.0           11
    2  Mary  Johnson          3.0            1
    

Now let's look at two more datasets. Execute `df1` and `df2` in the shell to check out two other preloaded datasets. The former shows the type and number of pets owned by three co-workers, and the latter shows the average BMI in three countries over several years. 


```python
print(df1.head())
```

          owner  dogs  cats  birds
    0     Jason     2     4      3
    1      Lisa     7    10      9
    2  Terrence     8     5      1
    


```python
print(df2.head())
```

           Country     Y1980     Y1981     Y1982     Y1983
    0  Afghanistan  21.48678  21.46552  21.45145  21.43822
    1      Albania  25.22533  25.23981  25.25636  25.27176
    2      Algeria  22.25703  22.34745  22.43647  22.52105
    

`df2` is messy because it violates rule 2.

## 4, Using `melt` to Tidy Data

Its basic syntax is `pd.melt(df, id_vars = lst)`, where `df` is the name of the data frame we're dealing with and `lst` is a list of all the columns that we want to keep as columns. 


```python
# Melt df2 into a new data frame: df2_melted
df2_melted = pd.melt(df2, id_vars = 'Country')

# print df2_melted
print(df2_melted)
```

            Country variable     value
    0   Afghanistan    Y1980  21.48678
    1       Albania    Y1980  25.22533
    2       Algeria    Y1980  22.25703
    3   Afghanistan    Y1981  21.46552
    4       Albania    Y1981  25.23981
    5       Algeria    Y1981  22.34745
    6   Afghanistan    Y1982  21.45145
    7       Albania    Y1982  25.25636
    8       Algeria    Y1982  22.43647
    9   Afghanistan    Y1983  21.43822
    10      Albania    Y1983  25.27176
    11      Algeria    Y1983  22.52105
    

**Renaming Columns**

Change the column names with pandas' rename function. Its syntax is `df.rename(columns = d, inplace = False)`, where `d` is a dictionary where the keys are the columns you want to change, and the values are the new names for these columns.


```python
# Rename the columns of df2_melted: df2_tidy
df2_tidy = df2_melted.rename(columns = {'variable': 'Year', 'value': 'Income'})

# Print out df2_tidy
print(df2_tidy)
```

            Country   Year    Income
    0   Afghanistan  Y1980  21.48678
    1       Albania  Y1980  25.22533
    2       Algeria  Y1980  22.25703
    3   Afghanistan  Y1981  21.46552
    4       Albania  Y1981  25.23981
    5       Algeria  Y1981  22.34745
    6   Afghanistan  Y1982  21.45145
    7       Albania  Y1982  25.25636
    8       Algeria  Y1982  22.43647
    9   Afghanistan  Y1983  21.43822
    10      Albania  Y1983  25.27176
    11      Algeria  Y1983  22.52105
    

**More messiness**

Execute `eyes` in the shell. This dataset is about the eye colors of three women and whether or not they wear glasses. What problem does this dataset have?


```python
print(eyes)
```

            Name  Brown  Blue  Black Wear_Glasses
    0     Esther      0     1      0        False
    1  Elizabeth      1     0      0        False
    2   Michelle      0     0      1         True
    

It violates rule 1 of tidy data: there are several columns that represent the same variable.

**Deal with it**

Use `melt`.

```python
# Melt the Black, Blue, and Brown columns of eyes: eyes_melted
eyes_melted = pd.melt(eyes, id_vars = ['Name', 'Wear_Glasses'])

# Rename the variable column and save to eyes_renamed
eyes_renamed = eyes_melted.rename(columns = {'variable': 'Eye_Color'})

# print out eyes_renamed
print(eyes_renamed)
```

            Name Wear_Glasses Eye_Color  value
    0     Esther        False     Brown      0
    1  Elizabeth        False     Brown      1
    2   Michelle         True     Brown      0
    3     Esther        False      Blue      1
    4  Elizabeth        False      Blue      0
    5   Michelle         True      Blue      0
    6     Esther        False     Black      0
    7  Elizabeth        False     Black      0
    8   Michelle         True     Black      1
    

**Further Cleaning**

Get rid of all rows whose value in the value column is 0.

`df1 = df2[df2.column == value]`

where `column` is the name of the column we are examining and `value` is the value we want to keep. This step will give us one row for each girl that tells us only her correct eye color. Now the `value` column is no longer necessary, so let's delete it:

`df.drop(lst, axis = 1)`

Here `lst` is a list of the columns we want to get rid of, and `axis = 1` specifies that we want to drop columns instead of rows.


```python
# Filter eyes_ranamed and save to eyes_filtered 
eyes_filtered = eyes_renamed[eyes_renamed.value == 1]

# Delete the `value` column and save to eyes_tidy
eyes_tidy = eyes_filtered.drop(['value'], axis = 1)

# print eyes_tidy
print(eyes_tidy)
```

            Name Wear_Glasses Eye_Color
    1  Elizabeth        False     Brown
    3     Esther        False      Blue
    8   Michelle         True     Black   