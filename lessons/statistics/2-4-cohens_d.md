[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>> The difference between the standardized difference of means between the weight of first babies and the weight of other babies is -0.089, which is considered a large effect size. The difference between pregnancy length of first babies comapred to other babies is 0.02 which is considered a small effect size. 

from __future__ import print_function

import sys
import os
import math
import numpy as np

import nsfg
import thinkstats2
import thinkplot
def CleanFemPreg(df):
    df.agepreg /= 100.0

    na_vals = [97, 98, 99]
    df.birthwgt_lb.replace(na_vals, np.nan, inplace=True)
    df.birthwgt_oz.replace(na_vals, np.nan, inplace=True)

    df['totalwgt_lb'] = df.birthwgt_lb + df.birthwgt_oz / 16.0
preg = nsfg.ReadFemPreg()

live = preg[preg.outcome == 1]
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d
first = firsts.totalwgt_lb
other = others.totalwgt_lb
CohenEffectSize(first,other)
first_length = firsts.prglngth
other_length = others.prglngth
CohenEffectSize(first_length,other_length)
