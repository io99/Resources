
# Matplotlib Reference Guide
***

<img src="https://matplotlib.org/_static/logo2.svg"/>


<img src="http://u01.appmifile.com/images/2017/02/07/a464f0b0-75dc-4806-974a-2e84c2e0bc6c.gif"/>

**Note:** Remember, there's so much information out there. Don't be afraid to explore and learn the various tools out there for visualization. 

*"If you're not Googling, you're not trying"* **- Anonymous :-)**

# Background
***

### Importance of Visualization
Humans are very visual creatures. We understand things better when we see things visualized. However, the step to presenting analyses, results or insights can be a bottleneck: you might not even know where to start or you might have already a right format in mind. Luckily for you, there is Matplotlib!

### Types of Graphs
Matplotlib is a python library that help us to plot data. The easiest and basic plots are **line, scatter** and **histogram** plots.

- **Line plot** is better when x axis is time.
- **Scatter plot** is better when there is correlation between two variables
- **Histogram** is better when we need to see distribution of numerical data.
- **Customization**: Colors,labels,thickness of line, title, opacity, grid, figsize, ticks of axis and linestyle


### Anatomy of Matplotlib
The anatomy of Matplotlib can be simply broken down into: **figure, axes, tick labels, (X,Y)-axis labels, title, and legend.**

- **Figure:** The Figure is the overall window or page that everything is drawn on.

- **Axes:** Ontop of a figure are axes. The Axes is the area on which the data is plotted with functions such as plot(). It contains your ticks, labels, etc.

- **Tick Labels:** These are the values, which are the locations along the x and y axis where the tick marks appear.

- **Axis Labels:** These are your X and Y axis column name that represents the type of values you're displaying.

- **Title:** This is just the title of your graph

- **Legend:** This represents your graph's key, which represents the different categories of your visualization. It requires handles as parameters


<img src="https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Matplotlib+Tutorial/content_content_unknown.png"/>

# Matplotlib Cheat Sheet
***

Matplotlib is a is a plotting library for the Python programming language. It allows to make quality charts in few lines of code. Most of the other python plotting library are build on top of Matplotlib. 

It makes that a basic understanding
of matplotlib is probably needed to make any chart with python. I highly advise you to have a look to the matplotlib homepage and have a look to this general concept page. 

This page aims to give a few tip concerning the general
usage of Matplotlib. It gives examples showing how to custom your title, the colors of your chart, how to annotate it etc.

**Resource:** https://www.datacamp.com/community/tutorials/matplotlib-tutorial-python#anatomy

<img src="https://python-graph-gallery.com/wp-content/uploads/Matplotlib_cheatsheet_datacamp.png">


# Matplotlib Basic Plot
***

### Step 1: Prepare Data

For now to keep it simple, let's prepare our dataset by creating two arrays. One for year values and the other for population values.



```python
# This magic function allows you to display your graphs without the need of plt.show()
%matplotlib inline

# Import the matplotlib library
import matplotlib.pyplot as plt

# Prepare your dataset
year = [1950, 1960, 1970, 1980, 1990, 2000, 2010, 2020]
population = [3, 4, 5, 6, 7.5, 9, 11, 15]
baby_population = [0.5, 1, 2, 3, 6, 8, 12, 13]

```

### Step 2: Create Plot
Apply the plot() function and pass in two parameters: your **x-values** and **y-values**



```python
# A. Create two plots
population_handle, = plt.plot(year, population, color='red', label='World Population')
baby_handle, = plt.plot(year, baby_population, color='blue', label='Baby Population')

# =============================================================================================
# Modify Aesthics of Your Graph
# =============================================================================================

# Create a title for your graph
plt.title('World Population Projection')

# Label your X-Axis
plt.xlabel('Year')

# Label your Y-Axis
plt.ylabel('Population (In Billions)')

# Modify your Y-Axis Ticks 
plt.yticks([0,3,6,9,12,15,18],['0','3B','6B','9B','12B','15B','18B'])

# Display a grid layout on the graph
plt.grid()

# Define and display your Legend
plt.legend(handles=[population_handle,baby_handle],loc='upper right')
```




    <matplotlib.legend.Legend at 0x231bfee0be0>




![png](output_3_1.png)


<img src="https://78.media.tumblr.com/079b3f8397250a4fc44648a79d6e9c61/tumblr_ns93qmgJOv1updbngo1_500.gif"/>

# Pandas Plot Examples
***
Not only are Pandas used for data manipulation, but Pandas also has a built in function that allows you to perform simple and powerful graphs from Matplotlib itself! We'll dive into three common graphs: Scatter Plot, Histograms, and 




```python
# Import the necessary libraries 
import pandas as pd
import matplotlib.pyplot as plt

# Prepare your dataset
year = [1950, 1960, 1970, 1980, 1990, 2000, 2010, 2020]
population = [3, 4, 5, 6, 7.5, 9, 11, 15]
baby_population = [0.5, 1, 2, 3, 6, 8, 12, 13]

# Convert your list into a DataFrame
world_df = pd.DataFrame({"Year":year, "World Population":population, "Baby Population":baby_population})

```


```python
# Examine the first five observations in your DataFrame
world_df.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>World Population</th>
      <th>Baby Population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1950</td>
      <td>3.0</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1960</td>
      <td>4.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1970</td>
      <td>5.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1980</td>
      <td>6.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1990</td>
      <td>7.5</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>



## Line Plot 


```python
# Use your DataFrame to create a line plot
world_df.plot(x="Year", y="World Population", kind = 'line', color = 'blue',label = 'World Population',alpha = 0.5, grid = True)

plt.xlabel('Years')              
plt.ylabel('World Population')
plt.title('World Population Line Plot')           
plt.show()

```


![png](output_8_0.png)


# Scatter Plot


```python
world_df.plot(kind='scatter', x='World Population', y='Year',alpha = 0.5,color = 'red')
plt.xlabel('World Population')              
plt.ylabel('Year')
plt.title('World Population Scatter Plot')            
plt.show()

```


![png](output_10_0.png)


# Histogram


```python
world_df["Baby Population"].plot(kind = 'hist',bins = 20,figsize = (10,4), color='green')
plt.xlabel('Baby Population')              
plt.ylabel('Frequency')
plt.title('Baby Population Histogram')            
plt.show()

```


![png](output_12_0.png)

