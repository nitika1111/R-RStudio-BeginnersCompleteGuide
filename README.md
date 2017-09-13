# A Beginner's Complete Guide for R and R Studio 
In this guide, installation of R, R Studio and R packages is covered. This guide also includes basic commands to begin working on R Studio. 

## Introduction to R
R is a language and environment for statistical computing and graphics. It is a GNU project which is similar to the S language and environment which was developed at Bell Laboratories (formerly AT&T, now Lucent Technologies) by John Chambers and colleagues. R can be considered as a different implementation of S. There are some important differences, but much code written for S runs unaltered under R.

R provides a wide variety of statistical (linear and nonlinear modelling, classical statistical tests, time-series analysis, classification, clustering, …) and graphical techniques, and is highly extensible. (r-project.org)

## Introduction to R Studio
RStudio is an integrated development environment (IDE) for R. It includes a console, syntax-highlighting editor that supports direct code execution, as well as tools for plotting, history, debugging and workspace management. (rstudio.com)

In order to work with R Studio, following steps should be completed in order:
1. Installation of R
2. Installation of R Studio
3. Installation of specific required packages according to developer's need

## Installation Steps
### 1. Installing R
Follow the steps below with respect to the operating system you are using

_For Windows_
1. Download the binary setup file for R from the following link: [R for Windows](https://cran.r-project.org/bin/windows/base/) 
2. Open the downloaded .exe file
3. Follow the instructions and install R


_For Mac_
1. Download the appropriate version of .pkg file form the following link: [R for Mac](https://cran.r-project.org/bin/macosx/) 
2. Open the downloaded .pkg file
3. Follow the instructions and install R

_For Linux_
1. For complete R System installation in Linux, follow the instructions on the following link: [R for Linux](https://cran.r-project.org/) 
2. For Ubuntu with Apt-get installed, execute sudo apt-get install r-base in terminal.

### 2. Installing R Studio
Follow these steps to install R Studio:
1. Go to this link: [RStudio Download](https://www.rstudio.com/products/rstudio/download/)
2. Click the Download RStudio Desktop button
3. Select the installation file for your system
4. Run the installation file and follow installation instructions

### 2. Installing R Packages(if required)
R packages can be installed using 2 ways. First one uses GUI on R Studio, and the other one uses Console on R Studio.
#### Method 1(Using GUI)
Follow the steps below if your work in R Studio requires installing specific packages that are not already available in R Base Package.
1. Run R studio
2. Click on the Packages tab in the bottom-right section and then click on install. 
3. A dialog box will appear. In the Install Packages dialog, write the package name you want to install under the Packages field and then click install. This will install the package you searched for or give you a list of matching package based on your package text.

#### Method 2(Using Console)
Let’s suppose you want to install the "class" package. Following command needs to be executed at R shell(make sure you have Root access on Linux)
1. Run R Studio
2. On the console, run following commands
   >install.packages("class") # Download and Install package from CRAN directly
   
   >library("class") # load the installed package so that you may use its functions
3. This will install the package "class"
 
This completes our installation part. If you want to learn how to perform a basic data analysis in R Studio, please follow the content given in [Basic Data Analysis in R](http://rpubs.com/Nitika/BasicDataAnalysisCommands)
