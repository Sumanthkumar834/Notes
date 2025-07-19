# Python

1. Loop over NumPy array - 1D array, 2D array.
2. creating a new column using  for - and aslo applying different function to exisiting dataframe includes -
``` 
apply()  
str.upper()
and so on....
```

3. Random Generator
```
np.random.seed(123)
np.random.rand()
np.random.randint(0,2)
```

## Data Manipulation with Pandas


* .head() returns the first few rows (the “head” of the DataFrame).
* .info() shows information on each of the columns, such as the data type and number of missing values.
* .shape returns the number of rows and columns of the DataFrame.
* .describe() calculates a few summary statistics for each column.
* .values: A two-dimensional NumPy array of values.
* .columns: An index of columns: the column names.
* .index: An index for the rows: either row numbers or row names.

## Sorting and subsetting
* sort_values('columname',ascending=False)
* sort_values(['columname1','columname2'], ascending=[True,False])

```
df['c1']
df[["c1","c2"]]
df[(df['c1']>10) & (df['c2']== 10) ]
df['c1'].isin(['v1','v2'])
```

## New Columns
```
df['nc'] = df['c1'] * 2
can perform different kinds of operations 
```

## Summarizing numbercial data

```
mean(), medium(), mode()
min(), max()
var(), std()
sum()
quatile()
agg(functionname)
agg([f1,f2])
agg([f1,"mean"])
cumulative Functions
cumsum(), cummax(), cummin(), cumprod()
```

## Counting
```
df.drop_duplicates(subset='c1')
df.drop_duplicates(subest=['c1','c2'])
df.value_counts()
df.value_counts(sort=True)  
df.value_counts(normalize=True)
df.value_counts().sort_values(ascending=True)


