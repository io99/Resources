
# Reference Guide: Python API
***
By: Randy :)
<img src="https://cdn-images-1.medium.com/max/1600/1*_JJTknJYPxJPLNEEB3jh7Q.gif"/>

# What is an API?
*** 

An **API (Application Programming Interface)** is something that any particular website can design to this thing called an API to give out their data and allow your web application to communicate with that data. Facebook, Twitter, Yelp, and many other services rely and have their own API's.

With APIs, applications talk to each other without any user knowledge or intervention.

When we want to interact with an API in Python (like accessing web services), we get the **responses** in a form called JSON. 

# What is JSON?
***

**JSON (JavaScript Object Notation)** is a compact, text based format for computers
to exchange data and is once loaded into Python just like a **dictionary**.

JSON data structures map directly to Python data types, which makes this a powerful tool for directly accessing data.

This makes JSON an ideal format for transporting data between a client and a server.

### JSON versus Dictionary
It is apples vs. oranges comparison:

- **JSON** is a data format (a string).

- **Python dictionary** is a data structure (in-memory object).

# Terminologies
***
- **API Key:** When using any API, normally you'll need to acquire an API Key. This key acts as a form of authentication, which can lead to access control
- **Key:** All keys are of string type
- **Value:** Values can be either strings, numbers, lists, booleans, or even another object (dictionary)
- **URL Request:** This is the URL that you can make a request to the website's API with. 
- **Response:** Once a request has been made, you'll recieve a JSON response.
- **Search Query:** This is the query that is used to get back any information of a particular API

<img src="https://developers.giphy.com/static/img/api.c99e353f761d.gif"/>

# How to Query a JSON API in Python
***

### Objective
1. Learn how to communicate with an API in your Python application
2. Learn how to get data out of your JSON format.
3. Learn how to query multiple API calls
4. Learn how to convert our newly acquired JSON objects into a Pandas DataFrame

### Here are the 4 Simple Steps:

1. Import Library Dependencies
2. Create Query URL (which contains the url, apikey, and query filters)
3. Perform a Request Call & Convert to JSON
4. Extract Data from JSON Response (Query it)


## Step 1. Import Library Dependencies


```python
# Dependencies
import requests as req
import json
```

## Step 2. Create Query URL
The Query URL is used to get our information from the API call.

Our Final Query URL should look like this: 

http://api.openweathermap.org/data/2.5/weather?apikey=ada32f6f2c68d7b9107ab5982777180d&q=Cypress&units=metric

**Note:** 
- The "**?**" syntax is used in the begginning of our query string so we can start building a filterized version of our data
- The "**&**" syntax is used to perform our different types of queries, in this case one for city and units



```python
# A. Get our base URL for the Open Weather API
base_url = "http://api.openweathermap.org/data/2.5/weather"

# B. Get our API Key 
key = "ada32f6f2c68d7b9107ab5982777180d"

# C. Get our query (search filter)
query_city = "Cypress"
query_units = "metric"

# D. Combine everything into our final Query URL
query_url = base_url + "?apikey=" + key + "&q=" + query_city + "&units=" + query_units

# Display our final query url
query_url

```




    'http://api.openweathermap.org/data/2.5/weather?apikey=ada32f6f2c68d7b9107ab5982777180d&q=Cypress&units=metric'



## Step 3. Perform a Request Call & Convert to JSON
Using our **req.get()** method, we'll get back a response from our Weather Map API with the filtered queries. Then just call the **.json()** at the end to convert it into a JSON format (aka dictionary)



```python
# Store our response in a variable
response = req.get(query_url).json()

response

```




    {'coord': {'lon': -95.7, 'lat': 29.97},
     'weather': [{'id': 721,
       'main': 'Haze',
       'description': 'haze',
       'icon': '50d'}],
     'base': 'stations',
     'main': {'temp': 29.6,
      'pressure': 1011,
      'humidity': 79,
      'temp_min': 28,
      'temp_max': 31},
     'visibility': 11265,
     'wind': {'speed': 5.1, 'deg': 150, 'gust': 8.2},
     'clouds': {'all': 92},
     'dt': 1529513400,
     'sys': {'type': 1,
      'id': 2640,
      'message': 0.0107,
      'country': 'US',
      'sunrise': 1529493737,
      'sunset': 1529544413},
     'id': 4684724,
     'name': 'Cypress',
     'cod': 200}



## Step 4. Extract Data from JSON Response
Finally, we're able to access our JSON object and extract information from it just as if it was a **Python Dictionary**.

Remember, a JSON object contains a **key-value pair**.



```python
# Extract the temperature data from our JSON Response
temperature = response['main']['temp']
print ("The temperature is " + str(temperature))

# Extract the weather description from our JSON Response
weather_description = response['weather'][0]['description']
print ("The description for the weather is " + weather_description)

```

    The temperature is 29.6
    The description for the weather is haze
    

## How to Perform Multiple API Calls
***
So far so good, right? In five simple steps, you were able to perform an API request call, convert it into a JSON format, and extract information from it! 

But this was only for one query. What if we wanted to query multiple cities? **Here's how:**



```python
# A. Get our base URL for the Open Weather API
base_url = "http://api.openweathermap.org/data/2.5/weather"

# B. Get our API Key 
key = "ada32f6f2c68d7b9107ab5982777180d"

# C. Create an empty list to store our JSON response objects
weather_data = []

# D. Define the multiple cities we would like to make a request for
cities = ["London", "Paris", "Las Vegas", "Stockholm", "Sydney", "Hong Kong"]

# E. Read through each city in our cities list and perform a request call to the API.
# Store each JSON response object into the list
for city in cities:
    query_url = base_url + "?apikey=" + key + "&q=" + city
    weather_data.append(req.get(query_url).json())
    
# Now our weather_data list contains five different JSON objects for each city
# Print the first city (London) 
weather_data[0]
```




    {'coord': {'lon': -0.13, 'lat': 51.51},
     'weather': [{'id': 803,
       'main': 'Clouds',
       'description': 'broken clouds',
       'icon': '04d'}],
     'base': 'stations',
     'main': {'temp': 295.94,
      'pressure': 1018,
      'humidity': 53,
      'temp_min': 294.15,
      'temp_max': 298.15},
     'visibility': 10000,
     'wind': {'speed': 5.7, 'deg': 260},
     'clouds': {'all': 75},
     'dt': 1529513400,
     'sys': {'type': 1,
      'id': 5091,
      'message': 0.0061,
      'country': 'GB',
      'sunrise': 1529466180,
      'sunset': 1529526089},
     'id': 2643743,
     'name': 'London',
     'cod': 200}



## Extract Multiple Queries and Store in Pandas DataFrame


```python
# Extract the city name, temperature, and weather description of each City
city_name = [data['name'] for data in weather_data]
temperature_data = [data['main']['temp'] for data in weather_data]
weather_description_data = [data['weather'][0]['description'] for data in weather_data]

# Create a dictionary containing our newly extracted information
weather_data = {"City": city_name, 
                "Temperature": temperature_data,
                "Weather Description": weather_description_data}

```


```python
# Convert our dictionary into a Pandas Data Frame
weather_data = pd.DataFrame(weather_data)
weather_data

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
      <th>City</th>
      <th>Temperature</th>
      <th>Weather Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>London</td>
      <td>295.94</td>
      <td>broken clouds</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Paris</td>
      <td>300.77</td>
      <td>clear sky</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Las Vegas</td>
      <td>306.30</td>
      <td>clear sky</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Stockholm</td>
      <td>286.20</td>
      <td>light rain</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sydney</td>
      <td>282.97</td>
      <td>broken clouds</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Hong Kong</td>
      <td>302.06</td>
      <td>few clouds</td>
    </tr>
  </tbody>
</table>
</div>


