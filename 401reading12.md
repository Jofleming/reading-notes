# Pandas Reading

## Pandas in 10

[Reading](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)

Import as follows:
```
import numpy as np
import pandas as pd
```

### Object Creation

You can create a series by passing a lost of values and letting pandas create default integer index.
example given: `s = pd.Series([1, 3, 5, np.nan, 6, 8])`

You can also pass in a NumPy array with a datetime index and labeled columns to make a dataframe.
```
dates = pd.date_range("20130101", periods=6)

dates
Out[6]: 
DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))

df
Out[8]: 
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
```

Can do similar by passing in a dictionary:
```
df2 = pd.DataFrame(
    {
        "A": 1.0,
        "B": pd.Timestamp("20130102"),
        "C": pd.Series(1, index=list(range(4)), dtype="float32"),
        "D": np.array([3] * 4, dtype="int32"),
        "E": pd.Categorical(["test", "train", "test", "train"]),
        "F": "foo",
    }
)


df2
Out[10]: 
     A          B    C  D      E    F
0  1.0 2013-01-02  1.0  3   test  foo
1  1.0 2013-01-02  1.0  3  train  foo
2  1.0 2013-01-02  1.0  3   test  foo
3  1.0 2013-01-02  1.0  3  train  foo
```

Subset of attributes that will be completed:
```
df2.A                  df2.bool
df2.abs                df2.boxplot
df2.add                df2.C
df2.add_prefix         df2.clip
df2.add_suffix         df2.columns
df2.align              df2.copy
df2.all                df2.count
df2.any                df2.combine
df2.append             df2.D
df2.apply              df2.describe
df2.applymap           df2.diff
df2.B                  df2.duplicated
```

### Viewing Data

`df.head()` will show you the top rows of the dataframe (df). Defaults to 5. You can pass in an argument to see more or less.
`df.tail()` will show you the bottom rows. In the example `df.tail(3)` is used to see the bottom 3.

```
df.index
Out[15]: 
DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

df.columns
Out[16]: Index(['A', 'B', 'C', 'D'], dtype='object')
```

`DataFrame.to_numpy()` gives a NumPy representation of the underlying data. Note that this can be an expensive operation when your DataFrame has columns with different data types, which comes down to a fundamental difference between pandas and NumPy: NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column. When you call `DataFrame.to_numpy()`, pandas will find the NumPy dtype that can hold all of the dtypes in the DataFrame. This may end up being object, which requires casting every value to a Python object.

`df.describe()` shows a quick statistic summary of your data.
`df.T` - Transposes your data. (switches axes)
`df.sort_index(axis=1, ascending=False)` - Sorts by an axis.
`df.sort_values(by="B")` - Sorts by a specified value. In this case B.

### Selection

`df["A"]` - Used to select a single column, which yields a series, equiv to `df.A`
`df[0:3]` - Can use slicing which will select the rows. In this case the first 3 rows.
`df["20130102":"20130104"]` Same as above but the values are in rows. Example below
```
df["20130102":"20130104"]
Out[25]: 
                   A         B         C         D
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
```



## What is Pandas

[Video](https://www.youtube.com/watch?v=dcqPhpY7tWk&t=391s&ab_channel=PythonProgrammer)

`ms['Adj. Close'].plot()` - ms is dataframe name, inside [] is the column name. Calling plot gives a nice group of the column.

`dataframename.index` will tell us what the index is. In the video it is a date.

He then uses: `ms['2018']['Adj. Close'].plot()` to plot the adjusted close for microsoft shares in 2018.
He then uses a more specific date, I.E. 2018-01-01. You can also use a range using :
He then joins two data sets. After they are both set to variables he uses:
`both_stocks = ms_price.join(apple_price,how='inner')` then `both_stocks.plot()`


[Back](README.md)