---
layout: post
title:  "EDA Python & R Package Development"
#date:   2022-03-01 10:00:40
blurb: "Spotify app post"
# og_image: /assets/img/content/post-example/Banner.jpg
---

<img src="{{"/assets/img/content/pypackage.png" | absolute_url }}" width="350" height="350" class="post-pic"/>
<br />
<br />

Packages are important tools that Data Scientists, Analysts and Developers use everyday in their work. Usually packages are the result of someone trying to make their own work easier, or reduce repetition of code, and then are made popular when others start using their packages. That is one of the beauties of this collaborative ecosystem, where others can reap the benefits of somebody else's hardwork in developing a tool specific to their former needs. I worked on a collaborative software project to develop a EDA-related package for Python and R ecosystems, and here I'll share my experiences on that.

The Python app is called [numeric_edahelper](https://pypi.org/project/numeric-edahelper/) and is published on PyPI, Python Package Index. It can be installed on your computer simply by calling `pip install numeric_edahelper`. You can also find the github repo [here](https://github.com/UBC-MDS/numeric_edahelper). We also created an [R version](https://github.com/UBC-MDS/nedahelpeR) of this package with similar functions. However, publishing on CRAN involved more layers of third-party reviews and we skipped that step. Nonetheless the R package can be downloaded easily by calling one line of code on R.

<br />


### Components of the package

1. [Package functions](#package-functions)
2. [Testing](#testing)
3. [Continuous Development and Integration](#3-combining-plots-with-widgets)
4. [Bootstrap Components and Layouts](#4-bootstrap-components-and-layouts)


#### 1. Package functions
The overall idea of the package is to provide nifty functions that can be called with just a couple of arguments like inputting a dataframe or a series/vector. And we would have four functions that belong to this one package, under the name `numeric_edahelper`. These four functions were suggested by me as I felt that some EDA processes could be better streamlined and made into just a simple function which can be easily called again and again, without repeating code or copying/pasting. These were: outlier detection, highly correlated variables, and missing values, description. The first two were more interesting, since they're more open-ended and are slightly more complicated to code.

The function I developed and built tests on was:
- Outlier detection: Takes in a dataframe with numeric values, as well as user-defined threshold for proportion of outliers. Let's say I have a dataframe with 10 numeric columns, and I want to flag those columns that contain outliers. I can call this function, which will return me the name of columns and their percentage of outliers. 

#### 2. Testing
After building the functions itself, I had to conduct different types of tests to ensure that our functions can handle various kinds of exceptions and errors in case the user inputs the wrong stuff and what kinds of messages to show the user when those things happen. Mainly, the focus was on unit testing and integration testing. So the use of some assert statements and error-handling statements was useful. The main module that helped me with these tests is `Pytest`, which will highlight areas which may have failed.

#### 3. Continuous Integration and Deployment
Once the main body of the package is done, it's time to think about CI/CD: Continuous Integration and Deployment. In software development and in this case package development, it's a super handy way to automate most of the running of the whole process to make sure things are smooth, and automatically detect where things are not working. This is especially useful when a product is in constant development and changes come in often. This saves alot of time manually running programs and discovering bugs. With CI/CD via Github actions, we just need to define the triggers to pull CI/CD and they'll provide a report of whether things went ok, or where it failed and we can zoom in on those to correct things.

#### 4. Publishing and documentation
Last but not least, we make this package available for public use. It's important at this stage to review the package documentation, since that's the main way we tell the public how to use this package. So it has to be easy to read, and well-documented with example code and demonstrations on function and package usage. [Readthedocs](https://numeric-edahelper.readthedocs.io/en/latest/) was a cool way to publish this manual, and these help documentation can also be called in the Python interface itself.

#### 5. Conclusions
Through this experience, I realized that creating packages may seem easy but there are a few layers to consider when it comes to making the package easily understood, usable and well-tested for errors or unexpected results. I do see the value of making packages for say a large data science team which often uses the same pipeline over and over, saving precious time. This is on the assumption that the packages are well-tested and peer-reviewed. Since people rarely peak into the actual function codes of packages, we are putting our trust that the developers of these packages know what they're doing and have ensured their reliability.
