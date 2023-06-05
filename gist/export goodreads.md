---
date created: Monday, June 5th 2023, 4:03:04 pm
date modified: Monday, June 5th 2023, 4:06:30 pm
tags:
  - data
  - goodreads
---

# export goodreads

go to [goodreads](https://goodreads.com/), navigate to one of your books *lists* and copy the rss feed (at the time of this writing it was available in the footer), put the url down below in the script instead of `list_rss/1234?key=abc`.

## usage

```shell
pip install feedparser
```

create a file like `goodreads.py` and put in the contents below:

```python
import feedparser

feed = feedparser.parse("https://www.goodreads.com/review/list_rss/1234?key=abc")

titles = [entry.title for entry in feed.entries]

for title in titles:
    print("- " + title)
```

run it:

```shell
python goodreads.py
```
