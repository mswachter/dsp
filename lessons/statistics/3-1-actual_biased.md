[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> Unbiased mean=1.024205155043831, biased mean=2.403679100664282


from __future__ import print_function

import math
import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot

resp = nsfg.ReadFemResp()
resp2=resp.numkdhh
pmf = thinkstats2.Pmf(resp2)
def BiasPmf(pmf, label=''):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
 
thinkplot.Pmf(pmf)
thinkplot.Config(xlabel='Children Under 18', ylabel='pmf')
biased = BiasPmf(pmf, label='biased')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased])
thinkplot.Show(xlabel='Children Under 18', ylabel='PMF')
pmf.Mean()
biased.Mean()'''
