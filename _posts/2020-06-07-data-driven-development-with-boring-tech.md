---
layout: post
title:  "Data-Driven Development + Boring Technology"
date:  20200607 22:19:52 +0800
categories: default
tags:
 - Engineering
 - just-ship
 - fail-fast
---

I'm reading [Dan McKinley](https://mcfunley.com/)'s posts -- very interesting and practical.


# Choosing Tech stack 

> The nice thing about boringness (so constrained) is that the capabilities of these things are well understood. But more importantly, their failure modes are well understood

> When choosing technology, you have both known unknowns and unknown unknowns [
 - A known unknown is something like: we don’t know what happens when this database hits 100% CPU.
 - An unknown unknown is something like: geez it didn’t even occur to us that writing stats would cause GC pauses.
Both sets are typically non-empty, even for tech that’s existed for decades. But for shiny new technology the magnitude of unknown unknowns is significantly larger, and this is important.
 
> Adding technology to your company comes with a cost. As an abstract statement this is obvious: if we’re already using Ruby, adding Python to the mix doesn’t feel sensible because the resulting complexity would outweigh Python’s marginal utility. But somehow when we’re talking about Python and Scala or MySQL and Redis people lose their minds, discard all constraints, and start raving about using the best tool for the job.

should read all the details:  https://mcfunley.com/choose-boring-technology


# Data-Driven for resource allocating

I have a great idea, we should try this!

Maybe not. aways think about the cost/benifit. reduce the feedback loop, fail fast.

watch the video here: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/SZOeV-S-2co?start=450" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>