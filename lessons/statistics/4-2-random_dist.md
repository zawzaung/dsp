[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> **The random funcition is not really random.  The distributions are uniform.**

from __future__ import print_function, division

%matplotlib inline

import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot

#generate random numbers
nums = np.random.random(1000)

#find pmf of random numbers and plot
nums_pmf = thinkstats2.Pmf(nums)
thinkplot.Pmf(nums_pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random numbers', ylabel='PMF')

#find cdf of random numbers and plot
nums_cdf = thinkstats2.Cdf(nums)
thinkplot.Cdf(nums_cdf)
thinkplot.Config(xlabel='Random numbers', ylabel='CDF')

