Capstone Project_Bellabeat
================
Uriel Ulloa
11/4/2021

<style>
body {
text-align: justify}
</style>

## Presentation

The following study is made for academic purposes. This is a Capstone
Project for the Google Data Analysis Professional Certificate, in which
the six steps of the Data Analysis Process are used.

**Title:** Google Data Analysis Capstone Project: Bellabeat Case Study  
**Author:** Uriel Ulloa  
**Date:** November 4th 2021

# Bellabeat: How Can A Wellness Technology Company Play It Smart?

### *PHASE 1: ASK*

------------------------------------------------------------------------

#### **1.1.General Background**

Founded in 2013, by Urška Sršen and Sando Mur, Bellabeat is a high-tech
company which aim to empower women with knowledge about their own health
and habits offering them health focused smart products. For more
information, please click the following link:
<https://bellabeat.com/about/>  
From that point forward the company has grown rapidly and quickly
positioned itself opening offices worldwide, having their multiple
products in the catalogue of many online retailers and in their own
e-commerce platform (for more information click the link to their
website).  
Chief Creative Officer, Urška Sršen would like to leverage all the
consumer data available and gain insight on how people are using their
smart devices (FitBit Fitness Tracker Data) in order to generate
data-driven recommendations for future marketing strategies

------------------------------------------------------------------------

#### **1.2.Project Objectives**

1.  Identify the trends in smart devices usage.
2.  Generate insights about the applicability to Bellabeat customers, in
    particular FitBit Fitness device.
3.  Deliver recommendations to the marketing team on how could the
    findings could improve the current campaigns.

------------------------------------------------------------------------

#### **1.3.Deliverables**

1.  Business Task summary
2.  Description of all the data used
3.  Data cleaning log
4.  Analysis’s summary
5.  Supporting and compelling visualizations
6.  Present key findings
7.  Recommendations based on findings.

------------------------------------------------------------------------

#### **1.4.Business Task**

Analyze smart device usage data in to gain insight about consumer
behavior trends and then apply the findings to Bella Beat FitBit Fitness
Tracker Data in order to make data-driven decisions in marketing
strategies.

------------------------------------------------------------------------

#### **1.5.Key Stakeholder**

• **Urška Sršen:** Bellabeat’s cofounder and Chief Creative Officer. She
is the one who proposed the project and the most interested in the
results.  
• **Sando Mur:** Mathematician and Bellabeat’s cofounder; key member of
the Bellabeat executive team.  
• **BellaBeat Marketing Analytics Team:** Team of data analyst working
on collecting, analyzing, reporting and conducting the project.  
• **Bellabeat Marketing Strategies Team:** Most likely the audience
wwich is going to receive the resultsm findings and recommendations of
the project in order to apply it to new marketing campaigns.

### *PHASE 2: PREPARE *

------------------------------------------------------------------------

#### **2.1.Data’s information**

• *FitBit Fitness Tracker Data* is an open-source data collection
uploaded by *Möbius*, which was last updated on December 2020. Check out
the [FitBit Fitness Tracker
Dataset](https://www.kaggle.com/arashnic/fitbit) on kaggle’s community
to learn more.  
• The data set is stored in 18 CSV files that have information about
*Daily Activities*, *Heart Rates*, *Burned Calories*, and *Sleep* sleep
patterns.  
• Datasets are generatedd in 2016, by respondents to a distributed
survey via Amazon Mechanical Turk between March 12th to May 12th.  
• Thirty (30) eligible Fitbit users consented to the submission of
personal tracker data.

------------------------------------------------------------------------

#### **2.2.Limitations of the data**

• As stated before, the data was generated in 2016, it’s been five year
since then, when people may have changed their behavior when it comes to
health care.  
• There is no possible way to guarantee the integrity and accuracy of
the data collected, hence it might be safe to assume data could be
biased in some way or another.  
• The sample size of 30 users is too low to apply the results to a
population. Even though multiple (thousands) of records exists, it’s
important to keep in mind, that came from just 30 individuals.

------------------------------------------------------------------------

#### **2.3.Does the data ROCC?**

| ROOCC         | MEASURE | COMMENT                                                                                                                          |
|:--------------|:--------|:---------------------------------------------------------------------------------------------------------------------------------|
| Reliable      | LOW     | Thirty individuals doesn’t make up for a reliable result                                                                         |
| Original      | LOW     | Data collected is from an external source, Amazon Mechanical Turk, a-third party provider                                        |
| Comprehensive | LOW     | Metadata about the tables provided is not stated                                                                                 |
| Current       | LOW     | Data is 5 years old, which might differ from current information                                                                 |
| Cited         | MED     | Amazon Mechanicl Turk collected the information themselves, information about their sources, parameters and method is not stated |

------------------------------------------------------------------------

#### **2.4.Data selected for analysis**

The following files were selected based on a most relevant criteria for
the analysis purposes:

-   Fitbase Data
    -   `dailyActivity_merged.csv`
    -   `heartrate_seconds_merged.csv`
    -   `minuteMETsNarrow_merfed.csv`
    -   `sleepDay-merged.csv`
    -   `weightLogInfo_meged.csv`

------------------------------------------------------------------------

### *PHASE 2: PROCESS *

The tool applied for data and statistical analysis is R programming
language, and R studio as the Integrated Development Environment (IDE).
Later on R Markdown is used for reporting.

------------------------------------------------------------------------

#### **3.1. Setting up the environment**

-   The following packaged are used for:
    -   `tidyverse`: Designed for data import, tidying, manipulation,
        visualization, and programming.
    -   `lubridate`: Dealing with Dates
    -   `here`: Importing files a little easier
    -   `conflicted`: Handles the ambiguity with functions overlapping
    -   `ggplot2` and `reshape2`: Create visualizations

<!-- -->

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.5     v dplyr   1.0.7
    ## v tidyr   1.1.4     v stringr 1.4.0
    ## v readr   2.0.2     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

    ## here() starts at C:/Users/pc/Documents/Google Analytics/Case Study

    ## 
    ## Attaching package: 'lubridate'

    ## The following objects are masked from 'package:base':
    ## 
    ##     date, intersect, setdiff, union

    ## ------------------------------------------------------------------------------

    ## You have loaded plyr after dplyr - this is likely to cause problems.
    ## If you need functions from both plyr and dplyr, please load plyr first, then dplyr:
    ## library(plyr); library(dplyr)

    ## ------------------------------------------------------------------------------

    ## 
    ## Attaching package: 'plyr'

    ## The following object is masked from 'package:here':
    ## 
    ##     here

    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     arrange, count, desc, failwith, id, mutate, rename, summarise,
    ##     summarize

    ## The following object is masked from 'package:purrr':
    ## 
    ##     compact

Following up is important to set the priority of functions right off the
bat with `conflicted`, in order to avoid any code error.

    ## [conflicted] Will prefer plyr::count over any other package

    ## [conflicted] Will prefer here::here over any other package

    ## [conflicted] Will prefer dplyr::summarize over any other package

    ## [conflicted] Will prefer dplyr::mutate over any other package

    ## [conflicted] Will prefer dplyr::filter over any other package

    ## [conflicted] Will prefer dplyr::rename over any other package

Now having the land prepared, data cleaning is on the way.

------------------------------------------------------------------------

#### **3.2. Importing the data frames**

Using the following chunk’s code, all the data necessary for the
analysis is imported.

#### **3.3. Understand the data**

Is important to preview the data we are dealing with as we get more
comfortable and familiarize with it, in order to draw early conclusions.
For this the `tible` function is used.

    ## # A tibble: 940 x 15
    ##            Id ActivityDate TotalSteps TotalDistance TrackerDistance LoggedActivitie~
    ##         <dbl> <chr>             <int>         <dbl>           <dbl>            <dbl>
    ##  1 1503960366 4/12/2016         13162          8.5             8.5                 0
    ##  2 1503960366 4/13/2016         10735          6.97            6.97                0
    ##  3 1503960366 4/14/2016         10460          6.74            6.74                0
    ##  4 1503960366 4/15/2016          9762          6.28            6.28                0
    ##  5 1503960366 4/16/2016         12669          8.16            8.16                0
    ##  6 1503960366 4/17/2016          9705          6.48            6.48                0
    ##  7 1503960366 4/18/2016         13019          8.59            8.59                0
    ##  8 1503960366 4/19/2016         15506          9.88            9.88                0
    ##  9 1503960366 4/20/2016         10544          6.68            6.68                0
    ## 10 1503960366 4/21/2016          9819          6.34            6.34                0
    ## # ... with 930 more rows, and 9 more variables: VeryActiveDistance <dbl>,
    ## #   ModeratelyActiveDistance <dbl>, LightActiveDistance <dbl>,
    ## #   SedentaryActiveDistance <dbl>, VeryActiveMinutes <int>,
    ## #   FairlyActiveMinutes <int>, LightlyActiveMinutes <int>,
    ## #   SedentaryMinutes <int>, Calories <int>

    ## # A tibble: 413 x 5
    ##            Id SleepDay              TotalSleepRecor~ TotalMinutesAsl~ TotalTimeInBed
    ##         <dbl> <chr>                            <int>            <int>          <int>
    ##  1 1503960366 4/12/2016 12:00:00 AM                1              327            346
    ##  2 1503960366 4/13/2016 12:00:00 AM                2              384            407
    ##  3 1503960366 4/15/2016 12:00:00 AM                1              412            442
    ##  4 1503960366 4/16/2016 12:00:00 AM                2              340            367
    ##  5 1503960366 4/17/2016 12:00:00 AM                1              700            712
    ##  6 1503960366 4/19/2016 12:00:00 AM                1              304            320
    ##  7 1503960366 4/20/2016 12:00:00 AM                1              360            377
    ##  8 1503960366 4/21/2016 12:00:00 AM                1              325            364
    ##  9 1503960366 4/23/2016 12:00:00 AM                1              361            384
    ## 10 1503960366 4/24/2016 12:00:00 AM                1              430            449
    ## # ... with 403 more rows

    ## # A tibble: 2,483,658 x 3
    ##            Id Time                 Value
    ##         <dbl> <chr>                <int>
    ##  1 2022484408 4/12/2016 7:21:00 AM    97
    ##  2 2022484408 4/12/2016 7:21:05 AM   102
    ##  3 2022484408 4/12/2016 7:21:10 AM   105
    ##  4 2022484408 4/12/2016 7:21:20 AM   103
    ##  5 2022484408 4/12/2016 7:21:25 AM   101
    ##  6 2022484408 4/12/2016 7:22:05 AM    95
    ##  7 2022484408 4/12/2016 7:22:10 AM    91
    ##  8 2022484408 4/12/2016 7:22:15 AM    93
    ##  9 2022484408 4/12/2016 7:22:20 AM    94
    ## 10 2022484408 4/12/2016 7:22:25 AM    93
    ## # ... with 2,483,648 more rows

    ## # A tibble: 67 x 8
    ##            Id Date     WeightKg WeightPounds   Fat   BMI IsManualReport    LogId
    ##         <dbl> <chr>       <dbl>        <dbl> <int> <dbl> <chr>             <dbl>
    ##  1 1503960366 5/2/201~     52.6         116.    22  22.6 True            1.46e12
    ##  2 1503960366 5/3/201~     52.6         116.    NA  22.6 True            1.46e12
    ##  3 1927972279 4/13/20~    134.          294.    NA  47.5 False           1.46e12
    ##  4 2873212765 4/21/20~     56.7         125.    NA  21.5 True            1.46e12
    ##  5 2873212765 5/12/20~     57.3         126.    NA  21.7 True            1.46e12
    ##  6 4319703577 4/17/20~     72.4         160.    25  27.5 True            1.46e12
    ##  7 4319703577 5/4/201~     72.3         159.    NA  27.4 True            1.46e12
    ##  8 4558609924 4/18/20~     69.7         154.    NA  27.2 True            1.46e12
    ##  9 4558609924 4/25/20~     70.3         155.    NA  27.5 True            1.46e12
    ## 10 4558609924 5/1/201~     69.9         154.    NA  27.3 True            1.46e12
    ## # ... with 57 more rows

    ## # A tibble: 1,325,580 x 3
    ##            Id ActivityMinute         METs
    ##         <dbl> <chr>                 <int>
    ##  1 1503960366 4/12/2016 12:00:00 AM    10
    ##  2 1503960366 4/12/2016 12:01:00 AM    10
    ##  3 1503960366 4/12/2016 12:02:00 AM    10
    ##  4 1503960366 4/12/2016 12:03:00 AM    10
    ##  5 1503960366 4/12/2016 12:04:00 AM    10
    ##  6 1503960366 4/12/2016 12:05:00 AM    12
    ##  7 1503960366 4/12/2016 12:06:00 AM    12
    ##  8 1503960366 4/12/2016 12:07:00 AM    12
    ##  9 1503960366 4/12/2016 12:08:00 AM    12
    ## 10 1503960366 4/12/2016 12:09:00 AM    12
    ## # ... with 1,325,570 more rows

    ## # A tibble: 188,521 x 4
    ##            Id date                 value       logId
    ##         <dbl> <chr>                <int>       <dbl>
    ##  1 1503960366 4/12/2016 2:47:30 AM     3 11380564589
    ##  2 1503960366 4/12/2016 2:48:30 AM     2 11380564589
    ##  3 1503960366 4/12/2016 2:49:30 AM     1 11380564589
    ##  4 1503960366 4/12/2016 2:50:30 AM     1 11380564589
    ##  5 1503960366 4/12/2016 2:51:30 AM     1 11380564589
    ##  6 1503960366 4/12/2016 2:52:30 AM     1 11380564589
    ##  7 1503960366 4/12/2016 2:53:30 AM     1 11380564589
    ##  8 1503960366 4/12/2016 2:54:30 AM     2 11380564589
    ##  9 1503960366 4/12/2016 2:55:30 AM     2 11380564589
    ## 10 1503960366 4/12/2016 2:56:30 AM     2 11380564589
    ## # ... with 188,511 more rows

As a summary:

| Data Frame     | #Observations | #Fields |
|:---------------|---------------|:--------|
| Daily Activity | 940           | 15      |
| Sleep Day      | 413           | 5       |
| Heart Rate     | 2,483,658     | 3       |
| Weight         | 67            | 8       |
| METs           | 1,325,580     | 3       |
| Sleep Mins     | 188,521       | 4       |

**Findings:** It’s important to notice that there are significant gaps
between the data frames, this is because the entry logs or observations
are measured in different units, for example the *Daily Activity* is in
days, *Sleep Mins* in minutes, and *Heart Rate* in seconds, hence there
is inconsistency in the data.

Note that the data type in all fields is all right, except for `Date`.
This particular filed is formatted as a `chr` which is characters, hence
it has to be converted to `datetime64` format for fuurther analysis.

------------------------------------------------------------------------

#### **3.4. Checking for any null values**

This code’s chunk checks for any nulls values in all data frames.

    ## Rows: 1
    ## Columns: 16
    ## $ x.Id                       <dbl> 0
    ## $ x.ActivityDate             <dbl> 0
    ## $ x.TotalSteps               <dbl> 0
    ## $ x.TotalDistance            <dbl> 0
    ## $ x.TrackerDistance          <dbl> 0
    ## $ x.LoggedActivitiesDistance <dbl> 0
    ## $ x.VeryActiveDistance       <dbl> 0
    ## $ x.ModeratelyActiveDistance <dbl> 0
    ## $ x.LightActiveDistance      <dbl> 0
    ## $ x.SedentaryActiveDistance  <dbl> 0
    ## $ x.VeryActiveMinutes        <dbl> 0
    ## $ x.FairlyActiveMinutes      <dbl> 0
    ## $ x.LightlyActiveMinutes     <dbl> 0
    ## $ x.SedentaryMinutes         <dbl> 0
    ## $ x.Calories                 <dbl> 0
    ## $ freq                       <int> 940

    ## Rows: 1
    ## Columns: 6
    ## $ x.Id                 <dbl> 0
    ## $ x.SleepDay           <dbl> 0
    ## $ x.TotalSleepRecords  <dbl> 0
    ## $ x.TotalMinutesAsleep <dbl> 0
    ## $ x.TotalTimeInBed     <dbl> 0
    ## $ freq                 <int> 413

    ## Rows: 1
    ## Columns: 4
    ## $ x.Id    <dbl> 0
    ## $ x.Time  <dbl> 0
    ## $ x.Value <dbl> 0
    ## $ freq    <int> 2483658

    ## Rows: 2
    ## Columns: 9
    ## $ x.Id             <dbl> 0, 0
    ## $ x.Date           <dbl> 0, 0
    ## $ x.WeightKg       <dbl> 0, 0
    ## $ x.WeightPounds   <dbl> 0, 0
    ## $ x.Fat            <dbl> 0, 1
    ## $ x.BMI            <dbl> 0, 0
    ## $ x.IsManualReport <dbl> 0, 0
    ## $ x.LogId          <dbl> 0, 0
    ## $ freq             <int> 2, 65

    ## Rows: 1
    ## Columns: 4
    ## $ x.Id             <dbl> 0
    ## $ x.ActivityMinute <dbl> 0
    ## $ x.METs           <dbl> 0
    ## $ freq             <int> 1325580

    ## Rows: 1
    ## Columns: 5
    ## $ x.Id    <dbl> 0
    ## $ x.date  <dbl> 0
    ## $ x.value <dbl> 0
    ## $ x.logId <dbl> 0
    ## $ freq    <int> 188521

**Findings:**Results show that there are no missing or null values.

------------------------------------------------------------------------

#### **3.5. Identifying unique ID’s**

Source information stated that the information is collected from thirty
(30) individuals records on their activities, let’s find out is that is
a consistent face value.

    ## # A tibble: 6 x 3
    ##   data_frames    nuniqueId   nrows
    ##   <chr>              <int>   <int>
    ## 1 Daily Activity        33     940
    ## 2 Sleep Day             24     413
    ## 3 Heart Rate            14 2483658
    ## 4 Weight                 8      67
    ## 5 METs                  33 1325580
    ## 6 Sleep Mins            24  188521

**Findings:**All data frames share the same inconsistency regarding
their number of unique ID’s, given none has the 30 individuals sample
size. Note that the `Weight` dataset only has 8 individual’s records and
64 observations, hence it’s not useful for further analysis.

------------------------------------------------------------------------

#### **3.6. Manipulation and cleaning of the data**

Every data frame requires converting the `Date` field which is in `chr`,
type into `datetime64` type, and then to `yyyy - mm- dd` format, to give
consistency throught the whole dataset.

------------------------------------------------------------------------

##### **3.6.1. Daily Activity DataFrame**

    ## # A tibble: 940 x 18
    ##            Id fixed_date week_day  TotalSteps TotalDistance TrackerDistance
    ##         <dbl> <date>     <chr>          <int>         <dbl>           <dbl>
    ##  1 1503960366 2016-04-12 Tuesday        13162          8.5             8.5 
    ##  2 1503960366 2016-04-13 Wednesday      10735          6.97            6.97
    ##  3 1503960366 2016-04-14 Thursday       10460          6.74            6.74
    ##  4 1503960366 2016-04-15 Friday          9762          6.28            6.28
    ##  5 1503960366 2016-04-16 Saturday       12669          8.16            8.16
    ##  6 1503960366 2016-04-17 Sunday          9705          6.48            6.48
    ##  7 1503960366 2016-04-18 Monday         13019          8.59            8.59
    ##  8 1503960366 2016-04-19 Tuesday        15506          9.88            9.88
    ##  9 1503960366 2016-04-20 Wednesday      10544          6.68            6.68
    ## 10 1503960366 2016-04-21 Thursday        9819          6.34            6.34
    ## # ... with 930 more rows, and 12 more variables:
    ## #   LoggedActivitiesDistance <dbl>, VeryActiveDistance <dbl>,
    ## #   ModeratelyActiveDistance <dbl>, LightActiveDistance <dbl>,
    ## #   SedentaryActiveDistance <dbl>, VeryActiveMinutes <int>,
    ## #   FairlyActiveMinutes <int>, LightlyActiveMinutes <int>,
    ## #   SedentaryMinutes <int>, Calories <int>, time_logged_mins <int>,
    ## #   time_logged_hours <dbl>

------------------------------------------------------------------------

##### **3.6.2. Sleep Day DataFrame**

``` r
#Transform the date string to a properly mdy format
sleep_clean <- sleep_day_df %>%
  mutate(date_time = mdy_hms(SleepDay))

sleep_clean$date_time <- ymd(sleep_clean$date_time)

#Calculate the time a person spent in bed while being awake
sleep_clean <- sleep_clean %>% 
  mutate(totaltime_awake = TotalTimeInBed - TotalMinutesAsleep)

#Identify the week days in dates for further analysis in patterns 
sleep_clean$week_day <- weekdays(sleep_clean$date_time)

#Drop unnecessary data and reorganize the dataframe
drops <- c("SleepDay")
sleep_clean <- sleep_clean[ , !(names(sleep_clean) %in% drops)]
sleep_clean <- sleep_clean[,c("Id","date_time","week_day","TotalMinutesAsleep",
                              "TotalTimeInBed", "totaltime_awake",
                              "TotalSleepRecords")]
head(sleep_clean)
```

    ##           Id  date_time  week_day TotalMinutesAsleep TotalTimeInBed
    ## 1 1503960366 2016-04-12   Tuesday                327            346
    ## 2 1503960366 2016-04-13 Wednesday                384            407
    ## 3 1503960366 2016-04-15    Friday                412            442
    ## 4 1503960366 2016-04-16  Saturday                340            367
    ## 5 1503960366 2016-04-17    Sunday                700            712
    ## 6 1503960366 2016-04-19   Tuesday                304            320
    ##   totaltime_awake TotalSleepRecords
    ## 1              19                 1
    ## 2              23                 2
    ## 3              30                 1
    ## 4              27                 2
    ## 5              12                 1
    ## 6              16                 1

------------------------------------------------------------------------

##### **3.6.3. Heart Rate DataFrame**

``` r
#Transform the date string to a properly mdy-hms format
heartrate_clean <- heartrate_df %>%
  mutate(date_time = mdy_hms(Time))

#Separate the date and time columns to individual ones
heartrate_clean <- heartrate_clean %>% 
  separate(date_time, into = c("date", "time"),sep = " ")

heartrate_clean$date <- ymd(heartrate_clean$date)
heartrate_clean$time <- hms(heartrate_clean$time)

#Identify the week days in dates for further analysis in patterns 
heartrate_clean$week_day <- weekdays(heartrate_clean$date)

#Drop unnecessary data and reorganizae the dataframe
drops <- c("Time")
heartrate_clean <- heartrate_clean[ , !(names(heartrate_clean) %in% drops)]
heartrate_clean <- heartrate_clean[,c("Id","date","time","week_day","Value")]
head(heartrate_clean) 
```

    ##           Id       date       time week_day Value
    ## 1 2022484408 2016-04-12  7H 21M 0S  Tuesday    97
    ## 2 2022484408 2016-04-12  7H 21M 5S  Tuesday   102
    ## 3 2022484408 2016-04-12 7H 21M 10S  Tuesday   105
    ## 4 2022484408 2016-04-12 7H 21M 20S  Tuesday   103
    ## 5 2022484408 2016-04-12 7H 21M 25S  Tuesday   101
    ## 6 2022484408 2016-04-12  7H 22M 5S  Tuesday    95

------------------------------------------------------------------------

##### **3.6.4. Weight DataFrame**

``` r
#Transform the date string to a properly mdy-hms format
weight_clean <- weight_df %>%
  mutate(date_time = mdy_hms(Date))

#Separate the date and time columns to individual ones
weight_clean <- weight_clean %>% 
  separate(date_time, into = c("date", "time"),sep = " ")

weight_clean$date <- ymd(weight_clean$date)
weight_clean$time <- hms(weight_clean$time)

#Identify the week days in dates for further analysis in patterns 
weight_clean$week_day <- weekdays(weight_clean$date)

#Drop unnecessary data and reorganize the dataframe
drops <- c("Date")
weight_clean <- weight_clean[ , !(names(weight_clean) %in% drops)]
weight_clean <- weight_clean[,c("Id","date","time","week_day",
                                "WeightKg","WeightPounds",
                                "Fat","BMI","IsManualReport")]
head(weight_clean)     
```

    ##           Id       date        time  week_day WeightKg WeightPounds Fat   BMI
    ## 1 1503960366 2016-05-02 23H 59M 59S    Monday     52.6     115.9631  22 22.65
    ## 2 1503960366 2016-05-03 23H 59M 59S   Tuesday     52.6     115.9631  NA 22.65
    ## 3 1927972279 2016-04-13   1H 8M 52S Wednesday    133.5     294.3171  NA 47.54
    ## 4 2873212765 2016-04-21 23H 59M 59S  Thursday     56.7     125.0021  NA 21.45
    ## 5 2873212765 2016-05-12 23H 59M 59S  Thursday     57.3     126.3249  NA 21.69
    ## 6 4319703577 2016-04-17 23H 59M 59S    Sunday     72.4     159.6147  25 27.45
    ##   IsManualReport
    ## 1           True
    ## 2           True
    ## 3          False
    ## 4           True
    ## 5           True
    ## 6           True

------------------------------------------------------------------------

##### **3.6.5. METs DataFrame**

``` r
#Transform the date string to a properly mdy-hms format
mets_clean <- mets_df %>%
  mutate(date_time = mdy_hms(ActivityMinute))

#Separate the date and time columns to individual ones
mets_clean <- mets_clean %>% 
  separate(date_time, into = c("date", "time"),sep = " ")
mets_clean$date <- ymd(mets_clean$date)
mets_clean$time <- hms(mets_clean$time)

#Identify the week days in dates for further analysis in patterns 
mets_clean$week_day <- weekdays(mets_clean$date)

#Drop unnecessary data and reorganize the dataframe
drops <- c("ActivityMinute")
mets_clean <- mets_clean[ , !(names(mets_clean) %in% drops)]
mets_clean <- mets_clean[,c("Id","date","time","week_day","METs")]
head(mets_clean)  
```

    ##           Id       date  time week_day METs
    ## 1 1503960366 2016-04-12    0S  Tuesday   10
    ## 2 1503960366 2016-04-12 1M 0S  Tuesday   10
    ## 3 1503960366 2016-04-12 2M 0S  Tuesday   10
    ## 4 1503960366 2016-04-12 3M 0S  Tuesday   10
    ## 5 1503960366 2016-04-12 4M 0S  Tuesday   10
    ## 6 1503960366 2016-04-12 5M 0S  Tuesday   12

------------------------------------------------------------------------

##### **3.6.6. Sleep Cycle DataFrame**

This data frame contains information about sleep patterns of the
individuals, defined in values *1,2 and 3*, any entry for each value
represents a minute of sleep. Due to the ambiguity of the data is
difficult to interpret what this pattern stands for, but it might follow
the logic of the **SLEEP CLYCLES**

Michael Grandner, MD, director of the Sleep and Health Research Program
at the University of Arizona in Tucson describes each cycle as:

> (1)Light Sleep: “Shallow and not restful. It’s when your body
> processes memories and emotions and your metabolism regulates itself”

> (2)Deep Sleep: “The thinking parts of the brain are largely offline.
> Your muscles are very relaxed. You’re not dreaming at all during this
> time. Your body is doing a lot of rebuilding and repairing”

> (3)REM Sleep: REM is when most dreaming happens and your eyes move
> rapidly in different directions (hence the name). Heart rate increases
> and your breathing becomes more irregular.

Check out this amazing
[blog](https://blog.fitbit.com/sleep-stages-explained/) by Danielle
Kosecki (source) for mor info.

``` r
#Verify if values correspond to sleeps cycles 
count_cycle <- count(min_sleep_df$value)
sleep_cycle <- data.frame(count_cycle)
conflict_prefer("mutate", "dplyr")
```

    ## [conflicted] Removing existing preference

    ## [conflicted] Will prefer dplyr::mutate over any other package

``` r
sleep_cycle <- sleep_cycle %>% 
  mutate(percentage = (sleep_cycle/nrow(min_sleep_df))*100)
tibble(sleep_cycle)
```

    ## # A tibble: 3 x 3
    ##       x   freq percentage$x $freq
    ##   <int>  <int>        <dbl> <dbl>
    ## 1     1 172480     0.000530 91.5 
    ## 2     2  14023     0.00106   7.44
    ## 3     3   2018     0.00159   1.07

``` r
#Transform the date string to a properly mdy-hms format
min_sleep_clean <- min_sleep_df %>%
  mutate(date_time = mdy_hms(date))

#Separate the date and time columns to individual ones
min_sleep_clean <- min_sleep_clean %>% 
  separate(date_time, into = c("date", "time"),sep = " ")

min_sleep_clean$date <- ymd(min_sleep_clean$date)
min_sleep_clean$time <- hms(min_sleep_clean$time)

#Identify the week days in dates for further analysis in patterns 
min_sleep_clean$week_day <- weekdays(min_sleep_clean$date)

#Replace values with sleep cycles names
min_sleep_clean[min_sleep_clean == 1] <- "Light Sleep"
min_sleep_clean[min_sleep_clean == 2] <- "Deep Sleep"
min_sleep_clean[min_sleep_clean == 3] <- "REM Sleep"

#Identify the number of observations per day for evvery user (ID)
date_sleep <- ddply(min_sleep_clean, "Id",summarize, number_days = n_distinct(date))

#Count the frequency of each sleep cycle for every user (ID)
conflict_prefer("count", "dplyr")
```

    ## [conflicted] Removing existing preference

    ## [conflicted] Will prefer dplyr::count over any other package

``` r
long_sleep_cycle <- min_sleep_clean %>% 
  group_by(logId, date, Id) %>% 
  count(value, sort = TRUE)

#Transform the data from long format to wide format for a better analysis and 
#matching with de days data previously collected
wide_sleep <- long_sleep_cycle %>% 
  pivot_wider(names_from = value, values_from = n)

wide_sleep[is.na(wide_sleep)] <- 0
sleep_cycle_clean <- wide_sleep

summary_long_sleep <- min_sleep_clean %>% 
  count(Id, value, sort = TRUE)

#Transform the data from long format to wide format for a better analysis and 
#matching with de days data previously collected
summary_wide_sleep <- long_sleep_cycle %>% 
  pivot_wider(names_from = value, values_from = n)

#Joining both days and frequency of sleep cycles.
summary_sleep <- merge(date_sleep, summary_wide_sleep, by= c("Id"))

#Adding more information such as average sleep cycle time in minutes and hours
#per day
summary_sleep <- summary_sleep %>% 
  mutate(avg_light = `Light Sleep`/number_days, avg_deep = `Deep Sleep`/number_days,
         avg_rem = `REM Sleep`/number_days)
summary_sleep <- summary_sleep %>% 
  mutate(total_sleep = round((avg_light + avg_deep + avg_rem), digit = 2))
summary_sleep <- summary_sleep %>% 
  mutate(hours_sleep = total_sleep/60)
tibble(summary_sleep)
```

    ## # A tibble: 713 x 12
    ##            Id number_days   logId date       `Light Sleep` `Deep Sleep` `REM Sleep`
    ##         <dbl>       <int>   <dbl> <date>             <int>        <int>       <int>
    ##  1 1503960366          25 1.16e10 2016-05-06           334           31           2
    ##  2 1503960366          25 1.14e10 2016-04-13            94           NA          NA
    ##  3 1503960366          25 1.16e10 2016-05-11           285           21          NA
    ##  4 1503960366          25 1.14e10 2016-04-17           668           11          NA
    ##  5 1503960366          25 1.15e10 2016-04-29           341           13          NA
    ##  6 1503960366          25 1.15e10 2016-05-01           369           22           5
    ##  7 1503960366          25 1.14e10 2016-04-19           304           16          NA
    ##  8 1503960366          25 1.14e10 2016-04-13           290           11          12
    ##  9 1503960366          25 1.16e10 2016-05-09           338            4          NA
    ## 10 1503960366          25 1.16e10 2016-05-07           331           16           2
    ## # ... with 703 more rows, and 5 more variables: avg_light <dbl>,
    ## #   avg_deep <dbl>, avg_rem <dbl>, total_sleep <dbl>, hours_sleep <dbl>

``` r
#Tryring figure out sleep patterns through days of the week 
min_sleep_clean <- min_sleep_clean %>%
  mutate(mins = 1)

min_sleep_clean <- min_sleep_clean %>% 
  group_by(logId, date, Id) %>% 
  summarize(total_mins = sum(mins))
```

    ## `summarise()` has grouped output by 'logId', 'date'. You can override using the `.groups` argument.

``` r
min_sleep_clean$week_day <- weekdays(min_sleep_clean$date)
tibble(min_sleep_clean)
```

    ## # A tibble: 713 x 5
    ##          logId date               Id total_mins week_day
    ##          <dbl> <date>          <dbl>      <dbl> <chr>   
    ##  1 11372227280 2016-04-11 5553957443        100 Monday  
    ##  2 11372227280 2016-04-12 5553957443        364 Tuesday 
    ##  3 11372414035 2016-04-11 1927972279        124 Monday  
    ##  4 11372414035 2016-04-12 1927972279        369 Tuesday 
    ##  5 11372566564 2016-04-11 2026352035        192 Monday  
    ##  6 11372566564 2016-04-12 2026352035        354 Tuesday 
    ##  7 11372617693 2016-04-12 6962181067        387 Tuesday 
    ##  8 11373088895 2016-04-11 8378563200        101 Monday  
    ##  9 11373088895 2016-04-12 8378563200        255 Tuesday 
    ## 10 11374744422 2016-04-12 4445114986        332 Tuesday 
    ## # ... with 703 more rows

------------------------------------------------------------------------

### *PHASE 4: ANALYZE *

It’s time to use statistics in order to find some patterns on the users
behavior for each data frame.

##### **4.1. Daily Activity Analysis**

``` r
daily_act_clean %>%  
  select(TotalSteps,TotalDistance,VeryActiveMinutes, FairlyActiveMinutes,
         SedentaryMinutes,Calories, time_logged_mins, time_logged_hours ) %>%
  summary()
```

    ##    TotalSteps    TotalDistance    VeryActiveMinutes FairlyActiveMinutes
    ##  Min.   :    0   Min.   : 0.000   Min.   :  0.00    Min.   :  0.00     
    ##  1st Qu.: 3790   1st Qu.: 2.620   1st Qu.:  0.00    1st Qu.:  0.00     
    ##  Median : 7406   Median : 5.245   Median :  4.00    Median :  6.00     
    ##  Mean   : 7638   Mean   : 5.490   Mean   : 21.16    Mean   : 13.56     
    ##  3rd Qu.:10727   3rd Qu.: 7.713   3rd Qu.: 32.00    3rd Qu.: 19.00     
    ##  Max.   :36019   Max.   :28.030   Max.   :210.00    Max.   :143.00     
    ##  SedentaryMinutes    Calories    time_logged_mins time_logged_hours
    ##  Min.   :   0.0   Min.   :   0   Min.   :   2.0   Min.   : 0.03    
    ##  1st Qu.: 729.8   1st Qu.:1828   1st Qu.: 989.8   1st Qu.:16.50    
    ##  Median :1057.5   Median :2134   Median :1440.0   Median :24.00    
    ##  Mean   : 991.2   Mean   :2304   Mean   :1218.8   Mean   :20.31    
    ##  3rd Qu.:1229.5   3rd Qu.:2793   3rd Qu.:1440.0   3rd Qu.:24.00    
    ##  Max.   :1440.0   Max.   :4900   Max.   :1440.0   Max.   :24.00

-   ***Findings:***
    -   The average female user take 7,638 steps, which is translated in
        5.2Km of distance. According an study adults should aim to walk
        10,000 steps or 8km. Check out [Medical News Today
        Newsletter](https://www.medicalnewstoday.com/articles/how-many-steps-should-you-take-a-day)
        to learn more.
    -   On average, females FitBit users burns 2,304 calories per day,
        value that falls in the range provided by the [U.S. Department
        of Health and Human
        Services](https://health.gov/our-work/nutrition-physical-activity/dietary-guidelines/previous-dietary-guidelines/2015),
        that states an adult woman expends roughly 1,600 to 2,400
        calories per day.
    -   Users spends more time in a sedentary state rather than doing
        some activity that requires a little bit of stimulus. The
        average 991.2 sedentary minutes represents the 81.4% of the
        total registered time, which sounds about right, but according
        to an study by *American Journal of Epidemiology*, Women who
        lead a sedentary lifestyle age nearly eight times more than
        women who are involved in physical work. Find more on [Health
        Article](https://www.hindustantimes.com/health-and-fitness/sedentary-lifestyle-and-women-do-some-exercise-daily-else-you-ll-age-faster/story-gbDeAzXbSjuGyWaj0f0tCN.html)
        from Hindustan Times

------------------------------------------------------------------------

Let’s search for patterns throughout weekdays

``` r
daily_act_clean %>%  
  group_by(week_day) %>% 
  summarize(TotalDistance = mean(TotalDistance), 
            VeryActiveMinutes = mean(VeryActiveMinutes), 
            SedentaryMinutes = mean(SedentaryMinutes), Calories = mean(Calories),
            time_logged_mins  = mean(time_logged_mins))
```

    ## # A tibble: 7 x 6
    ##   week_day  TotalDistance VeryActiveMinutes SedentaryMinutes Calories
    ##   <chr>             <dbl>             <dbl>            <dbl>    <dbl>
    ## 1 Friday             5.31              20.1            1000.    2332.
    ## 2 Monday             5.55              23.1            1028.    2324.
    ## 3 Saturday           5.85              21.9             964.    2355.
    ## 4 Sunday             5.03              20.0             990.    2263 
    ## 5 Thursday           5.31              19.4             962.    2200.
    ## 6 Tuesday            5.83              23.0            1007.    2356.
    ## 7 Wednesday          5.49              20.8             989.    2303.
    ## # ... with 1 more variable: time_logged_mins <dbl>

------------------------------------------------------------------------

### *PHASE 5: SHARE *

``` r
#Analyze the heaartrate per hour throughta day
heartrate_hour <- heartrate_clean %>% 
  mutate(day_hour = hour(time))

heartrate_hour <- heartrate_hour %>% 
  group_by(day_hour) %>% 
  summarize(avg = round(mean(Value),digit = 2))

#Create plot for average HeartRate per Day
ggplot(data = heartrate_hour, aes(x = day_hour, y = avg,))+
  geom_line(stat = "identity", color = "red", size = 2)+
  labs(title = "Average HeartRate per Hour", x= "Time(Hour) of the day", y= "HeartRate", )+
  geom_area( fill="#69b3a2", alpha=0.4)+
  geom_point(size=3, color="#69b3a2") +
  theme(axis.text.x = element_text(angle = 90))+
  expand_limits(x = 0, y = 0)+
  geom_hline(yintercept = 86.13, linetype = "dashed", color = "blue")+
  geom_vline(xintercept = 18, linetype = "dashed", color = "blue")
```

![](Bellabeat_Case_Study_Google-Data-Analytics_files/figure-gfm/Heart%20Rate%20Analysis-1.png)<!-- -->

-   ***Findings:***:
    -   The average female user resting heart rates range from 60.23 to
        86.13 heart beats per minutes..
    -   The lowest value corresponds to hours of the day when users
        usually are resting or in a slumber, this being 4 AM, meanwhile
        the highest value is attributes to hours when the body requires
        more oxygen due to various reasons such as working out,
        completing fairly/very demanding activities, winch usually
        happens at 6 PM.
    -   According to a research led by *Women’s Health Initiative *,
        based on data on 129,135 postmenopausal women. Women that have
        higher resting hert rates (more than 76bpm) were 26% more likely
        to have a heart attack or die, from those with the lowest level
        (less than 62bpm). Find more on [What your heart rate is telling
        you](https://www.health.harvard.edu/heart-health/what-your-heart-rate-is-telling-you)
        from Harvard Health Publishing.
    -   Based on the aforementioned facts, users does not represent a
        significant issue on this matter, since their heart rate only
        raises on average above 80bpm at 6PM. It would be worthwhile to
        conduct a further investigation on why users heart beat raises
        at this hour of the day, and which activities are related to
        this phenomenon.

------------------------------------------------------------------------

![Analyze the sleep time throughout a
week](C:/Users\pc\Documents\Google%20Analytics\Case%20Study\Sleep%20Cycles.png)
\* ***Findings:***: + Sunday is the day of the week when the average
user spend more sleeping time (aprox 446mins/7.8hrs) and in bed (aprox.
8.7hrs), on the other hand on Tuesday users tends to have less sleep
time (aprox. 404mins/6.7hrs) and time in bed (aprox. 443min/7.3hrs)  
+ According to a research led by *Curent Biology* subjects who cuts
their sleep, but made up for it on weekends still received aftermath
effects. + This bad habit could result in issues like excess of calories
intake after dinner, increased weight, reduced energy expenditure and
how the body handles insulin. For more information, please refer to
[Weekend catch-up sleep won’t fix the effects of sleep deprivation on
your
waistline](https://www.health.harvard.edu/blog/weekend-catch-up-sleep-wont-fix-the-effects-of-sleep-deprivation-on-your-waistline-2019092417861).

------------------------------------------------------------------------

``` r
#Merge sleep and activity observations to look for any correlation factor
daily_act_clean <- rename(daily_act_clean, date = fixed_date )
sleep_clean <- rename(sleep_clean, date = date_time)
d_act_sleep_merged <- merge(daily_act_clean, sleep_clean, by = c('Id', 'date'))
colnames(d_act_sleep_merged)
```

    ##  [1] "Id"                       "date"                    
    ##  [3] "week_day.x"               "TotalSteps"              
    ##  [5] "TotalDistance"            "TrackerDistance"         
    ##  [7] "LoggedActivitiesDistance" "VeryActiveDistance"      
    ##  [9] "ModeratelyActiveDistance" "LightActiveDistance"     
    ## [11] "SedentaryActiveDistance"  "VeryActiveMinutes"       
    ## [13] "FairlyActiveMinutes"      "LightlyActiveMinutes"    
    ## [15] "SedentaryMinutes"         "Calories"                
    ## [17] "time_logged_mins"         "time_logged_hours"       
    ## [19] "week_day.y"               "TotalMinutesAsleep"      
    ## [21] "TotalTimeInBed"           "totaltime_awake"         
    ## [23] "TotalSleepRecords"

``` r
drops <- c("TrackerDistance", "LoggedActivitiesDistance", "VeryActiveDistance",
           "ModeratelyActiveDistance", "LightActiveDistance", "SedentaryActiveDistance",
           "time_logged_mins", "time_logged_hours", "week_day.y", "TotalSleepRecords")
d_act_sleep_merged <- d_act_sleep_merged[ , !(names(d_act_sleep_merged) %in% drops)]
colnames(d_act_sleep_merged)
```

    ##  [1] "Id"                   "date"                 "week_day.x"          
    ##  [4] "TotalSteps"           "TotalDistance"        "VeryActiveMinutes"   
    ##  [7] "FairlyActiveMinutes"  "LightlyActiveMinutes" "SedentaryMinutes"    
    ## [10] "Calories"             "TotalMinutesAsleep"   "TotalTimeInBed"      
    ## [13] "totaltime_awake"

``` r
d_act_sleep_merged <- d_act_sleep_merged %>% 
  filter(TotalMinutesAsleep > 200) %>% 
  filter(TotalSteps >= 100)

#Looking for the average light sleep time in minutes and hours
summary_sleep[is.na(summary_sleep)] <- 0
summary_sleep_cycle <- summary_sleep %>% 
  select(avg_light, avg_deep, avg_rem) %>%
  filter(avg_light >200) %>% 
  summarize(avg_light = (mean(avg_light)/60), avg_deep = (mean(avg_deep)/60), 
            avg_rem = (mean(avg_rem)/60))
head(summary_sleep_cycle)
```

    ##   avg_light avg_deep avg_rem
    ## 1       NaN      NaN     NaN

``` r
#Preparing Mets Dataframe for merging
mets_analysis<- mets_clean %>% 
  group_by(date, Id) %>% 
  summarize(total_mets = sum(METs))
```

    ## `summarise()` has grouped output by 'date'. You can override using the `.groups` argument.

``` r
head(mets_analysis)
```

    ## # A tibble: 6 x 3
    ## # Groups:   date [1]
    ##   date               Id total_mets
    ##   <date>          <dbl>      <int>
    ## 1 2016-04-12 1503960366      25241
    ## 2 2016-04-12 1624580081      17234
    ## 3 2016-04-12 1644430081      22768
    ## 4 2016-04-12 1844505072      21704
    ## 5 2016-04-12 1927972279      15599
    ## 6 2016-04-12 2022484408      23035

``` r
#Merging Activities, METs and Sleep Cycle dataframes

correlation_sleep_cycle <- wide_sleep %>% 
  filter(`Light Sleep` >200)

df_analysis <- merge(d_act_sleep_merged, correlation_sleep_cycle, by = c('Id', 'date'))
colnames(df_analysis)
```

    ##  [1] "Id"                   "date"                 "week_day.x"          
    ##  [4] "TotalSteps"           "TotalDistance"        "VeryActiveMinutes"   
    ##  [7] "FairlyActiveMinutes"  "LightlyActiveMinutes" "SedentaryMinutes"    
    ## [10] "Calories"             "TotalMinutesAsleep"   "TotalTimeInBed"      
    ## [13] "totaltime_awake"      "logId"                "Light Sleep"         
    ## [16] "Deep Sleep"           "REM Sleep"

``` r
df_analysis <- merge(df_analysis, mets_analysis, by = c('Id', 'date'))
colnames(df_analysis)
```

    ##  [1] "Id"                   "date"                 "week_day.x"          
    ##  [4] "TotalSteps"           "TotalDistance"        "VeryActiveMinutes"   
    ##  [7] "FairlyActiveMinutes"  "LightlyActiveMinutes" "SedentaryMinutes"    
    ## [10] "Calories"             "TotalMinutesAsleep"   "TotalTimeInBed"      
    ## [13] "totaltime_awake"      "logId"                "Light Sleep"         
    ## [16] "Deep Sleep"           "REM Sleep"            "total_mets"

``` r
#Dropping unnecessary fields for the analysis
drops <- c("week_day.x", "TotalMinutesAsleep", "TotalTimeInBed",
           "totaltime_awake", "logId")
df_analysis <- df_analysis[ , !(names(df_analysis) %in% drops)]
colnames(df_analysis)
```

    ##  [1] "Id"                   "date"                 "TotalSteps"          
    ##  [4] "TotalDistance"        "VeryActiveMinutes"    "FairlyActiveMinutes" 
    ##  [7] "LightlyActiveMinutes" "SedentaryMinutes"     "Calories"            
    ## [10] "Light Sleep"          "Deep Sleep"           "REM Sleep"           
    ## [13] "total_mets"

``` r
#Creating a Pearson Correlation Matrix
mydata2 <- df_analysis[, c(3:13)]
head(mydata2)
```

    ##   TotalSteps TotalDistance VeryActiveMinutes FairlyActiveMinutes
    ## 1      13162          8.50                25                  13
    ## 2      10735          6.97                21                  19
    ## 3       9762          6.28                29                  34
    ## 4      12669          8.16                36                  10
    ## 5       9705          6.48                38                  20
    ## 6      15506          9.88                50                  31
    ##   LightlyActiveMinutes SedentaryMinutes Calories Light Sleep Deep Sleep
    ## 1                  328              728     1985         327         13
    ## 2                  217              776     1797         290         11
    ## 3                  209              726     1745         412         22
    ## 4                  221              773     1863         270         16
    ## 5                  164              539     1728         668         11
    ## 6                  264              775     2035         304         16
    ##   REM Sleep total_mets
    ## 1         6      25241
    ## 2        12      22859
    ## 3         8      22190
    ## 4         3      23694
    ## 5         0      21972
    ## 6         0      25883

``` r
corr_df_analysis <- round(cor(mydata2), 2)
head(corr_df_analysis)
```

    ##                      TotalSteps TotalDistance VeryActiveMinutes
    ## TotalSteps                 1.00          0.98              0.55
    ## TotalDistance              0.98          1.00              0.59
    ## VeryActiveMinutes          0.55          0.59              1.00
    ## FairlyActiveMinutes        0.56          0.55              0.32
    ## LightlyActiveMinutes       0.39          0.36             -0.23
    ## SedentaryMinutes          -0.15         -0.15             -0.01
    ##                      FairlyActiveMinutes LightlyActiveMinutes SedentaryMinutes
    ## TotalSteps                          0.56                 0.39            -0.15
    ## TotalDistance                       0.55                 0.36            -0.15
    ## VeryActiveMinutes                   0.32                -0.23            -0.01
    ## FairlyActiveMinutes                 1.00                -0.04            -0.03
    ## LightlyActiveMinutes               -0.04                 1.00            -0.36
    ## SedentaryMinutes                   -0.03                -0.36             1.00
    ##                      Calories Light Sleep Deep Sleep REM Sleep total_mets
    ## TotalSteps               0.40       -0.22       0.13     -0.11       0.77
    ## TotalDistance            0.52       -0.23       0.10     -0.11       0.79
    ## VeryActiveMinutes        0.63       -0.26      -0.07     -0.04       0.72
    ## FairlyActiveMinutes      0.17       -0.20       0.44     -0.06       0.46
    ## LightlyActiveMinutes     0.07        0.10      -0.12     -0.05       0.36
    ## SedentaryMinutes         0.04       -0.43      -0.04     -0.17      -0.02

``` r
melted_corr_df_analysis <- melt(corr_df_analysis)
head(melted_corr_df_analysis)
```

    ##                   Var1       Var2 value
    ## 1           TotalSteps TotalSteps  1.00
    ## 2        TotalDistance TotalSteps  0.98
    ## 3    VeryActiveMinutes TotalSteps  0.55
    ## 4  FairlyActiveMinutes TotalSteps  0.56
    ## 5 LightlyActiveMinutes TotalSteps  0.39
    ## 6     SedentaryMinutes TotalSteps -0.15

``` r
ggplot(data = melted_corr_df_analysis, aes(Var1, y = Var2, fill = value))+
  geom_tile()
```

![](Bellabeat_Case_Study_Google-Data-Analytics_files/figure-gfm/Analyze%20correlation%20between%20variables-1.png)<!-- -->

``` r
# Get lower triangle of the correlation matrix
get_lower_tri<-function(corr_df_analysis){
  corr_df_analysis[upper.tri(corr_df_analysis)] <- NA
  return(corr_df_analysis)
}

# Get upper triangle of the correlation matrix
get_upper_tri <- function(corr_df_analysis){
  corr_df_analysis[lower.tri(corr_df_analysis)]<- NA
  return(corr_df_analysis)
}

upper_tri <- get_upper_tri(corr_df_analysis)
upper_tri
```

    ##                      TotalSteps TotalDistance VeryActiveMinutes
    ## TotalSteps                    1          0.98              0.55
    ## TotalDistance                NA          1.00              0.59
    ## VeryActiveMinutes            NA            NA              1.00
    ## FairlyActiveMinutes          NA            NA                NA
    ## LightlyActiveMinutes         NA            NA                NA
    ## SedentaryMinutes             NA            NA                NA
    ## Calories                     NA            NA                NA
    ## Light Sleep                  NA            NA                NA
    ## Deep Sleep                   NA            NA                NA
    ## REM Sleep                    NA            NA                NA
    ## total_mets                   NA            NA                NA
    ##                      FairlyActiveMinutes LightlyActiveMinutes SedentaryMinutes
    ## TotalSteps                          0.56                 0.39            -0.15
    ## TotalDistance                       0.55                 0.36            -0.15
    ## VeryActiveMinutes                   0.32                -0.23            -0.01
    ## FairlyActiveMinutes                 1.00                -0.04            -0.03
    ## LightlyActiveMinutes                  NA                 1.00            -0.36
    ## SedentaryMinutes                      NA                   NA             1.00
    ## Calories                              NA                   NA               NA
    ## Light Sleep                           NA                   NA               NA
    ## Deep Sleep                            NA                   NA               NA
    ## REM Sleep                             NA                   NA               NA
    ## total_mets                            NA                   NA               NA
    ##                      Calories Light Sleep Deep Sleep REM Sleep total_mets
    ## TotalSteps               0.40       -0.22       0.13     -0.11       0.77
    ## TotalDistance            0.52       -0.23       0.10     -0.11       0.79
    ## VeryActiveMinutes        0.63       -0.26      -0.07     -0.04       0.72
    ## FairlyActiveMinutes      0.17       -0.20       0.44     -0.06       0.46
    ## LightlyActiveMinutes     0.07        0.10      -0.12     -0.05       0.36
    ## SedentaryMinutes         0.04       -0.43      -0.04     -0.17      -0.02
    ## Calories                 1.00       -0.18      -0.32     -0.05       0.68
    ## Light Sleep                NA        1.00      -0.13      0.23      -0.21
    ## Deep Sleep                 NA          NA       1.00      0.20      -0.04
    ## REM Sleep                  NA          NA         NA      1.00      -0.07
    ## total_mets                 NA          NA         NA        NA       1.00

``` r
# Melt the correlation matrix
melted_corr_df_analysis<- melt(upper_tri, na.rm = TRUE)
# Heatmap
ggplot(data = melted_corr_df_analysis, aes(Var2, Var1, fill = value))+
  geom_tile(color = "white")+
  scale_fill_gradient2(low = "blue", high = "red", mid = "white", 
                       midpoint = 0, limit = c(-1,1), space = "Lab", 
                       name="Pearson\nCorrelation") +
  theme_minimal()+ 
  theme(axis.text.x = element_text(angle = 45, vjust = 1, 
                                   size = 12, hjust = 1))+
  coord_fixed()
```

![](Bellabeat_Case_Study_Google-Data-Analytics_files/figure-gfm/Analyze%20correlation%20between%20variables-2.png)<!-- -->

``` r
#Convert the analysis data frame into a CSV file in order to create 
#visualizations in TABLEU  

write.csv(df_analysis, file = "bellabeat_viz.csv")
```

![METs Analysis based on Calories and
Activities](C:/Users/pc/Documents/Google%20Analytics/Case%20Study/Mets%20vs%20Calories%202.png)

-   ***Findings:***
    -   There is a positive relationship between the Very Active Minutes
        and the Calories burned by users, which means the more time
        users spend in daily doing activities (cleaning, walking the
        dog, gardening) or daily exercise, leads to a greater amount of
        calories burned.  
    -   There is negative relationship between the Sedentary Minutes and
        Total Minutes Asleep. Many research have concluded that
        sedentary is strongly associated with sleep problems such as
        insomnia or cases of sleep disturbance, and could be directly
        involved with issues with the sleep cycles of the users
        (disturbances in sleep stages).
    -   Total Distance and variables related to activities, share a
        strong relationship, which means user have a common pattern of
        burning calories completing activities like walking or jogging,
        rather than spending most of this time doing exercises like
        weight lifting.

### *PHASE 6: ACT *

## *Final Conclusions*:

According to the data provided users spends more time in a sedentary
state rather than doing some activity that requires a little bit of
stimulus. The average female user resting heart rates range from 60.23
to 86.13 heart beats per minutes. Throughout a week, user never meets
the required 8 hours of sleeping, and share a common pattern in which
they try to recover the cut off sleep time on weekends, resulting in
more time in bed, and less time doing activities that could help their
calories intake. A good day with full of activities and less sedentary
times proves to be beneficial for users sleep cycle, resulting in more
deep sleep minutes, which strengthen the immune system and other key
bodily processes.

## *Applying trends to Bellabeat customers*

Bellabeat customer are woman who are interested in their health care,
that’s the main reason for them to purchase this kind of smart devices.
The previous statement are mandatory facts that may greatly influence
one person habits which directly reflects in their health and well
being. As a company committed with our users interests, that’s why
taking this behavioral data is important in order to develop new
features that understand customers needs and helps them fix bad habits
and improve their health.

## *Marketing Strategies*

Creating campaigns that promotes the benefits of a good sleep cycle in
our daily life, introducing our customers new features that will help
them create a proper sleep schedule and alignment of the circadian
rhythm.

Promote user community activities on weekends, prompting customers
performing different light, fair and intense activities, to create
awareness of their impact on calories burnt to balance the calories
intake.
