

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import os
```


```python
os.listdir("input")
```




    ['circuits.csv',
     'status.csv',
     'drivers.csv',
     'driverStandings.csv',
     'races.csv',
     'constructors.csv',
     'constructorResults.csv',
     'lapTimes.csv',
     'qualifying.csv',
     'pitStops.csv',
     'seasons.csv',
     'constructorStandings.csv',
     'results.csv']




```python
constructors = pd.read_csv("input/constructors.csv",encoding="latin1")
constructors[:10]
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
      <th>constructorId</th>
      <th>constructorRef</th>
      <th>name</th>
      <th>nationality</th>
      <th>url</th>
      <th>Unnamed: 5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>mclaren</td>
      <td>McLaren</td>
      <td>British</td>
      <td>http://en.wikipedia.org/wiki/McLaren</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>bmw_sauber</td>
      <td>BMW Sauber</td>
      <td>German</td>
      <td>http://en.wikipedia.org/wiki/BMW_Sauber</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>williams</td>
      <td>Williams</td>
      <td>British</td>
      <td>http://en.wikipedia.org/wiki/Williams_Grand_Pr...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>renault</td>
      <td>Renault</td>
      <td>French</td>
      <td>http://en.wikipedia.org/wiki/Renault_F1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>toro_rosso</td>
      <td>Toro Rosso</td>
      <td>Italian</td>
      <td>http://en.wikipedia.org/wiki/Scuderia_Toro_Rosso</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>ferrari</td>
      <td>Ferrari</td>
      <td>Italian</td>
      <td>http://en.wikipedia.org/wiki/Scuderia_Ferrari</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>toyota</td>
      <td>Toyota</td>
      <td>Japanese</td>
      <td>http://en.wikipedia.org/wiki/Toyota_Racing</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>super_aguri</td>
      <td>Super Aguri</td>
      <td>Japanese</td>
      <td>http://en.wikipedia.org/wiki/Super_Aguri_F1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>red_bull</td>
      <td>Red Bull</td>
      <td>Austrian</td>
      <td>http://en.wikipedia.org/wiki/Red_Bull_Racing</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>force_india</td>
      <td>Force India</td>
      <td>Indian</td>
      <td>http://en.wikipedia.org/wiki/Force_India</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
constructors_data = dict()
for index, row in constructors.iterrows():
    if row["nationality"] in constructors_data.keys():
        constructors_data[row["nationality"]]+=1
    else:
        constructors_data[row["nationality"]]=1
constructors_data
```




    {'British': 85,
     'German': 10,
     'French': 12,
     'Italian': 29,
     'Japanese': 5,
     'Austrian': 1,
     'Indian': 1,
     'Dutch': 3,
     'Russian': 2,
     'Swiss': 4,
     'Irish': 1,
     'Hong Kong': 1,
     'Brazilian': 1,
     'Canadian': 2,
     'Mexican': 1,
     'American': 39,
     'Australian': 1,
     'New Zealand': 1,
     'South African': 3,
     'Rhodesian': 1,
     'Belgium': 1,
     'East German': 1,
     'Spanish': 1,
     'Malaysian': 2}



# Country wise Constructors


```python
import plotly 
import plotly.plotly as py
import plotly.graph_objs as go

data=[go.Bar(
            x=list(constructors_data.keys()),
            y=list(constructors_data.values())
    )]

py.iplot(data, filename='Country wise Constructors')
```

    /Users/neelpatel/anaconda3/lib/python3.6/site-packages/IPython/core/display.py:689: UserWarning:
    
    Consider using IPython.display.IFrame instead
    





<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~neelpatel05/2.embed" height="525px" width="100%"></iframe>




```python
data=go.Pie(labels=list(constructors_data.keys()), values=list(constructors_data.values()))
py.iplot([data], filename='Country wise Constructors Percentage')
```




<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~neelpatel05/4.embed" height="525px" width="100%"></iframe>




```python

```
