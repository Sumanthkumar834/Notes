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
```
setting the index while accessing a csv file
```
df = pd.read_csv("hello.csv",index_col=['name'])
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

new_df = pd.DataFrame(dict)
```

## Reading and Writing CSV Files

```
df1  = pd.read_csv("hello.csv")
df1.to_csv("hello.csv")
```

Performing different kinds of operations using combination of different functions and methods.....

## Joinig Dataframe

Inner Join
```
newdf = df1.merge(df2,on="commoncolumnname"),suffixes=('_df1','_df2')
```
One to Many relations - same syntax
```
newdf = df1.merge(df2,on=["commoncolumnname1","commoncolumnname2"])\
        .merge(df3,on="commoncolumnname3")
```

Left Merge

```
newdf=df1.merge(df2,on="commoncolumnname",how="left")
```

Right Merge
```
newdf=df1.merge(df2,,how="right",left_on="leftcolumnname", right_on="rightcolumnname")
```
Outer Join
```
newdf=df1.merge(df2,how="outter")
```

Self Join/Merge
```
newdf=df.merge(df,left_on='c1',right_on='c2',suffixes=('_left','_right'))
```
Merging on Indexes
```
newdf=df1.merge(df2,how='inner',left_on='c1',right_on='c2',right_index=True,left_index=True,suffix('_leftc','_rightc'))
```

## connecting to tables vertically 
## Basic Concatenation
```
pd.concat([inv_jan,inv_feb,inv_march])
```
### Ignore the index if there is not valuable info
```
pd.concat([inv_jan,inv_feb,inv_march],ignore_index=True)
```
### setting labels to original tables
```
pd.concat([inv_jan,inv_feb,inv_march],ignore_index=False, keys=['JAN','FEB','MARCH'])
```
### Concat tables if we have different columnnames
```
pd.concat([inv_jan,inv_feb],join='inner) 
```
-- this will ignore the additional columns
```
pd.concat([inv_jan,inv_feb],sort=True)
```
 -- adds the additional column to, the rest values of differnt table would be nan

## Verfying integirity
merge the tables - join
``` 
df1.merge(df2,on='columnname',validate='one_to_one')
```
through an error if the relation between df1 and df2 is not one to one relationship.

similarly, we have --  one_to_many, many_to_one, many_to_many.


Concat the tables
```
pd.concat([inv_jan,inv_feb],verify_integrity=True)
```
it through an error if there is any common index number in both the table.

if it is set of Flase it doesnt through any error.

## merge_ordered()
```
pd.merge_ordered(df1,df2,on='columnname', suffixes=('_left','_right'), fill_method='ffill')
```
usually used while dealing with time series data. farward fill is quite usefull for missing values.

## merge as_of - similar to merge_ordered left join

```
pd.merge_asof(visa,ibm,on=['date_time'],suffixes=('_visa','_ibm'),direction='forward')
```
this merge usually used in times series data- like transactions. we have another value to direction include - nearest.

## Selecting date with query()
```
stocks.query('nike>90 and disney<140')
```

we can also use or operator and <,>,== operator other column condition similar to SQL.

## Reshaping data with .melt()

wide format vs long format
melt methos used to change wide to long format
```
social_fin_tall=soical_fin.melt(id_vars=['finanical','company'],value_vars=['2018','2017'])
```

## Statistics

* study of collecting and analyzing the data
* summary statistics is about summary of the data.
* statistics provide different kinds of answer to the question we have based on what of data we are dealing with.

Type of statistics data -  Descriptive statistics(describe and summarize the data) and inferential statitics(based on the sample data we define it to a population).

Type of data - numeric(quantitative) - continuous data (measured- speed)and discrete data(counted- number of bottles) and categorial(qualitative) Data -- normial(unordered- married/unmarried) and oridnal(ordered - strong agree, agree, disagree, )

## measures of center
```
np.mean(df['columnname'])
```

mean.median, mode

mode is usually used for categorial data

if you think there are outliners or the graph is left skewed or right skewed use median 

## Spread sheet
variance - calculate the distance from each data point to mean and square  the each data point and add altogether. finally divided by sum of data point -1.

unit is square.

The Higher the variance - the wider the spred sheet is..
```
np.var(df['columname'],ddof=1)
```
Standard Deviation - square route of variance.
```
np.std(df['columnname'],ddof=1)
```
Mean Absolute deviation
```
np.abs(sd['columnname'],ddof=1)
```

std square the distances, penalizing the longer than the shorter ones, while the abs penalizes all the distance equally.


Qunatiles(percentiles)
```
np.quantiles(animals['sleep'],0.5) 
```
- assuming the answer is 10 then 50% of the animal sleep less than 10 hrs and other 50% more than 10hrs..

Quartiles
```
np.quantiles(animals['sleep'],[0,0.25,0.5,0.75,1])
```

Quantiles using np.linespace()
```
np.quantile(animals['sleep'],np..linspace(0,1,5))

i.e
np.linespace(start,stop,intervals)
```

Interquartile range(IQR) - distance between 25% and 75% 
```
from spicy.stats import iqr
iqr(animals['sleep'])
```

Outliners
It is a outliners -
data < Q1 -1.5 * iqr
data > Q3 +1.5 * iqr


all these statitics can be calculated using describe()

