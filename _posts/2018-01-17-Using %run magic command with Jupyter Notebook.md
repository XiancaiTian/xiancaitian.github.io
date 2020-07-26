---
layout: post
category: Python
title: Using %run magic command with Jupyter Notebook
---

When working with Jupyter Notebook, in many cases we want to share some code blocks between different notebooks to reduce code redundancy.

<!-- more -->

Good news is that in newer Jupyter, we can achieve this with the **%run** magic command, which allows us to run one jupyter notebook inside another. 

For example, we have a jupyter notebook named utility.ipynb, which defines some utility functions to be used by a set of notebooks. Instead of copy and paste the code in each notebook, we can simply add the following code into the top of each notebook:



```
%run utility.ipynb
```


Running the above magic command give us to whatever is defined in utility.ipynb, including both variables and functions.


[Official doc](http://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-run target="_blank")