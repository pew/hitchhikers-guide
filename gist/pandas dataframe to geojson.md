---
tags: 
  - pandas
  - geojson
  - python
date created: Monday, August 22nd 2022, 4:56:46 am
date modified: Monday, August 22nd 2022, 4:59:21 am
---

# pandas dataframe to geojson

```python
import io
import json
import requests
import pandas as pd

# get text from request
data = response.text

# set column names for csv like input
colnames = ['country', 'colo', 'lat', 'lon', 'ms']

# read csv from response object, separate by tab, set column names
df = pd.read_csv(io.StringIO(data), sep="\t", names=colnames, header=None, parse_dates=True)

# geojson skeleton
geojson = {"type": "FeatureCollection", "features": []}

# go through dataframe, append entries to geojson format
for _, row in df.iterrows():
    feature = {"type": "Feature", "geometry": {"type": "Point", "coordinates": [row['lon'], row['lat']]}, "properties": {"colo": row["colo"], "ms": row['ms']}}
    geojson['features'].append(feature)

with open('result.geojson', 'w') as fp:
    json.dump(geojson, fp)
```
