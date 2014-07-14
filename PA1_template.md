# Reproducible Research: Peer Assessment 1

Per the assignment description:  
"This assignment makes use of data from a personal activity monitoring device. This device collects data at 5 minute intervals through out the day. The data consists of two months of data from an anonymous individual collected during the months of October and November, 2012 and include the number of steps taken in 5 minute intervals each day."

## Loading and preprocessing the data

### Retrieving the data


```r
setwd('~/Reproducible/RepData_PeerAssessment1')
download.file(
  'http://d396qusza40orc.cloudfront.net/repdata/data/activity.zip',
  'activity.zip')
```

```
## Warning: unable to resolve 'd396qusza40orc.cloudfront.net'
```

```
## Error: cannot open URL
## 'http://d396qusza40orc.cloudfront.net/repdata/data/activity.zip'
```

```r
unzip('activity.zip', 'activity.csv')
```

```
## Warning: error 1 in extracting from zip file
```

```r
activity <- read.csv('activity.csv')
```


## What is mean total number of steps taken per day?

Ignoring days with missing values for the number of steps, we can determine the distribution of the total number of steps in a given day, as well as calculate mean and median values.


```r
# Sum the 5 minute intervals for each day
dailyTotal<- rowsum(activity$steps, activity$date)

# Plot the distribution
hist(dailyTotal, 10, main = 'Total Number of Steps Taken Each Day')
```

![plot of chunk MeanSteps](figure/MeanSteps.png) 

```r
# Calculate some statistics
meanDailyTotal <- mean(dailyTotal[!is.na(dailyTotal)])
medianDailyTotal <- median(dailyTotal[!is.na(dailyTotal)])
print(c('The Mean Daily Total is:  ', meanDailyTotal))
```

```
## [1] "The Mean Daily Total is:  " "10766.1886792453"
```

```r
print(c('The Median Daily Total is:  ', medianDailyTotal))
```

```
## [1] "The Median Daily Total is:  " "10765"
```

The mean total number of steps taken per day is 10766.  
The median total number of steps taken per day is 10765.

## What is the average daily activity pattern?


```r
meanInterval <- aggregate(steps ~ interval, 
                          data= activity[!is.na(activity$steps),], 
                          mean)
plot(meanInterval, 
     type='l', 
     main='Average Daily Activity Pattern', 
     sub = 'Average Number of Steps per Day by Interval')
```

![plot of chunk DailyPattern](figure/DailyPattern.png) 

```r
maxInterval <- meanInterval[max(meanInterval$steps),]$interval
print(c('The Interval with the maximum daily average is:  ', maxInterval))
```

```
## [1] "The Interval with the maximum daily average is:  "
## [2] "1705"
```

The Interval with the maximum daily average of 206.1698 is 1705.

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
