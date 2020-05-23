---
layout: post
title:  "Slugify strings with pure Regex and Python"
date:  20200523 18:07:03 +0800
categories: default 
tags:
 - python
 - regex
---

There are many libs to do slugify, that's cool. but if you just want to slugify simple strings without any dependency, you may want to try:

```
import re


def slugify(s: str) -> str:
    s_after_basic_replacement = re.sub("[^a-zA-Z0-9]", "-", s)
    s_with_no_continues_dash = re.sub("[-]+", "-", s_after_basic_replacement)
    s_with_no_ending_dash = re.sub("-$", "", s_with_no_continues_dash)
    return s_with_no_ending_dash


if __name__ == '__main__':
    print(slugify("is this a good title? "))
    # is-this-a-good-title

```

purely simple `regex` (yes, I agree, I'm bad at regex, so I copy/pasted all from stackoverflow)

