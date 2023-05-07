---
date created: Sunday, May 7th 2023, 11:35:46 am
date modified: Sunday, May 7th 2023, 11:36:54 am
tags:
  - cpufrequtils
  - cpu
---

# cpufrequtils

see also [cpupower](cpupower.md)

**install:**

```shell
apt-get install cpufrequtils
systemctl enable cpufrequtils
```

## set cpu governor

```shell
echo 'GOVERNOR="powersave"' | sudo tee /etc/default/cpufrequtils
systemctl restart cpufrequtils.service
```
