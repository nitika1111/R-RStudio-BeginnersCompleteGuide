# Basic commands for Data Analysis in R

Here we will design a basic data analysis program in R using R Studio by utilizing the features of R Studio to create some visual representation of data. We need to perform the following tasks in order

    1. Importing and understanding data in R 
    2. Pre-processing the data
    3. Basic data analysis using statistical averages
    4. Plotting data distribution

Let's understand the code step by step in order to achieve our goal!

#1. Importing and understanding Data


```r
acs <- read.csv(url("http://stat511.cwick.co.nz/homeworks/acs_or.csv")) #reads data from internet in local R variable "acs"
View(acs) #view whole dataset with all rows and all columns

head(acs,10) # view top 10 rows of dataset
```

```
##    household age_husband age_wife income_husband income_wife bedrooms
## 1         48          64       62          11000       29200        1
## 2        218          63       64         100000        3100        4
## 3        279          56       51          31000           0        2
## 4        612          71       68          51700        8800        3
## 5        947          37       33          16600       26000        3
## 6       1373          86       91          77500       30000        4
## 7       1733          67       67           8400        4800        4
## 8       1858          70       74          73670       11000        0
## 9       1947          33       31          55050         600        1
## 10      1962          41       47          42000       36000        3
##    electricity gas number_children internet     mode
## 1           90   3               0      Yes followup
## 2          230  30               0      Yes     mail
## 3          200  40               0       No followup
## 4          170   3               0      Yes internet
## 5          260   3               2      Yes internet
## 6           20  30               0      Yes internet
## 7           70 150               0      Yes internet
## 8          180  80               0      Yes     mail
## 9           20  30               0      Yes internet
## 10          80 200               2      Yes followup
##                            own     language decade_built
## 1  Owned with mortgage or loan English only         1940
## 2  Owned with mortgage or loan English only         1990
## 3                       Rented English only         1950
## 4         Owned free and clear English only         1950
## 5  Owned with mortgage or loan English only         1990
## 6         Owned free and clear English only         1980
## 7         Owned free and clear        Other         1980
## 8         Owned free and clear English only         2000
## 9                       Rented English only         1930
## 10 Owned with mortgage or loan English only         2000
```

```r
tail(acs) # view last rows of dataset(default is 6 rows)
```

```
##      household age_husband age_wife income_husband income_wife bedrooms
## 7806   1491153          41       37          42000       27000        2
## 7807   1491548          64       62          75700       13900        3
## 7808   1491592          71       63          21700       36000        3
## 7809   1492112          40       40          65000        4800        3
## 7810   1492158          64       65          90000       85030        4
## 7811   1492278          38       36         150000       28000        4
##      electricity gas number_children internet     mode
## 7806         200   3               0      Yes followup
## 7807          80   3               0      Yes internet
## 7808          90  30               0      Yes     mail
## 7809         180 120               0      Yes internet
## 7810          60   3               0      Yes followup
## 7811          70  60               2      Yes     mail
##                              own     language decade_built
## 7806 Owned with mortgage or loan English only         1950
## 7807        Owned free and clear English only         1930
## 7808 Owned with mortgage or loan English only         1990
## 7809 Owned with mortgage or loan English only         1940
## 7810        Owned free and clear English only         1940
## 7811                      Rented        Other         2000
```

```r
summary(acs$age_husband) #get the statistical summary of the dataset by just running on either a column or the complete dataset
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   17.00   42.00   55.00   54.32   66.00   95.00
```

```r
summary(acs[,5]) #summary of 5th column
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -6300    6225   18110   28990   39600  421000
```

```r
str(acs) # structure of dataset will column details
```

```
## 'data.frame':	7811 obs. of  14 variables:
##  $ household      : int  48 218 279 612 947 1373 1733 1858 1947 1962 ...
##  $ age_husband    : int  64 63 56 71 37 86 67 70 33 41 ...
##  $ age_wife       : int  62 64 51 68 33 91 67 74 31 47 ...
##  $ income_husband : int  11000 100000 31000 51700 16600 77500 8400 73670 55050 42000 ...
##  $ income_wife    : int  29200 3100 0 8800 26000 30000 4800 11000 600 36000 ...
##  $ bedrooms       : int  1 4 2 3 3 4 4 0 1 3 ...
##  $ electricity    : int  90 230 200 170 260 20 70 180 20 80 ...
##  $ gas            : int  3 30 40 3 3 30 150 80 30 200 ...
##  $ number_children: int  0 0 0 0 2 0 0 0 0 2 ...
##  $ internet       : Factor w/ 2 levels "No","Yes": 2 2 1 2 2 2 2 2 2 2 ...
##  $ mode           : Factor w/ 3 levels "followup","internet",..: 1 3 1 2 2 2 2 3 2 1 ...
##  $ own            : Factor w/ 4 levels "Occupied without payment of rent",..: 3 3 4 2 3 2 2 2 4 3 ...
##  $ language       : Factor w/ 3 levels "English only",..: 1 1 1 1 1 1 2 1 1 1 ...
##  $ decade_built   : int  1940 1990 1950 1950 1990 1980 1980 2000 1930 2000 ...
```

```r
table(acs$bedrooms) # give data frequency distribution
```

```
## 
##    0    1    2    3    4    5   10 
##   24  198 1475 4040 1652  350   72
```

```r
table(acs$bedrooms, acs$number_children) # gives cross tabulation
```

```
##     
##         0    1    2    3    4    5    6    7    8   10   12
##   0    15    1    5    3    0    0    0    0    0    0    0
##   1   175   16    6    1    0    0    0    0    0    0    0
##   2  1103  178  140   42   10    2    0    0    0    0    0
##   3  2750  504  526  202   39   13    6    0    0    0    0
##   4   892  241  322  130   39   20    5    1    1    1    0
##   5   174   37   66   48   14    5    2    2    1    0    1
##   10   42   11   10    2    5    1    1    0    0    0    0
```

```r
class(acs) # gives class/ data type of argument
```

```
## [1] "data.frame"
```

```r
class(acs$language) # gives class/ data type of particular column of dataset
```

```
## [1] "factor"
```

#2. Pre-processing the Data

```r
#Subsetting the data: Find rows from the dataset in which the age_husband is greater than age_wife
a <- subset(acs , age_husband > age_wife) # assign the subset of rows in variable "a"
a[1:5,c(2,3)] # display first 6 rows and column 2 and 3 from "a" to verify subset data
```

```
##   age_husband age_wife
## 1          64       62
## 3          56       51
## 4          71       68
## 5          37       33
## 9          33       31
```

```r
#Adding a new column to dataset
acs$newcol<- rnorm(nrow(acs)) # find number of rows using "rnum(acs)" and assign that many values to new column "newcol" in "acs"
names(acs) # view column names of "acs" dataset
```

```
##  [1] "household"       "age_husband"     "age_wife"       
##  [4] "income_husband"  "income_wife"     "bedrooms"       
##  [7] "electricity"     "gas"             "number_children"
## [10] "internet"        "mode"            "own"            
## [13] "language"        "decade_built"    "newcol"
```

```r
#removing a column from dataset
acs$newcol <- NULL 
names(acs)
```

```
##  [1] "household"       "age_husband"     "age_wife"       
##  [4] "income_husband"  "income_wife"     "bedrooms"       
##  [7] "electricity"     "gas"             "number_children"
## [10] "internet"        "mode"            "own"            
## [13] "language"        "decade_built"
```

#3. Getting Statistical Averages from data

```r
#For mean of any column :  
mean(acs$age_husband)
```

```
## [1] 54.31776
```

```r
#Median: 
median(acs$age_husband)
```

```
## [1] 55
```

```r
#Quantile: 
quantile(acs$age_wife)
```

```
##   0%  25%  50%  75% 100% 
##   19   40   53   63   95
```

```r
#Variance: 
var(acs$age_wife)
```

```
## [1] 220.527
```

```r
#Standard Deviation: 
sd(acs$age_wife)
```

```
## [1] 14.85015
```

#4. Plotting Data

```r
#create a scatter plot of a data set
plot(x = acs$age_husband , y = acs$age_wife, type = 'p', col="red")
```

![](BasicDataAnalysisInR_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

```r
#create a histogram
hist(acs$electricity, col="blue")
```

![](BasicDataAnalysisInR_files/figure-html/unnamed-chunk-4-2.png)<!-- -->

```r
#create a boxplot
boxplot(acs$age_husband~acs$internet, col="blue")
title(main="Husband Age Vs Internet Availability",xlab = "Internet Availability", ylab = "Age of Husband")
```

![](BasicDataAnalysisInR_files/figure-html/unnamed-chunk-4-3.png)<!-- -->

Congratulations for your first Data Analysis!! :)

Remember its just a beginning and there are lots of other data analysis functionalities that you need to try. As we progress, the complexity of data increases and therefore we require a lot of pre-processing on the dataset. 

Good luck!
