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

## Visualing your data

### Histogram

```
import maltplotlib.pyplot as plt
df['weight'].hist()
plt.show()
```
bins & Bars

```
df['weight].hist(bins=20)
df['weight'].hist(kind='bar',title = " mean weight")

df.plot(x='date',y='weight',kind='line',rot=45,)
df.show()

for scatter - kind='scatter'
alpha=0.7
plt.legend(['M','F'])

```
##  Missing Values

```
df.isna()
df.isna().any() -- using value atleast one in the column
df.isna().sum() -- sum of all the missing values in the column

df.isna.sum().plot(kind='bar')
show.plt()

df.dropna() -drop all missing values
df.fillna(0) --  fill missing values
```

## Creating a data frame

```
two ways of creating a datafram - row by row and column by column

dictionaries -
dict = {"key1":value1,
        "key2":value2,
        "key3":value3}

row by row

list_of_dict = [
    {"name":"hello world","salary":100000},
    {"name":"abc","salary":800000}
    ]

column by column

dict_oflist =
    {
        "name":["hello world","abc"],
        "salary":[100000,800000]
    }

new_df = df.DataFrame(dict)
```

## Reading and Writing CSV Files

```
df1  = pd.read_csv("hello.csv")
df1.to_csv("hello.csv")
```

Performing different kinds of operations using combination of different functions and methods.....
