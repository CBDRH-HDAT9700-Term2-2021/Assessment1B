HDAT9700: Assignment 1B - Chapters 4 & 5
================
Andrea Schaffer
16 Jun 2021

### Submission instructions

This is an R Markdown document—an example of *literate programming*, an
approach which allows users to interweave text, statistical output and
the code that produces that output.

To complete your assignment:

-   Edit this file directly, interweaving text and R code as appropriate
    to answer the questions below. Remember to `Knit` the file to make
    sure everything is running smoothly. Detailed information on R
    Markdown is available
    [here](https://rmarkdown.rstudio.com/lesson-1.html), and there is a
    useful cheatsheet
    [here](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf).

-   Use git to `commit` changes you make in this repo locally.

-   `Push` the repo, together with this edited file and the
    corresponding `.md` file to GitHub Classroom.  
    You can `commit` and `push` as often as necessary—your assessment
    will be graded on the most recent version of your repo at the
    assessment due date.

Good luck!

------------------------------------------------------------------------

### Overview

For this assessment you will use a subset of data from a study of the
impact of a new law on the homicide rate in the state of Florida, USA
(data are from:
[10.1093/ije/dyaa152](https://academic.oup.com/ije/article-abstract/49/6/2010/5917161)).

On 1 October 2005, Florida implemented the “Stand-your-ground law,”
which extends the use of lethal force as a legitimate defense where an
individual perceives a threat of harm, such as for the protection of
private property. For more information see:
<https://en.wikipedia.org/wiki/Stand-your-ground_law>. Florida was one
of the first US states to implement this law.

In this assessment you will evaluate the impact of this law on deaths by
homicide. The main outcome variable is the homicide rate per 100,000
population in Florida from January 2000 to December 2007.

The *flhom.csv* file contains the following variables:

-   **date** - Month and year
-   **hom\_rate** - Homicide rate per 100,000

You will need to have the following packages installed: `readr` (to read
in the csv file), `astsa`, `lmtest`, `forecast`, and `zoo`.

The data are contained in your assignment repo and can be read as
follows:

``` r
flhom <- read.csv("flhom.csv", header=TRUE)
```

------------------------------------------------------------------------

### Assessment questions

1.  Create a plot of the homicide rate over time, as if you were
    preparing it for inclusion in a report or publication. (20%)

2.  Describe the homicide rate time series in terms of the trend,
    seasonality, and outliers. Provide appropriate plots and summary
    statistics to support your statements. (20%)

3.  Create the necessary vectors and fit the segmented regression models
    listed below. Here, `time` is the time since start of the study,
    `syg` is an indicator for the “Stand-your-ground” law (before=0,
    after=1), `time.after` is the time since the law was implemented,
    `month` is a monthly dummy variable, and `syg.lag1` and
    `time.after.lag1` are `syg` and `time.after` delayed/lagged by one
    month. Comment on the fit/appropriateness of each model, and state
    which model you believe best describes the association between the
    intervention, and the homicide rate over time. Provide evidence to
    justify your answer. (25%)

    -   **Model 1** - hom\_rate \~ time + syg + time.after + month
    -   **Model 2** - hom\_rate \~ time + syg + time.after
    -   **Model 3** - hom\_rate \~ time + syg.lag1 + time.after.lag1 +
        month
    -   **Model 4** - hom\_rate \~ time + syg.lag1 + time.after.lag1

4.  Using the “best” model from question (3), summarise your findings
    and write a conclusion describing the impact of the law on the
    homicide rate in Florida. Provide effect estimates and relevant
    statistics to support your answer. (20%)

5.  Including a negative control series is one way of improving causal
    inference from interrupted time series analysis. Give one example of
    a negative control series for this intervention (be specific), and
    justify your selection. Explain in your own words how a negative
    control series helps with inference. (15%)

------------------------------------------------------------------------

### Student declaration

***Instructions: Indicate that you understand and agree with the
following three statements by typing an x in the square brackets below,
e.g. \[x\].***

I declare that this assessment item is my own work, except where
acknowledged, and has not been submitted for academic credit elsewhere
or previously, or produced independently of this course (e.g. for a
third party such as your place of employment) and acknowledge that the
assessor of this item may, for the purpose of assessing this item: (i)
Reproduce this assessment item and provide a copy to another member of
the University; and/or (ii) Communicate a copy of this assessment item
to a plagiarism checking service (which may then retain a copy of the
assessment item on its database for the purpose of future plagiarism
checking).

-   [ ] I understand and agree

I certify that I have read and understood the University Rules in
respect of Student Academic Misconduct.

-   [ ] I understand and agree

I have a backup copy of the assessment.

-   [ ] I understand and agree
