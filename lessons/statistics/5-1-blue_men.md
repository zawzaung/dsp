[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> **34% of US male population is between 5'10" and 6'1".**

from __future__ import print_function, division

%matplotlib inline

import numpy as np
import nsfg
import analytic
import thinkstats2
import thinkplot
import scipy.stats

#scipy.stats.norm for normal distribution

mu = 178
sigma = 7.7
norm_distribution = scipy.stats.norm(loc=mu, scale=sigma)

#find percentages of population below 5'10" and 6'1".  The differnce of two is population eligible to join Blue Men

below_5_10 = norm_distribution.cdf(177.8)    # 5'10" height in cm
below_6_1 = norm_distribution.cdf(185.4)     # 6'1" height in cm
blue_men_eligible = below_6_1 - below_5_10
print(blue_men_eligible)