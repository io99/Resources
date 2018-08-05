
# Python & Pandas Reference Guide
***

<img src="https://media.giphy.com/media/eH9sawQbajAQM/source.gif"/>

## Table of Contents
### Python Contents:

[Virtual Enviornments](#virtual_enviornments)

[Terminal Commands](#terminal)

[Variable Declaration](#variable_declaration)

[User Inputs and Prompts](#user_input)

[Conditionals](#conditionals)

[Lists](#lists)

[Tuples](#tuples)

[Loops](#loops)

[Reading CSV Files](#reading_csv)

[Zipping Lists](#zipping_lists)

[Functions](#functions)

[Dictionaries](#dictionaries)

[Key and Values](#key_values)

## Jupyter Notebooks Content:


[Jupyter Notebooks](#jupyter_notebooks)

## Pandas Content:

[Pandas Overview](#pandas_overview)

[Pandas Reference Sheet](#pandas_reference_guide)

    
    
<img src="https://cdn.dribbble.com/users/681303/screenshots/3524015/dribbble-1.gif"/>

<a id='virtual_enviornments'></a>

### Virtual Environments
***
Check anaconda version:
```
conda --version
```

To create a virtual environment that will run Python 3.6:

- First run the following command in terminal
```
conda create -n PythonData python=3.6 anaconda
```

- To activate the environment:
```
source activate PythonData
```
 
- To deactivate the environment:
```
source deactivate
```

<a id='terminal'></a>

### Terminal Commands
***

```cd ``` (Changes the directory)

```cd ~``` (Changes to the home directory)

```cd ..``` (Moves up one directory)

```ls``` (Lists files in folder)

```pwd``` (Shows the current directory)

```mkdir``` <FOLDERNAME> (Creates a new directory with the FOLDERNAME)

```touch``` <FILENAME> (Creates a new file with the FILENAME)

```rm <FILENAME>``` (Deletes a file)

```rm -r <FOLDERNAME>``` (Deletes a folder, make sure to note the -r)

```open .``` (Opens the current folder on Macs)

```explorer .``` (Opens the current folder on Bash)

```open <FILENAME>``` (Opens a specific file on Macs)

```explorer <FILENAME>``` (Opens a specific file on Bash)

<a id='variable_declaration'></a>
### Variable Declaration
*** 

Variables let us store information that we can later use.

- Variables can store different data types like strings, integers and a completely new data type called booleans which hold ```True``` or ```False``` values.
- We can print statements which include variables but Python can only print strings. This means integers and booleans must be cast as strings using the ```str()``` function.

```
name = 'Tom Cruise'
number = 1
```

<a id='user_input'></a>
### User Inputs and Prompts
***

- Every response to an input is stored as a string regardless of the characters entered. As such, variables that are intended to be integers must be cast in order to be used in calculations.
- The bool() function always returns True if any text is inside of it
- Print statements can be concatenated with variables so long as they are also strings or are cast as strings

```
name = input('What is your name?')
```

<a id='conditionals'></a>
### Conditionals
****

- Python uses ```if```, ```elif```, and ```else```
- Conditional statements are concluded with a colon but all lines after the colon must be indented in order to be considered a part of that code block. This is because Python reads blocks of code based on indentation.
- All sorts of operators like greater than, less than, equal to, and much more can be used to create logic tests for conditionals.
- Multiple logic tests can be checked within a single conditional statement. Using the term ```and``` must mean both tests return ```True``` while ```or``` require that only one test return as true.
- Conditionals can even be nested, allowing programmers to run logic tests based upon whether or not the original logic test returned as ```True```.

```
if (x>10):
	print('x is greater than 10')
else:
	print('x is less than 10')
```


<a id='lists'></a>
### Lists
****

- Lists are the Python equivalent of arrays in VBA, functioning in much the same way by holding multiple pieces of data within one variable.
- Lists can hold multiple types of data inside of them as well. This means that strings, integers, and boolean values can be stored within a single list

The ```append``` method can add elements on to the end of a list

The ```index``` method return the numeric location of a given value within a list

The ```len``` function returns the length of a list

The ```remove``` method deletes a given value from a list

The ```pop``` method to remove a value by index.

```
# Create a variable and set it as an List
myList = ["Jacob", 25, "Ahmed", 80]
print(myList)

# Adds an element onto the end of a List
myList.append("Matt")
print(myList)

# Changes a specified element within an List at the given index
myList[3] = 85
print(myList)

# Returns the index of the first object with a matching value
print(myList.index("Matt"))

# Returns the length of the List
print(len(myList))

# Removes a specified object from an List
myList.remove("Matt")
print(myList)

# Removes the object at the index specified
myList.pop(0)
myList.pop(0)
print(myList)
```

<a id='tuples'></a>
### Tuples
***

- Python also has a data type called tuples that are functionally similar to lists in what they can store but are immutable.
- While lists in Python can be modified after their creation, tuples can never be modified after their declaration.
- Tuples tend to be more efficient to navigate through than lists and also protect the data stored within from being changed.

```
myTuple = ('Python', 100, 'VBA', False)
print(myTuple)
```

<a id='loops'></a>
### Loops
***

- The variable ```x``` is created within the loop statement and could theoretically take on any name so long as it is unique.
- When looping through a range of numbers, Python will halt the loop one number before the final number. For example, when looping from 0 to 5, the code will run five times but ```x``` will only ever be printed as 0 through 4.
- When provided with a single number, ```range()``` will always start the loop at 0. When provided with two numbers, however, the code will loop from the first number until it reaches one less than the second number.
- Python can also loop through all of the letters within a string or all of the values stored within a list by using the syntax ```for <variable> in <string or list>```
- ```while``` loops will run blocks of code just like a for loop does but will continue looping for as long as a condition is met


```
# Loop through a range of numbers (0 through 4)
for x in range(5):
  print(x)

print("-----------------------------------------")

# Loop through a range of numbers (2 through 6)
for x in range(2, 7): 
  print(x)

print("----------------------------------------")

# Iterate through letters in a string
word = "Peace"
for letters in word:
  print(letters)

print("----------------------------------------")

# Iterate through a list
zoo = ["cow", "dog", "bee", "zebra"]
for animal in zoo:
  print(animal) 

print("----------------------------------------")

# Loop while a condition is being met
run = "y"

while run == "y":
  print("Hi!")
  run = input("To run again. Enter 'y'" )
```

<a id='reading_csv'></a>
### Reading in CSVs
***

```
import os 
import csv

csvpath = os.path.join('Resources', 'accounting.csv')
with open(csvpath, newline = '') as csvfile:

	csvreader = csv.reader(csvfile, delimiter = ',')
	
	for row in csvreader:
		print(row)
```

<a id='zipping_lists'></a>
### Zipping lists
***

While it is possible to write new rows of data into a CSV file using a bunch of csv.writerow() statements, Python users can far more efficiently write data into a new CSV file by using the zip() function.

- ```zip()``` takes in a series of lists as its parameters and joins them together into a stack.
- Zipped lists are turned into tuples. This means that the lists inside of a zip can no longer be modified or added to in any way.


<a id='functions'></a>
### Functions
***

A function is a block of organized, reusable code that is used to perform a single, related action. In other words, functions are placeable blocks of code that perform a specific action.

- To create a new function, simply use ```def <Function Name>():``` and then place the code that you would like to run within the block underneath it.
- In order to run the code stored within a function, the function itself must be called within the program. Functions will never run unless called upon.
- Functions that take in parameters can also be created by simply adding a variable into the parentheses of the function's definition. This allows specific data to be passed into the function for usage.

```
# Define the function and tell it to print "Hello!" when called
def printHello():
    print("Hello!")
# Call the function within the application to ensure the code is run
printHello()
```

<a id='dictionaries'></a>
### Dictionaries
***

- Like lists and tuples, dictionaries can contain multiple values and types of data within them.
- Unlike lists and tuples, however, store data in key-value pairs. The key in a dictionary is a string that can be referenced in order to collect the value it is associated with.
- Referencing a value within a dictionary is as simple as calling the dictionary and following it up with a pair of brackets containing the key for the value desired. 

```
actor = {'name':'Tom Cruise'}
print(actor['name'])
```

<a id='key_values'></a>
### Keys and Values
***

- All keys in a dictionary can be accessed by using the ```keys()``` method.
- Similarly, all values in a dictionary can be accessed using the ```values()``` method.
- The ```keys()``` and ```values()``` methods can also be used to iterate through a dictionary using a for loop.
- The entire dictionary - both keys and values - can be iterated through by using the ```items()``` method.
- The ```del()``` function can be used to remove a key-value pair by referencing the dictionary and key within
- To add or update values within a dictionary, simply create a reference to the key desired and then set it equal to the value desired.

```
# Two Dictionaries
actress = {"name": "Angelina Jolie", "genre": "Action", "nationality": "United States"}
actor = {"name": "Adam Sandler", "genre": "comedy", "nationality": "United States"}

# Access all the keys
print(actor.keys())

# Access all values
print(actress.values())

# We can iterate through dictionaries with a for-loop
for key in actress.keys():
    print("This is a key:", key)

# Looping through values
for value in actress.values():
    print("This is a value:", value)

# Use items() to loop through both keys and values
for key, value in actress.items():
    print("This is a key:", key)
    print("This is a value:", value)
```

<a id='jupyter_notebooks'></a>
### Jupyter Notebooks
***

<img src="https://avatars3.githubusercontent.com/u/7388996?s=400&v=4"/>

Run ```jupyter notebook``` from terminal which will automatically open up a webpage where users can navigate into any files/folders within the folder they ran the command from.

<a id='pandas_overview'></a>
### Pandas
***

**Intro**

- A Pandas Series is a one-dimensional labeled array capable of holding any data type. This means that, like an array, the data is linear but that, like a dictionary, it has an index that acts like a key.
- A Pandas DataFrame is a two-dimensional labeled data structure with columns of potentially different types. The easiest way to think of it is like an Excel spreadsheet with each column being a Series.

**DataFrame Creation**

- Before doing anything else, the Pandas library is imported using import pandas as pd. This method of import allows Pandas functions/methods to be called using the variable pd.

```
import pandas as pd
```

- To create a Series, simply use the pd.Series() function and place a list within the parentheses. The index for the values within the Series will be the numeric index of the initial list.

```
# We can create a Pandas Series from a raw list
data_series = pd.Series(["UCLA", "UC Berkeley", "UC Irvine", "University of Central Florida", "Rutgers University"])
```

- Creating pandas dataframe in two ways:

1. List of Dictionaries

```
# Convert a list of dictionarys into a dataframe
states_dicts = [{"STATE":"New Jersey","ABBREVIATION":"NJ"},{"STATE":"New York","ABBREVIATION":"NY"}]
```

2. Dictionary of Lists

```
# Convert a single dictionary containing lists into a dataframe
df = pd.DataFrame(
        {"Dynasty": ["Early Dynastic Period","Old Kingdom"],
         "Pharoh": ["Thinis","Memphis"]
        }
    )
```


**DataFrame Functions**

```df.head()``` (shows only the first five rows of data inside of it)

```df.describe()``` (prints out a DataFrame containing some analytic information on the table and its columns)

```df['column'].mean()``` (returns the average for a series)

```df['column'].sum()``` (returns the sum for a series)

```df['column'].unique()``` (shows every element of the series that appears only once)

```df['column'].value_counts()``` (counts the unique values in a column)

```df[['column_1', 'column_2]]``` (to reference more than one column in a pandas DataFrame)

```df.columns``` (to see all columns in DataFrame)

```df.rename(columns={'old name': 'new name'})``` (to rename columns)

```df.set_index()``` (declare a new index)

```df.count()``` (returns a count of all columns, helps identify incomplete rows)

```df.dropna(how='any')``` (to drop rows with missing information)

```df.fillna(value=<Value>)``` (handling missing values)

```df.replace({})``` (to replace values with other values) 

**Reading and Writing CSVs**

Reading CSV:

```pd.read_csv(file_name)```

Writing CSV:

```pd.to_csv(output_file_name)```

**Exploring Data**

- The ```loc()``` method allows its users to select data using label based indexes. In other words, it takes in strings as the keys and returns data based upon that. Using ```loc()``` to search through rows is only really useful when the index of a dataset is a collection of strings. 
- The ```iloc()``` method also allows its users to select data, but instead of using labels, it instead uses integer based indexing for selection by position. In other words, it selects data in much the same way as one would select data from within a list; using a numeric index.


<a id='pandas_reference_guide'></a>
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


