---
title: Using R Packages
teaching: 15
exercises: 10
questions:
- "How do find packages that will help us with our work?"
- "How do we understand the contents of an R package?"
objectives:
- "To be able to use CRAN task views to identify packages to solve a problem."
- "To understand sources of help for using a package" 
- "To understand how to install a package"
- "To understand where R installs packages to, and issues with permissions"
keypoints:
- "Install packages from CRAN using install.package()"
- 'Load an installed package using libarary("packagename")'
- "sessionInfo() gives information on loaded packages"
- "The .libPaths() function lets us get and set where packages are installed to"
source: Rmd
---


At the start of the course we showed how to install packages in R, and installed some packages that we've been using in the rest of the course.  In this lesson we will cover finding packages that will be useful in *your* research.  One of the many strengths of R is its packaging system; this makes it easy to use others' code in your analysis, and (relatively) easy to distribute code you have written for others to use.  

The aim of this lesson is to provide an overview of the process of finding, loading, understanding and using an R package.  I will illustrate this with an example I'm familiar with, but the ideas presented are applicable to all research areas.

In addition to providing a convenient way of providing an a set of tools to perform a task, packages can also call code written in other languages.  In many packages much of the computationally intensive work is performed with code written in C or Fortran; this can provide a huge boost in execution speed compared to running native R code.

There are several sources of packages in R:

## CRAN

[CRAN](https://cran.r-project.org) is the main repository of packages for R.  All the packages have undergone basic quality assurance when they were submitted.  There are over 10,000 packages in the archive; there is a lot of overlap between some packages.  Working out _what_ the most appropriate package to use isn't always straightforward.   

## Bioconductor

[Bioconductor](https://www.bioconductor.org/) is a more specalised repository, which contains packages for bioinformatics.  Common workflows are provided, and the packages are more thoroughly quality assured.   Because of its more specialised nature we don't focus on Bioconductor in this course.

## Github / personal websites

Some authors distribute packages via [Github](https://www.github.com) or their own personal web-pages.  These packages may not have undergone any form of quality assurance.   Note that many packages have their own website, but the package itself is distributed via CRAN. 

## Finding packages to help with your research

There are various ways of finding packages that might be useful in your research:

* The [CRAN task view](https://cran.r-project.org/web/views/) provides an overview of the packages available for various research fields and methodologies.   

* Journal articles should cite the R packages they used in their analysis. 

* [The Journal of Statistical Software](https://www.jstatsoft.org/index) contains peer-reviewed articles for R packages (and other statistical software)

* [The R Journal](https://journal.r-project.org/) contains articles about new packages in R.

* Asking colleagues

## Example; meta analysis of clinical trial data

Meta-analysis is a statistical technique that lets us combine the results of similar experiments, to obtain a better estimate of the effect we are trying to observe.  It is widely used in many research fields, including physics and medicine.   Assume we've been given some data that we have to meta-analyse, and we know that we want to fit a model using the inverse-variance method (this is a relatively simple meta-anlysis model) but we're not sure what the best package to use is.

A Google search for "meta analysis R" suggests a package called "meta" on CRAN.  It also returns a link to the [R task view](https://cran.r-project.org/web/views/MetaAnalysis.html) for meta analysis.  How do we choose?

Look at the package page for each of the 4 packages:

* [epiR](https://cran.r-project.org/web/packages/epiR/index.html)
* [meta](https://cran.r-project.org/web/packages/meta/index.html)
* [metafor](https://cran.r-project.org/web/packages/metafor/index.html)
* [rmeta](https://cran.r-project.org/web/packages/rmeta/index.html)

Any of these packages should be able to do the task we want.  Useful things to look for when deciding which package to use:

* Package updated regularly (look at version number, publication date)
* How easy it will be to use -- the reference manual is not a tutorial.  Package vignettes are often tutorials.
* Colleagues' recommendations
* Good software development practice:
    # Version control
    # Good documentation
    # Continuous integration
* The package licence - are you free to use the software?

## Understanding a packages DESCRIPTION file

A `DESCRIPTION` file is included with every R package. This forms the basis of the package's page on CRAN.  Many of the fields in the file will be self explanatory.   The _Depends_ and _Imports_ fields list packages and software that the package depends on (this will invariably include R iteself).  When we install a package thse dependencies will be installed automatically.  _Suggests:_ lists package that, although not required for the basic operation of the package, will enhance it.  These are not installed automatically.   If the package has a homepage, it will be listed under the _URL_ field. The _reverse depend s_, _reverse imports_ and _reverse suggests_ fields list packages that depend on the package.  


> ## Citing R and R packages
> If you use R in your work you should cite it, and the packages you use. The `citation()` command will return the appropriate citation for R itself.  `citation(packagename)` will provide the citation for `packagename`. 
>
{: .callout}


> ## Challenge
> Take a look at the four packages listed above.  Discuss with your neighbour which you think is most likely to be useful for our task (note that you do *not* need to know how to perform a meta analysis; the aim is to think about how well the packages meet the criteria above)
{: .challenge}

Let's assume we're going to use the `metafor` package to conduct our analysis. 

## Installing packages from CRAN

If a package is available on CRAN this is almost invariably the most straightforward way of installing it. The `metafor` package is available on CRAN, so we install it as follows:

```
install.packages("metafor")
```
{: .r}

We may be prompted to select a mirror to install the package from. You should ideally select a mirror that is close by.  The package will then be installed. By default, the package's dependencies will also be installed.

> ## Installing multiple packages
> If you want to install more than one package, supply the list of packages as a character vector:
> 
> ```r
> install.packages(c("package1", "package2", "package3"))
> ```
>
{: .callout}






