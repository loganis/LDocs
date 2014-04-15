---
title: "Overview of Loganis Query Script elements"
layout: article
desc: "LQuery or Loganis Query Script overview."
---

## About this guide

This guides provides an overview of Loganis Query Script elements, like:

* Date period
* Metrics
* Dimensions
* Query Sources
* Sorting
* Filtering

## LQuery overview

* LQuery or Loganis Query Script is a declarative query script.
* A declarative statement consists of key-value pairs: `:met "ch0:ga:visitors"`
  * key is `:met`
  * value is `"ch0:ga:visitors"`
* Order of statements is flexible.
* Semicolon is used for comment.
* Queries can be used at
  * Query Script Explorer tool
  * Excel plug-in
  * REST API for programming languages
* Supported Metrics
  * ga: [Google Analytics API v3](https://developers.google.com/analytics/devguides/reporting/core/dimsmets)
  * mcf: [Multi-Channel Funnels GA API v3](https://developers.google.com/analytics/devguides/reporting/mcf/dimsmets/)
  * fb: [Facebook Insights API](https://developers.facebook.com/docs/graph-api/reference/insights#page_impressions)
* An example LQuery script:

``` clojure
{:met "ch4:ga:visits"
 :beg "2013-03-21" :end "2013-04-17"
 :dim "date"
 :src :update
 :fun {
       "mean visits" (round (mean ch4:ga:visits)) ; rounded mean
       "visits_diff1" (diff ch4:ga:visits) ; first derivative
       "visits_diff2" (diff visits_diff1) ; second derivative
       }
 :col "date,mean visits,ch4:ga:visits,visits_diff1,visits_diff2"
 }
```

* Chart output
  * ![pic1](/assets/images/diffc.jpg "Diff Chart")
* Raw data in a table
  * ![pic1](/assets/images/difft.jpg "Diff Table")
* [Interactive Chart output](/assets/javascripts/diff.html)




## Date period :per or :beg and :end

* It is always required to provide a date period for your query
* You can use `absolute` or `relative` date definitions

### Absolute date :beg and :end

* Absolute date is useful when you are interested only in a given date period.
  * `:beg` defines the begin of the query period
  * `:end` defines the end of the query period
* You always have to define both `:beg` and `:end` in a query
* `YYYY-MM-DD` format used. like "2014-04-05"

``` clojure
{
 :beg "2014-01-01"
 :end "2014-01-31"
}
```

### Relative date period :per

* Relative date is useful when you want to reuse your query without updating `:beg` and `:end` definitions.
* Example: `last_1_month` last is called `minor`, 1 is `middle`, month is `major` term
* You can combine the following terms
* `Minor` term can be:
  * `this` period, variable length from the beginning of the period
  * `last` period, fixed length period to yesterday
  * `prev` period before `last` period
* `Middle` term can be an Integer number
* `Major` term can be:
  * `day`
  * `week` 7 days
  * `4week` 28 days
  * `month` 28 days or 4 weeks
  * `calmonth` calendar month
  * `quarter` 3 months
  * `half` 6 month or 1/2 year
  * `year` calendar year


``` clojure
{
 :per "last_1_month"
}
```
  
## Metrics :met

* Metrics are usually numbers that represents a measured value of a specific performance in a date period of a Channel.
* A single request is limited to a maximum of 10 metrics.
* Always starts with a channel label string, then a channel type string

* One Google Analytics Metric

```clojure
{
 :met "ch0:ga:visitors"
 ; Channel: ch0
 ; Channel type: ga (Google Analytics)
 ; Metric: ga:visitors
 :per "last_1_month"
 :dim "date"
}
```

* Two Google Analytics Metrics

```clojure
{
 :met "ch0:ga:visitors,ch0:ga:visits"
 ; Channel: ch0
 ; Channel type: ga (Google Analytics)
 ; Metrics: ga:visitors, ga:visits
 :per "last_1_month"
 :dim "date"
}
```

* Two Google Analytics Metrics and one Facebook Metric

```clojure
{
 :met "ch0:ga:visitors,ch0:ga:visits,ch1:fb:page_impressions"
 ; Channel: ch0
 ; Channel type: ga (Google Analytics)
 ; Metrics: ga:visitors, ga:visits
 :per "last_1_month"
 :dim "date"
}
```

### SQL to LQuery Metrics mapping examples

* `SELECT` ga:visitors `FROM` ch1
  * Fetches ga:visitors metric from ch1 GA channel

```clojure
{
 :met "ch1:ga:visitors"
 :per "last_1_month"
 :dim "date"
}
```

* `SELECT` ga:visitors, ga:visits `FROM` ch1
  * Fetches 2 metrics from ch1 GA channel

```clojure
{
 :met "ch1:ga:visitors,ch1:ga:visits"
 :per "last_1_month"
 :dim "date"
}
```

* `SELECT` ga:visitors `FROM` ch1,ch2
  * fetches ga:visitors from both ch1 and ch2 GA channel

```clojure
{
 :met "ch1:ga:visitors,ch2:ga:visitors"
 :per "last_1_month"
 :dim "date"
}
```

* `SELECT` ga:visitors,fb:page_impressions `FROM` ch1,ch3
  * Fetches ga:visitors from ch1 GA and fb:page_impressions from ch3 FB channel

```clojure
{
 :met "ch1:ga:visitors,ch3:fb:page_impressions"
 :per "last_1_month"
 :dim "date"
}
```

## Dimensions :dim

* Dimensions are descriptive attributes usually used to segment or group a Metrical value in a time period.
  * 100 `ga:visitors` in a month can be segmented by a dimension like `ga:city` in order to see which cities drives the most visitors to your site.
* A single request is limited to a maximum of 7 dimensions.
* Dimension names do not include channel ids, since we are going to group data from different channels by these dimensions.
* You always have to use at least one metric to use dimension grouping.
* GA fully supported, for FB only :dim "date" at the moment.
* Not all dimensions and metrics can be queried together.
* [Learn more on Valid Combinations](https://developers.google.com/analytics/devguides/reporting/core/dimsmets)
* Channel independent Loganis Dimensions:
  * `dateyw` week of year [1-52]
  * `dateym` month of year [1-12]
  * `year` year
  * `date` YYYY-MM-DD format date, `2014-04-05`

### SQL to LQuery Dimensions mapping examples

* `SELECT` ga:visitors `FROM` ch1 `GROUP BY` ga:city
  * Fetches ga:visitors metric from ch1 GA channel grouped by ga:city

``` clojure
{
 :met "ch1:ga:visitors"
 :dim "ga:city"
 :per "last_1_month"
}
```

* `SELECT` ga:visitors, ga:visits `FROM` ch1 `GROUP BY` ga:city
  * Fetches 2 metrics from ch1 GA channel grouped by ga:city

``` clojure
{
 :met  "ch1:ga:visitors,ch1:ga:visits"
 :dim "ga:city"
 :per "last_1_month"
}
```

* `SELECT` ga:visitors `FROM` ch1,ch2 `GROUP BY` ga:city
  * Fetches ga:visitors from both ch1 and ch2 GA channel grouped by ga:city

``` clojure
{
 :met "ch1:ga:visitors,ch2:ga:visitors"
 :dim "ga:city"
 :per "last_1_month"
}
```

## Source of query :src

* Loganis uses an intelligent result cache in order to
  * improve query speed performance 
  * lower network traffic
  * use GA and FB quotas intelligently
* `:src` can be `:update`, `:direct` or `:cache`
  * `:src :update` uses cache and fetches only missing data.
  * `:src :direct` uses no cache, all queries request data directly from GA or FB
  * `:src :cache` uses cache only
* If you do not provide `:src` tag, then `:update` will be used as default source of query

## Sort order :ord

* Sorting is supported using `:ord` tag
* You can sort by Metrics or Dimensions
* You can sort ascending or descending (-)
* Examples
  * `:ord "ch0:ga:visits"` sort by ch0:ga:visits ascending
  * `:ord "-ch0:ga:visits"` sort by ch0:ga:visits descending
  * `:ord "ga:country,ga:city"` Sort first by ga:country then by ga:city

## Normalize Dimensional values :nod

* Replaces dimensional values using regexp or list of values
* `[ ... ]` is an array of values
* `#"..."` is a regexp
* Example:
  * Mobile device vendor names instead of device model names

``` clojure
{:per "last_1_month"
 :met "ch4:ga:visitors"
 :dim "ga:mobileDeviceModel"
 :nod {"ga:mobileDeviceModel" {"Samsung" [ #"GT-.*" ]
                               "Nokia" [ #"Lumia.*"]
                               "Sony" ["WT19i" "E15i" #"C\d{4}" #"ST\d{2}.*"]
                               }
       }
 }
```

## Filter :fil

* Dimension or metric filters that restrict the data returned for your request.
* [Learn more on filter operators.](https://developers.google.com/analytics/devguides/reporting/core/v3/reference#filters)


### Metric filter operators

* `==` Equals
  * `:fil "ga:timeOnPage==10"`
  * Return results where the time on the page is exactly ten seconds:
* `!=` Does not equal
  * `:fil "ga:timeOnPage!=10"`
  * Return results where the time on the page is not ten seconds:
* `>` Greater than
  * `:fil "ga:timeOnPage>10"`
  * Return results where the time on the page is strictly greater than ten seconds:
* `<` Less than
  * `:fil "ga:timeOnPage<10"`
  * Return results where the time on the page is strictly less than ten seconds:
* `>=` Greater than or equal to
  * `:fil "ga:timeOnPage>=10"`
  * Return results where the time on the page is ten seconds or more:
* `<=` Less than or equal to
  * `:fil "ga:timeOnPage<=10"`
  * Return results where the time on the page is ten seconds or less:

### Dimension filter operators

* `==` Exact match
  * `:fil "ga:city==Irvine"`
  * Aggregate metrics where the city is Irvine:
* `!=` Does not match
  * `:fil "ga:city!=Irvine"`
  * Aggregate metrics where the city is not Irvine:
* `=@` Contains substring
  * `:fil "ga:city=@York"`
  * Aggregate metrics where the city contains York:
* `!@` Does not contain substring
  * `:fil "ga:city!@York"`
  * Aggregate metrics where the city does not contain York:
* `=~` Contains a match for the regular expression
  * `:fil "ga:city=~^New.*"`
  * Aggregate metrics where the city starts with New:
  * (the ^ character that anchors a pattern to the beginning of the string.)
* `!~` Does not match regular expression
  * `:fil "ga:city!~^New.*"`
  * Aggregate metrics where the city does not start with New:

## Advanced Segments :seg

* Segments the data returned for your request.
* [Learn more on advanced segments](https://developers.google.com/analytics/devguides/config/mgmt/v3/mgmtReference/management/segments/list#try-it)
* Dynamic segment:
  * `:seg "dynamic::ga:source=~twitter"`
* Segment by ID
  * `:seg "gaid::-3"`

* Examples for using segment:
* Really Engaged Traffic
  * `:seg "dynamic::ga:pageDepth>3;ga:timeOnSite>180"`
* 3 keywords
  * `:seg "dynamic::ga:keyword=~^\\s*[^\\s]+(\\s+[^\\s]+){2}\\s*$;ga:medium==organic"`
* 4 keywords
  * `:seg "ga:keyword=~^\\s*[^\\s]+(\\s+[^\\s]+){3}\\s*$;ga:medium==organic"`
* 5 keywords
  * `:seg "ga:keyword=~^\\s*[^\\s]+(\\s+[^\\s]+){4}\\s*$;ga:medium==organic"`
* 6+ keywords
  * `:seg "ga:keyword=~^\\s*[^\\s]+(\\s+[^\\s]+){5}\\s*$;ga:medium==organic"`
* Branded organic traffic
  * `:seg "ga:keyword=@cutroni,ga:keyword=@brand;ga:medium=@organic`
* Non-Branded organic traffic
  * `:seg "ga:keyword!@cutroni,ga:keyword!@brand;ga:medium=@organic"`
* Not Provided keyword traffic
  * `:seg "ga:keyword=@(not provided)"`
* 7+ keywords
  * `:seg "ga:keyword=~^\\s*[^\\s]+(\\s+[^\\s]+){6,}\\s*$;ga:medium=@organic"`
* Ad position Top
  * `:seg "ga:adSlot=@Top"`
* Ad position RHS (Right hand side)
  * `:seg "ga:adSlot=@RHS"`
* Google Adwords CPC
  * `:seg "ga:medium=@cpc;ga:source=@google"`
* Generic Keywords- Branded Ad Text
  * `:seg "ga:adContent=@brand,ga:keyword!@brand"`
* Sitelink in landing page
  * `:seg "ga:landingPagePath=@sitelink"`
* Paid Branded keywords
  * `:seg "ga:keyword=@brand;ga:medium=@cpc|ppc"`
* Paid generic terms excluding Brand
  * `:seg "ga:keyword!@brand;ga:medium=@cpc|pp"`

## Maximize the number of queried rows :max

* Useful for maximizing the number of rows returned from GA or FB

``` clojure
{
 :max 10 ; Query max 10 rows
 :met "ch2:ga:visitors"
 :per "last_1_month"
 :dim "date"
}
```

## Limit the number of returned rows 

* Useful for limiting the numbers of rows after processing
* When you need Top 10 performing media etc.

``` clojure
{
 ;; Top 10 days in last month when most visitors arrived
 :lim 10 ; Return first 10 rows only after processing
 :met "ch2:ga:visitors"
 :per "last_1_month"
 :dim "date"
 :ord "-ch2:ga:visitors"
}
```

## Column filter :col

* Filter final dataset column and results to only those column names that specified in :col
* Useful for rearranging column order or hiding columns
* `:col "ch0:ga:visits,ch0:ga:visitors"`

## Transpose rows and columns :tra

* Transpose final dataset rows and columns
* `:tra true`

## Time series Frequency :frq

* Sets aggregation time frame.
* Values can be `:daily`, `:weekly` or `:monthly`
* Default is freqency is daily

``` clojure
{
 :met "ch1:ga:visitors"
 :per "last_4_week"
 :dim "date"
 :frq :daily 
}
```

* `:weekly` date dimension is `dateyw` (week of the year)

``` clojure
{
 :met "ch1:ga:visitors"
 :per "last_4_week"
 :dim "dateyw"
 :frq :weekly 
}
```

* `:monthly` date dimension is `dateym`  (month of the year)

``` clojure
{
 :met "ch1:ga:visitors"
 :per "last_4_week"
 :dim "dateym"
 :frq :monthly 
}
```

## Join Queries :joi

* Joins serveral queries into a result dataset by a join key
  * `:query [list of object-ids]` 
  * `:key "column name"`
  * `:col "column names separated by a comma"`
* Default join key is `date`

* Example 1

``` clojure
{
  :joi {:query ["521f0cd1e4b0f10cb48a6392" "52207ba6e4b0fdc12a933d0c"]}
  ; minimal join query, join 2 queries by date, show all columns
}
```

* Example 2

``` clojure
{
  :joi {:query ["521f0cd1e4b0f10cb48a6392" "52207ba6e4b0fdc12a933d0c"]}
  :key "date"
  :col "date,ch1:ga:visits,ch2:ga:visits"
}
```

## Dashboard assembly :dsh

* Dashboard assemby by referring to query object-ids
* 1 line consist 12 cells
* `:chart` tag needs a matrix array
  * a `2x2` dashboard definition `[[[chart1][chart2]][chart3][chart4]]`
* One query dashboard definition requires 3 parameters:
  * Query object-id: `"524aa20ae4b0c2f2d313a807"`
  * Title and optional tooltip seperated by a `|` character: `"title1 logscale|tooltip text"` (Tooltip text can contain HTML tags)
  * Size of cell (1-12)
* `:label` tags need 1 dashboard title and a group title for each row
* `:next` optional tag can refer to a `next` dashboard and includes an HTML link in final dashboard.
* Dashboards needs to be `exported` to see it.
  

``` clojure
{:dsh {:chart [
               [ ; This is row 1 group, 6+6 wide
                ["524aa20ae4b0c2f2d313a807" "title1 logscale|tooltip text" 6]
                ["521dd1f1e4b053cf3f34ddca" "title2 candle|tooltip text" 6]
                ]
               [ ; This is row 2 group, 3+6+3 wide
                ["52303bdce4b02b20312dcdce" "title3 combo|tooltip text" 3]
                ["52304d9ce4b02b20312dd4ff" "title4 map|tooltip text" 6]
                ["52305528e4b02b20312ddd23" "title5 scatter trendb|tooltip text" 3]
                ]
               ]
       :label ["Dashboard label" "Row1 group label" "Row2 group label"]
       :next "521f0cd1e4b0f10cb48a6392"
       }
 }
```


## Function :fun

* Functions can be used to create a new column values by using arithmetic functions
* Example : sum of 2 columns
  * `:fun` creates a new column `Sum` that is the sum of 2 base metrics and `Sum2` that refers to `Sum`.

``` clojure
{:met "ch0:ga:visits,ch1:ga:visits"
 :dim "date"
 :per "last_1_week"
 :fun {
 "Sum" ($= ch0:ga:visits + ch1:ga:visits)
 "Sum2" ($= Sum * 2)
 }}
```
* Example : weighted sort of visits by country (weight is avgTimeOnPage)

``` clojure
{
 :met "ch0:ga:visits,ch0:ga:avgTimeOnPage"
 :per "last_1_week"
 :dim "ga:country"
 :fun {"ws-visits" (wsort  ch0:ga:visits ch0:ga:avgTimeOnPage )}
 :ord "-ws-vsits"
}
```
* List of Loganis arithmetic functions (function column-name)
  * `(wsort value-column weight-column)` Weighted sort values for each row
  * `(wmean value-column weight-column)` Weighted mean for result dataset
  * `($= column1 operator column2)` general arithmetic operations (+,-,*,/)
  * `(log column)` natural logarithm
  * `(log2 column)` base 2 logarithm
  * `(log10 column)` base 10 logarithm
  * `(mean column)` calculate average of a column
  * `(min column)` smallest value of a column
  * `(max column)` biggest value of a column
  * `(round column)` round values of a column to integer
  * `(round2 column)` round values of a column to 2 digit fraction
  * `(median column)` median value of a column
  * `(sd column)` standard deviation of a column
  * `(diff column)` derivation values of a column
  * `(norm column)` normalize values of a column between 0 and 1
  * `(share column)` calculates percent of values of the total sum of column


  

