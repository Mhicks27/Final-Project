# MCPN (Most Convenient Pittsburgh Neighborhood)

MCPN is a Python library for collecting data on the convenience of public internet, transportation and grocery stores in the neighborhood.

# Team Name

Just Kidding

# Group Number

14

# Team Members

Madison Hickman: mrh176@pitt.edu
Jenna Higgins: jkh79@pitt.edu

# Data Sets
[Allegheny County Supermarkets and Convenience Stores](https://data.wprdc.org/dataset/allegheny-county-supermarkets-convenience-stores/resource/626357fa-c95d-465f-9a02-3121655b2b78?view_id=a6bdfc00-061c-4586-a7c2-008a0528fa9b) Gives data on how many supermarkets and convenience stores are in the zip code. 

[Public Wi-Fi Locations](https://data.wprdc.org/dataset/public-wifi-locations) Gives data on how many locations there are for public Wi-Fi. 

[Monthly on time performance for Port Authority](https://data.wprdc.org/dataset/port-authority-monthly-average-on-time-performance-by-route) Gives Data on average monthly times for Port Authority buses. 

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install MCPN.

```bash
pip install MCPN
```

## Usage

```python
import MCPN
```

### Amount of locations with public Wi-Fi (analyzed by Madison)

```python
import pandas as pd

wifi = pd.read_csv("Wifi-data.tsv", sep='\t')

wifi.head()

mport pandas as pd
import numpy as np
%matplotlib inline
import matplotlib.pyplot as plt

codes = pd.read_csv("Wifi-data.tsv", sep="\t")
unique= codes['zip'].value_counts().rename_axis('Zip Codes').to_frame(name='Wifi Count')

#data = unique.value_counts().rename_axis('Zip Codes').to_frame(name='Store Count')
pd.set_option('display.max_rows',500)
pd.set_option('display.max_columns',500)
pd.set_option('display.width',1000)

#print(data)

unique.plot.bar()

unique.head(90)
```


### Amount of grocery/convenience stores (analyzed by Madison)

```python

import pandas as pd

stores = pd.read_csv("Grocery-data.tsv", sep='\t')

stores.head()

import pandas as pd
import numpy as np
%matplotlib inline
import matplotlib.pyplot as plt

codes = pd.read_csv("Grocery-data.tsv", sep="\t")
unique= codes['Zip'].value_counts().rename_axis('Zip Codes').to_frame(name='Store Count')

#data = unique.value_counts().rename_axis('Zip Codes').to_frame(name='Store Count')
pd.set_option('display.max_rows',500)
pd.set_option('display.max_columns',500)
pd.set_option('display.width',1000)

#print(data)

unique.plot.bar()

unique.head(90)
```

### Average accuracy of Port Authority buses (analyzed by Jenna)

```python

import pandas as pd
import numpy as np
%matplotlib inline
import matplotlib.pyplot as plt
#turning tsv file into data frame
bus_accuracy = pd.read_csv('Bus_Accuracy.tsv', delimiter='\t')
#example
bus_accuracy.head()

## there is a list full of dictionaries with what bus routes are in each neighborhood,
## but for the sake of ease of reading I have not shown it here

results = []
#iterating through each dictionary in list
for code_dict in neighborhood:
    name = code_dict['name']
    codes = code_dict['codes']
    # separating info
    df_filtered = bus_accuracy[bus_accuracy['ridership_route_code'].isin(codes)]
    #calculating mean
    mean = df_filtered['on_time_percent'].mean()
    results.append({"neighborhood": name, "accuracy": mean})
#turning data into a new data frame
fin = pd.DataFrame(results)

# creating a graph that displays the accuracy of each neighborhood (by their index in fin)
fin.plot.line()
plt.show()

# example of what the list looks like!
# add this to see full DF
# pd.set_option('display.max_rows', 90)
fin
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
