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
```
## groupby
```
groupby('c1')['c2']
groupby(['c1','c2'])[['c1','c2']]
```

## Pivot Tables
```
pivot_table(values='c1',index='c2',aggfunc="median")
pivot_table(values='c1',index='c2',aggfunc=['mean','median'])
pivot_table(values='c1',index='c21',columns="c22",fill_value=0, margin=True)
```
margin=True represents to add mean of those rows.

## Explicit indexes

```
df.columns
df.index
```
### Seting the column name as index
```
df.set_index('name')
df.set_index(['name','color'])
df.reset_index()
df.reset_index(drop=True)
df.sort_index()
df.sort_index(level='name')
df.sort_index(level=['name','color'],ascending=[True,False])
df.loc[cities] ---- here cities = ['USA','India']
df.iloc
df.
```

## slicing and subsetting using loc and iloc

### Slicing
```
df[:2]
df[2:]
df[2:5]
df[:]
```
### subsetting
```
df.set_index(level=['name','color']).sort_index()
df.loc['Arjun':'Nice']   --- outer index level
```
---here, we can perform the indicies only after the sort and it will slic throught the names from Arjun(A) to Nice(until N of this names)
```
df.loc['red','pink'] --- inner index level
```
--- here, it provide an empty dataframe without throught any error

slicing columns using loc
slice twice- rows and columns
```
df.loc[("outer name1","inner name1"):("outername2","innername2"),"columnname1":"columname2"]
```

slicing using index iloc
```
df.iloc["rn":"rn","cn":"cn"]
```




