
# Reference Guide: Teach Me How To Pandas
***
<img src="https://s-media-cache-ak0.pinimg.com/originals/7e/cc/a7/7ecca73c35701df2708c43d0c9f40ada.png"/>
<img src="https://a.disquscdn.com/get?url=https%3A%2F%2Fmedia.giphy.com%2Fmedia%2FIU5ApmC4e6wEw%2Fgiphy.gif&key=yOhwdV8VW_y07hJuhGmfZQ"/>

# Background
***

### "Hey, can you teach me how to Pandas?" 

Say no more friends! Today we're going to learn the Pandas library. Pandas stands for “Python Data Analysis Library”. According to the Wikipedia page on Pandas, “the name is derived from the term “panel data”, an econometrics term for multidimensional structured data sets.” 

### Why Pandas

Pandas is one of the most powerful data manipulation tools out there but when a data scientist can leverage the power of indexing to his advantage, it makes pandas the best data manipulation tool out there!

- Pandas is a game changer when analyzing data with Python
- It's a python module that makes data science easy and effective
- It's one of the most preferred and widely used tools in data manipulation if not **THE** most used one
- Pandas is an open source package and is **FREE** to use

### DataFrame Basics

*Dataframe* is a main object in Pandas. What’s cool about Pandas is that it takes data (like a CSV or JSON file, or a SQL database) and creates a Python object with **rows** and **columns**. It is used to reprsent data with rows and columns (tabular or excel spreadsheet like data). 


*Reference*: https://towardsdatascience.com/a-quick-introduction-to-the-pandas-python-library-f1b678f34673

# Pandas Main Concepts & Exercises
***

<img src="https://data.whicdn.com/images/109402725/original.gif"/>

## 6 Parts of Pandas
1. Importing Data and Reading Data
2. Summarizing Data (Statistics)  
3. Manipulating Data / Cleaning Data
4. Selecting Data / Subsetting Data
5. Grouping and Filtering Data
6. Combining Datasets

<img src="https://pbs.twimg.com/media/C65MaMpVwAA3v0A.jpg"/>


# 1. Importing Data and Reading Data
***

### Summary

Don't make things complicated. This is literally a two step process! 

You import the Pandas library and then you use it's **read_csv()** function to read your files :-)

**Note:** We'll be working with a Human Resources Dataset. Please download the file below

**Download File Here**: https://www.kaggle.com/ludobenistant/hr-analytics/data


```python
# Import the pandas package
import pandas as pd
```


```python
# Read the CSV File stored in your file destination
# Remember to download the csv file and replace the file location in order to read in your csv
df = pd.read_csv('C:/Users/Randy/Downloads/HR_comma_sep.csv')
```

# 2. Summarizing Data (Statistics)
***
### Objective

You cannot do anything as a data scientist without even having any data! So now you've loaded your dataset and now you want to examine it. What headers and values does your data frame have? How big is my data set? What summary can be displayed? Some really handy Pandas functions can help you solve these problems!

These functions are the most common tools used when trying to summarize your data

### Functions

- **df.head(n)** — Returns the first n rows of your DataFrame. Having a blank argument will display the first 5 by default
- **df.tail(n)** — Returns the last n rows of your DataFrame. Having a blank argument will display the last 5 by default
- **df.shape()** — Displays the number of rows and columns in your DataFrame
- **df.describe()** — Dispalys a stastical summary for numerical columns
- **df.mean()** — Returns the mean of all columns
- **df.median()** — Returns the median of all columns
- **df.std()** — Returns the standard deviation of all columns
- **df.max()** — Returns the highest value in each column
- **df.min()** — Returns the lowest value in each column 


```python
# Run and test the functions here:





```

# 3. Manipulating / Cleaning Data
***
<img src="https://i.imgur.com/bhKeU4P.gif"/>

### Objective

Clean up on column 5! When your data is dirty, your job as a Data Scientist is to clean it up! 

Some common tasks are to understand every feature you're working with, identify errors, missing values, and corrupt records. 

Cleaning the data involves you to throw away, replace, and/or fill missing values/errors


### Functions
- **df.isnull().sum()** — Used to display the total amount of missing values in your columns
- **df.columns** — Displays a list of your column names
- **df.columns = ['col_name1','col_name2','col_name3']** — Allows you to replace your columns with a new name
- **df.rename(columns={'old_name1':'new_name1', 'old_name2':'new_name2'})** — Allows you to rename certain columns directly
- **df.fillna(x)** — Repalces every null value in your table with x (could be a string value or numeric value)


```python
# Run and test the functions here:





```

# 4. Selecting / Subsetting Data
***

### Summary

Pandas is great for selecting certain columns or rows within your DataFrame. Let's see the various ways we can do this!


### Functions


- **df[['col_name1','col_name2','col_name3']]** — Creates a new DataFrame by extracting certain column names
- **df['col_name1']** — Creates a new DataFrame that selects a single column name
- **df['col_name1'].unique()** — Creates an arraylist containing the unique values of a column 

### Select by Loc 
**How it works:** loc works on labels in the index.
- **df.loc[ :, 'col_name1':'col_name2']** — Creates a new DataFrame that only includes columms 1-3

### Select by iLoc
**How it works:** iloc works on the positions in the index (so it only takes integers).

- **df.iloc[ :, [1,2,3]]** — Creates a new DataFrame that only includes columns 1-3


```python
# Run and test the functions here:





```

# 5. Grouping and Filtering Data
***

### Objective

Grouping and Filtering plays an important role in data manipulation. Luckily, the Pandas library provides you really simple, but powerful, functions that allows you to do just that. Here's the main functions that you should be comfortable with:

### Filtering

You can use different conditions to filter columns. For example, df[df[year] > 1984] would give you only the column year is greater than 1984. You can use & (and) or | (or) to add different conditions to your filtering. These is also called boolean filtering.

- **df[df['col_name1'] == 'value']** — Select a value from this list and create a new DataFrame that only matches the condition
- **df.loc[df['col_name1' > 10] , ['col_name1','col_name2','col_name3']]** — Select columns 1-3 from the DataFrame that meets the condition

### Sorting

- **df.sort_values('col_name1')** — Sorts the values in a certain column in ascending order
- **df.sort_values('col_name1', ascending=False)** — Sorts the values in a certain column in descending order

### Grouping
Grouping involves splitting the data into groups based on some criteria, applying a function to each group independently and combining the results into a data structure.

- **df.groupby('col_name1')** — Returns a groupby object for values from one column
- **df.groupby(['col_name1' , 'col_name2'])** — Returns a groupby object for values from multiple columns




```python
# Run and test the functions here:





```

# 6. Combining Datasets
***

### Objective

Here are some common functions that allows you to combine multiple datasets easily!

### Functions

- **df1.append(df2)** — add the rows in df1 to the end of df2 (columns should be identical)
- **df.concat([df1, df2],axis=1)** — add the columns in df1 to the end of df2 (rows should be identical)
- **df1.join(df2,on=col1,how='inner')** — SQL-style join the columns in df1 with the columns on df2 where the rows for colhave identical values. how can be equal to one of: 'left', 'right', 'outer', 'inner'


```python
# Run and test the functions here:





```

# Final Note
***

These are the very basic Pandas commands but I hope you can see how powerful Pandas can be for data analysis. 

This post is just the tip of the iceberg — after all, entire books can be (and have been) written about data analysis with Pandas. 

I also hope this notebook made you feel like taking a dataset and **PLAYING** around with it using Pandas! :)

<img src="http://img1.liveinternet.ru/images/attach/c/3/76/786/76786793_pandaDONE.gif"/>


```python

```
