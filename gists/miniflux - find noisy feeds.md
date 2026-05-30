---
date created: Sunday, February 1st 2026, 4:23:45 pm
date modified: Sunday, February 1st 2026, 4:30:04 pm
tags:
  - miniflux
  - rss
---

# miniflux - find noisy feeds

[miniflux](https://miniflux.app/) is my RSS reader of choice. I wanted to list all *noisy* feeds.

## feeds with most entries over a 7 day period

- list feeds sorted by the amount of entries for the last 7 days
- also prints out an average per day

```sql
WITH bounds AS (
  SELECT
    ((date_trunc('day', now() AT TIME ZONE 'Europe/Stockholm') - interval '6 days') AT TIME ZONE 'Europe/Stockholm') AS start_ts,
    ((date_trunc('day', now() AT TIME ZONE 'Europe/Stockholm') + interval '1 day') AT TIME ZONE 'Europe/Stockholm') AS end_ts
)
SELECT
  f.id AS feed_id,
  f.title,
  f.feed_url,
  count(*) AS entries_7d,
  round(count(*) / 7.0, 2) AS avg_per_day,
  max(e.created_at) AS last_seen_at
FROM entries e
JOIN feeds f ON f.id = e.feed_id
WHERE e.user_id = 1
  AND e.created_at >= (SELECT start_ts FROM bounds)
  AND e.created_at <  (SELECT end_ts   FROM bounds)
  AND e.status <> 'removed'
GROUP BY f.id, f.title, f.feed_url
ORDER BY entries_7d DESC
LIMIT 50;
```
