---
layout: default
title: Python convert datetime by timezone
---

```python
def get_local_datetime_from_utc(t):
    from dateutil import tz
    
    utc = t.replace(tzinfo=tz.gettz('UTC'))
    local_datetime = utc.astimezone(tz.tzlocal())
    return local_datetime.replace(tzinfo=None)
```

http://stackoverflow.com/questions/4770297/python-convert-utc-datetime-string-to-local-datetime
