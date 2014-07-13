# Reproducible Research: Peer Assessment 1

Per the assignment description:  
"This assignment makes use of data from a personal activity monitoring device. This device collects data at 5 minute intervals through out the day. The data consists of two months of data from an anonymous individual collected during the months of October and November, 2012 and include the number of steps taken in 5 minute intervals each day."

## Loading and preprocessing the data

### Retrieving the data


```r
setwd('~/Reproducible/Project01')
download.file(
  'http://d396qusza40orc.cloudfront.net/repdata/data/activity.zip',
  'activity.zip')
unzip('activity.zip', 'activity.csv')
activity <- read.csv('activity.csv')
```


## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
