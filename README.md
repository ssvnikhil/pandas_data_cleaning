# Cleaning dirty data using Pandas and Jupyter notebook

There is more to life than a million rows - fact. Most data journalists start in excel, then progress to SQL and so forth but once your data swells in size I struggle to clean millions of rows of dirty data. 

Rather than venturing down the SQL cleaning route and acknowledging that OpenRefine has its limitations I'm putting together a little cheat sheet on how to clean dirty data using pandas in Jupyter notebook. 

##First steps - take a look at that data

It's all well and good saying we're going to clean dirty data but do we even know how it's dirty?
We need to eyeball that sucker and figure how how it looks. 

First thing we need to do is read our data into pandas and take a look for ourselves.

`import pandas as pd`

`df = pd.read_csv('/user/home/test.csv')`

`df.head()`

Take a good look at that data and figure out what values you were expecting and what looks unusual. This is a good time to pull out your data dictionary and start looking though your data. 

##Merging, joining and concatenating data

Sometimes before cleaning our data set we need to build it first, merging, joining and concatenating rows and columns enables us to take multiple csvs and join them together. This saves time when it comes to cleaning our data for analysis

###Concatenating objects

```
In [1]: df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
   ...:                     'B': ['B0', 'B1', 'B2', 'B3'],
   ...:                     'C': ['C0', 'C1', 'C2', 'C3'],
   ...:                     'D': ['D0', 'D1', 'D2', 'D3']},
   ...:                     index=[0, 1, 2, 3])
   ...: `

In [2]: df2 = pd.DataFrame({'A': ['A4', 'A5', 'A6', 'A7'],
   ...:                     'B': ['B4', 'B5', 'B6', 'B7'],
   ...:                     'C': ['C4', 'C5', 'C6', 'C7'],
   ...:                     'D': ['D4', 'D5', 'D6', 'D7']},
   ...:                      index=[4, 5, 6, 7])
   ...:

In [3]: df3 = pd.DataFrame({'A': ['A8', 'A9', 'A10', 'A11'],
   ...:                     'B': ['B8', 'B9', 'B10', 'B11'],
   ...:                     'C': ['C8', 'C9', 'C10', 'C11'],
   ...:                     'D': ['D8', 'D9', 'D10', 'D11']},
   ...:                     index=[8, 9, 10, 11])`
   ...: `

In [4]: frames = [df1, df2, df3]

In [5]: result = pd.concat(frames)
```


