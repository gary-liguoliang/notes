---
layout: post 
title: debugging notes
tags:
- debugging
---

it was a Thursday afternoon, I sat with my teammate walking though a long (manual) release plan. remote login, clicking, double clicking…. I got bored in 10 minutes. Before I fall asleep, a testing issue popped up: a user was deleted in the DB. our boss wants to know what happened, immediately. 

it's the second time of this issue, a database trigger was created after the first deletion. so we can get the audit trail. we found the deletion record. 
however, there're many timestamp in the audit trail, so we picked up one called 'last_modified', it was two days ago and it happens on CI-Node-A, 
so we logged in to the CI, try to find which job was running and try to collect some logs. 

however, no luck. we identified one job, but the log looks good, no database interaction found. 

then we get back to the database again, we're so confused with the timestamps of the audit trail, so we try to get the trigger details: a filed called 'last_change' contains the `getdate()`. 
with the 'last_change' datetime, we managed to find the job and what happened to the database. 

## what I learned
**Trust and Verify**

I should not trust anyone, especially myself. 

**If you're tired, take a break**






