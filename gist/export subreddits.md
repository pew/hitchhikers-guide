---
date created: Monday, June 5th 2023, 4:19:23 pm
date modified: Monday, June 5th 2023, 4:21:36 pm
tags:
  - data
  - reddit
---

# export subreddits

1. [create a new reddit app](https://www.reddit.com/prefs/apps/)
2. select `script` for the app type
3. use `http://localhost:8000` as the redirect url
4. note the client id and secret id
5. put all the information down below in the script

## usage

to get a list of your subscribed subreddits:

```shell
pip install praw
```

create a file such as `subreddits.py`:

```python
import praw

reddit = praw.Reddit(
    client_id="client_id",
    client_secret="your_secret_id",
    user_agent="export",
    username="your_username",
    password="your_password",
)

# Get list of subscribed subreddits
subscribed_subreddits = [sub.display_name for sub in reddit.user.subreddits(limit=None)]

# Print the list
for sub in subscribed_subreddits:
    print("- {}".format(sub))
```

run the script to get a list of your subreddits.
