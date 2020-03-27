[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> The CDF plot is a straight line (approximately), so the distribution is uniform.
```
from __future__ import print_function, division
%matplotlib inline
import numpy as np
import nsfg
import first
import thinkstats2
import thinkplot
```

```
random = np.random.random(1000)
pmf = thinkstats2.Pmf(random)
thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random', ylabel='PMF')
```

```
cdf = thinkstats2.Cdf(random)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='Random', ylabel='CDF')
```
