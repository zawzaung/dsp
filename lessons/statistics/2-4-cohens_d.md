[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

 

>>The mean total weight of first babies is 7.2 lbs and the mean total weight of other babies is 7.33 lbs. Also looking at the histogram, first babies tend to weight less than other babies. Cohen's d of total weight is 0.089. The difference in mean for total weight is 0.089 standard deviation, whereas cohen's d of pregency length is 0.029. Both of these effect size are trivial.


from __future__ import print_function, division

%matplotlib inline

import numpy as np
import math
import nsfg
import first
import thinkstats2
import thinkplot

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

#read the total weight(lb) data of first and other babies
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

first_hist = thinkstats2.Hist(firsts.totalwgt_lb, label='first')
other_hist = thinkstats2.Hist(others.totalwgt_lb, label='other')

# plot histogram
width = 0.01
thinkplot.PrePlot(2)
thinkplot.Hist(first_hist, align='right', width=width)
thinkplot.Hist(other_hist, align='left', width=width)
thinkplot.Config(xlabel='total weight (lb)', ylabel='Count', xlim=[6, 8])

#Find mean,var,std of first babies
mean_firsts = firsts.totalwgt_lb.mean()
var_firsts = firsts.totalwgt_lb.var()
std_firsts = firsts.totalwgt_lb.std()

#Find mean,var,std of other babies
mean_other = others.totalwgt_lb.mean()
var_other = others.totalwgt_lb.var()
std_other = others.totalwgt_lb.std()

def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d

#Computer Cohen's d for first and other babies' total weight(lb)
CohenEffectSize(firsts.totalwgt_lb,others.totalwgt_lb)
