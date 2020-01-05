[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> **Biased Mean is 135% hight than actual.  As expected, PMF of family with no child is zero in biased distribution**

from __future__ import print_function, division

%matplotlib inline

import numpy as np
import math
import nsfg
import first
import thinkstats2
import thinkplot

#read in data
resp = nsfg.ReadFemResp()

pmf = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')

#function to calculate biased pmf
def BiasPmf(pmf,label):
    new_pmf = pmf.Copy(label=label)
    
    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf

#biased pmf
biased = BiasPmf(pmf, label='biased')

#Plot of actual and biased distribution
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased])
thinkplot.Config(xlabel='Number of children', ylabel='PMF')

#actual means and biased means
print('Actual Mean:',pmf.Mean())
print('Biased Mean:',biased.Mean())