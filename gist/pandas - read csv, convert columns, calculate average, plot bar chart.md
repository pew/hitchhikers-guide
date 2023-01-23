---
date created: Monday, January 23rd 2023, 5:19:39 am
date modified: Monday, January 23rd 2023, 5:20:35 am
tags: 
  - pandas
  - python
  - matplotlib
---

# pandas - read CSV, convert columns, calculate average, plot bar chart

I had [speedtest-cli](https://www.speedtest.net/apps/cli) running on a regular basis to figure out which provider mobile provider works best in a given location. For this, I gathered all speedtest results in a CSV and just wanted to get the average download and upload speed over all entries.

This is how the CSV looks like:

|server name|server id|idle latency|idle jitter|packet loss|download|upload|download bytes|upload bytes|share url|download server count|download latency|download latency jitter|download latency low|download latency high|upload latency|upload latency jitter|upload latency low|upload latency high|idle latency low|idle latency high|
|-----------|---------|------------|-----------|-----------|--------|------|--------------|------------|---------|---------------------|----------------|-----------------------|--------------------|---------------------|--------------|---------------------|------------------|-------------------|----------------|-----------------|
|foobar     |1337     |33.1252     |8.44775    |0          |1067331 |436851|12296456      |4025128     |         |1                    |737.564         |85.5956                |39.424              |1710.7               |323.56        |69.9196              |35.317            |1023               |26.975          |44.814           |

and here's the python script how to convert all the things and display them:

```python
import pandas as pd
import matplotlib.pyplot as plt

"""read csv"""

df = pd.read_csv('results.csv')

"""convert bytes to mbps"""

def bytes_to_mbits(num_bytes):
    return num_bytes * 8 / 1e6

"""take just the download and upload columns from the csv file, convert each entries using the function above, round to two decimal points"""

dl_ul = df[['download', 'upload']]
dl_ul.reset_index(drop=True)

download = round(df['download'].apply(bytes_to_mbits), 2)
upload = round(df['upload'].apply(bytes_to_mbits), 2)

"""take the download and upload results, calculate average, put on bar chart"""

plt.bar(['download', 'upload'], [download.mean(), upload.mean()], color=['green', 'red'])
plt.ylabel('speed in mbit/s')
plt.title('speedtest')
plt.show()
```
