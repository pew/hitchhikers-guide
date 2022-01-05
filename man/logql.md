# logql

query language used in Grafana for loki (and other things?) logs

## ignore errors

since I can't never seem to remember this. parse logs to json and ignore all errors to get your results:

```
{job="your-job-name"} | json | __error__ = "" | OriginResponseStatus=200
```
