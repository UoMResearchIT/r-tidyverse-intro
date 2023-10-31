---
layout: page
title: Setup
permalink: /setup/
---
## Files
*We will be using some example data in the lesson.  Download the file from [here]({{ page.root }}/data/r-novice.zip) and extract it to your computer*

## Software
This lesson assumes you have the _R_ and _Rstudio_ software installed on your computer. This should already be the case if you are using the University computers on a cluster.

1.  _R_ can be downloaded [here](https://www.stats.bris.ac.uk/R/). Select the precompiled binary distribution for your operating system.

2.  _Rstudio_ is an environment for code development using _R_. It can be downloaded [here](https://www.rstudio.com/products/rstudio/download/). You will need the Desktop version for your computer; scroll to the bottom of the page for links.

#### University Managed Laptop (Windows)
To install R and RStudio on a University managed windows machine, go to Software Centre to install: `R (4.2.3)`, `Rtools`, and `R Studio`

#### 😱 Help! It is the Day 1 of the course and I didn't install R/R Studio

If this is you, we recommend that you either:

+  Log on to a University of Manchester Cluster PC. RStudio is available in most computer clusters including the Main Library, AGLC, Stopford and AMBS.

+  Use [_R Studio Cloud_](https://login.rstudio.cloud/) (an online version of _RStudio_). This service is not associated with the University of Manchester. You should take care to ensure that you only sign up for a free account.

## Packages

The course teaches the [tidyverse](https://www.tidyverse.org), which is a collection of _R_ packages that are designed to make many common data analysis tasks easier. Cluster computers already have the tidyverse installed. If you are using your own laptop *please* install this before the course.  You can do this by starting _Rstudio_, and typing:

```{r}
install.packages("tidyverse")
```

At the `>` prompt in the left hand window of RStudio.   You may be prompted to select a mirror to use; either select one in the UK, or the "cloud" option at the start of the list.

R will download the packages that constitute the tidyverse, and then install them.  This can take some time.  You may get a prompt `There are binary versions available but the source versions are later` and asking if you want to install from sources packages which require compilation.  You should answer no to this.

If you are using a mac you may be prompted whether you wish to install binary or source versions of the packages; you should select binary.

On Linux, several of the packages will be compiled from source.  This can take several minutes.  You may find that you need to install additional development libraries to allow this to happen.  

There will be a number of messages displayed during installation. After the installation has completed you should see a message containing:

```
** testing if installed package can be loaded
* DONE (tidyverse)
```

## Testing your installation

Type the following commands at the `>` prompt:

```{r}
library(tidyverse)
ggplot(cars, aes(x=speed, y=dist)) + geom_point()
```

(the message about conflicts can be safely ignored)

This should produce a plot in the lower right hand window of RStudio.

If you encounter difficulties installing R, RStudio or the Tidyverse please contact martin.herreriasazcue@manchester.ac.uk before the course starts. There is little time to resolve installation problems on the day.

