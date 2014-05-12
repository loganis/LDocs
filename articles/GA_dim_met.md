---
title: "GA metrics and dimensions overview"
desc: "Loganis Queries using GA Dimensions and Metrics overview"
layout: article
---

##Overview of GA metrics and dimensions
* This guides provides an overview of GA dimensions and metrics by example
* Based on GA Metadata API
* 1 Metric, 1 Dimension and 1 LQuery for each example

### Exceptions


#### Crashes by Mobile Input Selector
  * `Crashes` (INTEGER): The number of exceptions where isFatal is set to true.
  * `Mobile Input Selector` (STRING): Selector used on the mobile device (e.g.: touchscreen, joystick, clickwheel, stylus).

``` clojure
{ :met "ch0:ga:fatalExceptions"
  :dim "ga:mobileInputSelector"
  :per "last_1_month"}
```


#### Crashes / Screen by Hostname
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `Hostname` (STRING): The hostname from which the tracking request was made.

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:hostname"
  :per "last_1_month"}
```


#### Exceptions / Screen by Count of Sessions
  * `Exceptions / Screen` (PERCENT): The number of exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:exceptions / ga:screenviews*
  * `Count of Sessions` (STRING): The session index for a user to your property. Each session from a unique user will get its own incremental index starting from 1 for the first session. Subsequent sessions do not change previous session indicies. For example, if a certain user has 4 sessions to your website, sessionCount for that user will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:exceptionsPerScreenview"
  :dim "ga:sessionCount"
  :per "last_1_month"}
```


#### Exceptions by Mobile Device Info
  * `Exceptions` (INTEGER): The number of exceptions that were sent to Google Analytics.
  * `Mobile Device Info` (STRING): The branding, model, and marketing name used to identify the mobile device.

``` clojure
{ :met "ch0:ga:exceptions"
  :dim "ga:mobileDeviceInfo"
  :per "last_1_month"}
```

### Traffic Sources


#### Bounce Rate by Medium
  * `Bounce Rate` (PERCENT): The percentage of single-page session (i.e., session in which the person left your property from the first page).
  * Calculated by *ga:bounces / ga:sessions*
  * `Medium` (STRING): The type of referrals to your property. When using manual campaign tracking, the value of the utm_medium campaign tracking parameter. When using AdWords autotagging, the value is ppc. If the user comes from a search engine detected by Google Analytics, the value is organic. If the referrer is not a search engine, the value is referral. If the users came directly to the property, and document.referrer is empty, the value is (none).

``` clojure
{ :met "ch0:ga:bounceRate"
  :dim "ga:medium"
  :per "last_1_month"}
```


#### Page Download Time (ms) by Social Network
  * `Page Download Time (ms)` (INTEGER): The total amount of time (in milliseconds) to download this page among all samples.
  * `Social Network` (STRING): Name of the social network. This can be related to the referring social network for traffic sources, or to the social network for social data hub activities. E.g. Google+, Blogger, etc.

``` clojure
{ :met "ch0:ga:pageDownloadTime"
  :dim "ga:socialNetwork"
  :per "last_1_month"}
```


#### Organic Searches by Social Source Referral
  * `Organic Searches` (INTEGER): The number of organic searches that happened within a session. This metric is search engine agnostic.
  * `Social Source Referral` (STRING): Indicates sessions that arrived to the property from a social source. The possible values are Yes or No where the first letter is capitalized.

``` clojure
{ :met "ch0:ga:organicSearches"
  :dim "ga:hasSocialSourceReferral"
  :per "last_1_month"}
```


#### Average QTY by Campaign
  * `Average QTY` (FLOAT): The average quantity of this item (or group of items) sold per purchase.
  * Calculated by *ga:itemQuantity / ga:uniquePurchases*
  * `Campaign` (STRING): When using manual campaign tracking, the value of the utm_campaign campaign tracking parameter. When using AdWords autotagging, the name(s) of the online ad campaign that you use for your property. Otherwise the value (not set) is used.

``` clojure
{ :met "ch0:ga:itemsPerPurchase"
  :dim "ga:campaign"
  :per "last_1_month"}
```


#### Abandoned Funnels by Source
  * `Abandoned Funnels` (INTEGER): The overall number of times users started goals without actually completing them.
  * Calculated by *(ga:goalStartsAll - ga:goalCompletionsAll)*
  * `Source` (STRING): The source of referrals to your property. When using manual campaign tracking, the value of the utm_source campaign tracking parameter. When using AdWords autotagging, the value is google. Otherwise the domain of the source referring the user to your property (e.g. document.referrer). The value may also contain a port address. If the user arrived without a referrer, the value is (direct)

``` clojure
{ :met "ch0:ga:goalAbandonsAll"
  :dim "ga:source"
  :per "last_1_month"}
```


#### Avg. Session Duration by Referral Path
  * `Avg. Session Duration` (TIME): The average duration of user sessions represented in total seconds.
  * Calculated by *ga:sessionDuration / ga:sessions*
  * `Referral Path` (STRING): The path of the referring URL (e.g. document.referrer). If someone places a link to your property on their website, this element contains the path of the page that contains the referring link.

``` clojure
{ :met "ch0:ga:avgTimeOnSite"
  :dim "ga:referralPath"
  :per "last_1_month"}
```


#### Crashes by Ad Content
  * `Crashes` (INTEGER): The number of exceptions where isFatal is set to true.
  * `Ad Content` (STRING): When using manual campaign tracking, the value of the utm_content campaign tracking parameter. When using AdWords autotagging, the first line of the text for your online Ad campaign. If you are using mad libs for your AdWords content, this field displays the keywords you provided for the mad libs keyword match. Otherwise the value is (not set)

``` clojure
{ :met "ch0:ga:fatalExceptions"
  :dim "ga:adContent"
  :per "last_1_month"}
```


#### Avg. Time on Screen by Keyword
  * `Avg. Time on Screen` (TIME): The average amount of time users spent on a screen in seconds.
  * `Keyword` (STRING): When using manual campaign tracking, the value of the utm_term campaign tracking parameter. When using AdWords autotagging or if a user used organic search to reach your property, the keywords used by users to reach your property. Otherwise the value is (not set).

``` clojure
{ :met "ch0:ga:avgScreenviewDuration"
  :dim "ga:keyword"
  :per "last_1_month"}
```


#### Crashes / Screen by Full Referrer
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `Full Referrer` (STRING): The full referring URL including the hostname and path.

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:fullReferrer"
  :per "last_1_month"}
```


#### Clicks by Source / Medium
  * `Clicks` (INTEGER): The total number of times users have clicked on an ad to reach your property.
  * `Source / Medium` (STRING): Combined values of ga:source and ga:medium.

``` clojure
{ :met "ch0:ga:adClicks"
  :dim "ga:sourceMedium"
  :per "last_1_month"}
```

### User


#### New Users by User Type
  * `New Users` (INTEGER): The number of users whose session on your property was marked as a first-time session.
  * `User Type` (STRING): A boolean indicating if a user is new or returning. Possible values: New Visitor, Returning Visitor.

``` clojure
{ :met "ch0:ga:newUsers"
  :dim "ga:userType"
  :per "last_1_month"}
```


#### Users by Days Since Last Session
  * `Users` (INTEGER): Total number of users to your property for the requested time period.
  * `Days Since Last Session` (STRING): The number of days elapsed since users last visited your property. Used to calculate user loyalty.

``` clojure
{ :met "ch0:ga:users"
  :dim "ga:daysSinceLastSession"
  :per "last_1_month"}
```


#### % New Sessions by Count of Sessions
  * `% New Sessions` (PERCENT): The percentage of sessions by people who had never visited your property before.
  * Calculated by *ga:newUsers / ga:sessions*
  * `Count of Sessions` (STRING): The session index for a user to your property. Each session from a unique user will get its own incremental index starting from 1 for the first session. Subsequent sessions do not change previous session indicies. For example, if a certain user has 4 sessions to your website, sessionCount for that user will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:percentNewSessions"
  :dim "ga:sessionCount"
  :per "last_1_month"}
```


#### Local Revenue by User Defined Value
  * `Local Revenue` (CURRENCY): Transaction revenue in local currency.
  * `User Defined Value` (STRING): The value provided when you define custom user segments for your property.

``` clojure
{ :met "ch0:ga:localTransactionRevenue"
  :dim "ga:userDefinedValue"
  :per "last_1_month"}
```

### Site Speed


#### Speed Metrics Sample by Minute
  * `Speed Metrics Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the averages for site speed metrics. This metric is used in all site speed average calculations including avgDomainLookupTime, avgPageDownloadTime, avgRedirectionTime, avgServerConnectionTime, and avgServerResponseTime.
  * `Minute` (STRING): Returns the minute in the hour. The possible values are between 00 and 59.

``` clojure
{ :met "ch0:ga:speedMetricsSample"
  :dim "ga:minute"
  :per "last_1_month"}
```


#### Domain Lookup Time (ms) by Social Entity
  * `Domain Lookup Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in DNS lookup for this page among all samples.
  * `Social Entity` (STRING): For social interactions, a value representing the URL (or resource) which receives the social network action.

``` clojure
{ :met "ch0:ga:domainLookupTime"
  :dim "ga:socialInteractionTarget"
  :per "last_1_month"}
```


#### Page Download Time (ms) by Originating Social Action
  * `Page Download Time (ms)` (INTEGER): The total amount of time (in milliseconds) to download this page among all samples.
  * `Originating Social Action` (STRING): For a social data hub activity, this value represents the type of social action associated with the activity (e.g. vote, comment, +1, etc.).

``` clojure
{ :met "ch0:ga:pageDownloadTime"
  :dim "ga:socialActivityAction"
  :per "last_1_month"}
```


#### Avg. Server Connection Time (sec) by Week Index
  * `Avg. Server Connection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in establishing TCP connection for this page.
  * Calculated by *(ga:serverConnectionTime / ga:speedMetricsSample / 1000)*
  * `Week Index` (STRING): Index for each week in the specified date range. Index for the first week in the date range is 0, 1 for the second week, and so on. The index corresponds to week entries.

``` clojure
{ :met "ch0:ga:avgServerConnectionTime"
  :dim "ga:nthWeek"
  :per "last_1_month"}
```


#### Avg. Domain Lookup Time (sec) by Social Network
  * `Avg. Domain Lookup Time (sec)` (FLOAT): The average amount of time (in seconds) spent in DNS lookup for this page.
  * Calculated by *(ga:domainLookupTime / ga:speedMetricsSample / 1000)*
  * `Social Network` (STRING): Name of the social network. This can be related to the referring social network for traffic sources, or to the social network for social data hub activities. E.g. Google+, Blogger, etc.

``` clojure
{ :met "ch0:ga:avgDomainLookupTime"
  :dim "ga:socialNetwork"
  :per "last_1_month"}
```


#### Avg. Redirection Time (sec) by Minute Index
  * `Avg. Redirection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in redirects before fetching this page. If there are no redirects, the value for this metric is expected to be 0.
  * Calculated by *(ga:redirectionTime / ga:speedMetricsSample / 1000)*
  * `Minute Index` (STRING): Index for each minute in the specified date range. Index for the first minute of first day (i.e., start-date) in the date range is 0, 1 for the next minute, and so on.

``` clojure
{ :met "ch0:ga:avgRedirectionTime"
  :dim "ga:nthMinute"
  :per "last_1_month"}
```


#### Document Content Loaded Time (ms) by Browser
  * `Document Content Loaded Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document and execute deferred and parser-inserted scripts (DOMContentLoaded), including the network time from the user's location to your server. Parsing of the document is finished, the Document Object Model is ready, but referenced style sheets, images, and subframes may not be finished loading. This event is often the starting point for javascript framework execution, e.g., JQuery's onready() callback, etc.
  * `Browser` (STRING): The names of browsers used by users to your website. For example, Internet Explorer or Firefox.

``` clojure
{ :met "ch0:ga:domContentLoadedTime"
  :dim "ga:browser"
  :per "last_1_month"}
```


#### DOM Latency Metrics Sample by Shared URL
  * `DOM Latency Metrics Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the averages for site speed DOM metrics. This metric is used in the avgDomContentLoadedTime and avgDomInteractiveTime calculations.
  * `Shared URL` (STRING): For a social data hub activity, this value represents the URL shared by the associated social network user.

``` clojure
{ :met "ch0:ga:domLatencyMetricsSample"
  :dim "ga:socialActivityContentUrl"
  :per "last_1_month"}
```


#### Server Connection Time (ms) by Longitude
  * `Server Connection Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in establishing TCP connection for this page among all samples.
  * `Longitude` (STRING): The approximate longitude of the user's city. Derived from IP address. Locations east of the meridian are represented by positive values and locations west of the meridian by negative values.

``` clojure
{ :met "ch0:ga:serverConnectionTime"
  :dim "ga:longitude"
  :per "last_1_month"}
```


#### Server Response Time (ms) by Month of Year
  * `Server Response Time (ms)` (INTEGER): The total amount of time (in milliseconds) your server takes to respond to a user request among all samples, including the network time from user's location to your server.
  * `Month of Year` (STRING): Combined values of ga:year and ga:month.

``` clojure
{ :met "ch0:ga:serverResponseTime"
  :dim "ga:yearMonth"
  :per "last_1_month"}
```


#### Document Interactive Time (ms) by Currency Code
  * `Document Interactive Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document (DOMInteractive), including the network time from the user's location to your server. At this time, the user can interact with the Document Object Model even though it is not fully loaded.
  * `Currency Code` (STRING): The local currency code of the transaction based on ISO 4217 standard.

``` clojure
{ :met "ch0:ga:domInteractiveTime"
  :dim "ga:currencyCode"
  :per "last_1_month"}
```


#### Avg. Page Download Time (sec) by Placement Domain
  * `Avg. Page Download Time (sec)` (FLOAT): The average amount of time (in seconds) to download this page.
  * Calculated by *(ga:pageDownloadTime / ga:speedMetricsSample / 1000)*
  * `Placement Domain` (STRING): The domains where your ads on the content network were placed.

``` clojure
{ :met "ch0:ga:avgPageDownloadTime"
  :dim "ga:adPlacementDomain"
  :per "last_1_month"}
```


#### Page Load Time (ms) by Ad Format
  * `Page Load Time (ms)` (INTEGER): Total Page Load Time is the amount of time (in milliseconds) it takes for pages from the sample set to load, from initiation of the pageview (e.g. click on a page link) to load completion in the browser.
  * `Ad Format` (STRING): Your AdWords ad formats (Text, Image, Flash, Video, etc.).

``` clojure
{ :met "ch0:ga:pageLoadTime"
  :dim "ga:adFormat"
  :per "last_1_month"}
```


#### Page Load Sample by Goal Previous Step - 3
  * `Page Load Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the average page load time.
  * `Goal Previous Step - 3` (STRING): The page path or screen name that matched any destination type goal, three steps prior to the goal completion location.

``` clojure
{ :met "ch0:ga:pageLoadSample"
  :dim "ga:goalPreviousStep3"
  :per "last_1_month"}
```


#### Avg. Document Interactive Time (sec) by Longitude
  * `Avg. Document Interactive Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document and execute deferred and parser-inserted scripts including the network time from the user's location to your server.
  * Calculated by *(ga:domInteractiveTime / ga:domLatencyMetricsSample / 1000)*
  * `Longitude` (STRING): The approximate longitude of the user's city. Derived from IP address. Locations east of the meridian are represented by positive values and locations west of the meridian by negative values.

``` clojure
{ :met "ch0:ga:avgDomInteractiveTime"
  :dim "ga:longitude"
  :per "last_1_month"}
```


#### Redirection Time (ms) by Custom Dimension 
  * `Redirection Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in redirects before fetching this page among all samples. If there are no redirects, the value for this metric is expected to be 0.
  * `Custom Dimension ` (STRING): The name of the requested custom dimension, where XX refers the number/index of the custom dimension.

``` clojure
{ :met "ch0:ga:redirectionTime"
  :dim "ga:dimensionXX"
  :per "last_1_month"}
```


#### Avg. Page Load Time (sec) by Hostname
  * `Avg. Page Load Time (sec)` (FLOAT): The average amount of time (in seconds) it takes for pages from the sample set to load, from initiation of the pageview (e.g. click on a page link) to load completion in the browser.
  * Calculated by *(ga:pageLoadTime / ga:pageLoadSample / 1000)*
  * `Hostname` (STRING): The hostname from which the tracking request was made.

``` clojure
{ :met "ch0:ga:avgPageLoadTime"
  :dim "ga:hostname"
  :per "last_1_month"}
```


#### Avg. Document Content Loaded Time (sec) by Hour
  * `Avg. Document Content Loaded Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document.
  * Calculated by *(ga:domContentLoadedTime / ga:domLatencyMetricsSample / 1000)*
  * `Hour` (STRING): A two-digit hour of the day ranging from 00-23 in the timezone configured for the account. This value is also corrected for daylight savings time, adhering to all local rules for daylight savings time. If your timezone follows daylight savings time, there will be an apparent bump in the number of sessions during the change-over hour (e.g. between 1:00 and 2:00) for the day per year when that hour repeats. A corresponding hour with zero sessions will occur at the opposite changeover. (Google Analytics does not track user time more precisely than hours.)

``` clojure
{ :met "ch0:ga:avgDomContentLoadedTime"
  :dim "ga:hour"
  :per "last_1_month"}
```


#### Avg. Server Response Time (sec) by Mobile Device Marketing Name
  * `Avg. Server Response Time (sec)` (FLOAT): The average amount of time (in seconds) your server takes to respond to a user request, including the network time from user's location to your server.
  * Calculated by *(ga:serverResponseTime / ga:speedMetricsSample / 1000)*
  * `Mobile Device Marketing Name` (STRING): The marketing name used for the mobile device.

``` clojure
{ :met "ch0:ga:avgServerResponseTime"
  :dim "ga:mobileDeviceMarketingName"
  :per "last_1_month"}
```

### Adwords


#### CPC by AdWords Customer ID
  * `CPC` (CURRENCY): Cost to advertiser per click.
  * Calculated by *ga:adCost / ga:adClicks*
  * `AdWords Customer ID` (STRING): A string. Corresponds to AdWords API AccountInfo.customerId.

``` clojure
{ :met "ch0:ga:CPC"
  :dim "ga:adwordsCustomerID"
  :per "last_1_month"}
```


#### Cost by TrueView Video Ad
  * `Cost` (CURRENCY): Derived cost for the advertising campaign. The currency for this value is based on the currency that you set in your AdWords account.
  * `TrueView Video Ad` (STRING): 'Yes' or 'No' - Indicates whether the ad is an AdWords TrueView video ad.

``` clojure
{ :met "ch0:ga:adCost"
  :dim "ga:isTrueViewVideoAd"
  :per "last_1_month"}
```


#### Goal Completions by Display URL
  * `Goal Completions` (INTEGER): The total number of completions for all goals defined for your profile.
  * `Display URL` (STRING): The URLs your AdWords ads displayed.

``` clojure
{ :met "ch0:ga:goalCompletionsAll"
  :dim "ga:adDisplayUrl"
  :per "last_1_month"}
```


#### Cost per Transaction by AdWords Campaign ID
  * `Cost per Transaction` (CURRENCY): The cost per transaction for your property.
  * Calculated by *(ga:adCost) / (ga:transactions)*
  * `AdWords Campaign ID` (STRING): A string. Corresponds to AdWords API Campaign.id.

``` clojure
{ :met "ch0:ga:costPerTransaction"
  :dim "ga:adwordsCampaignID"
  :per "last_1_month"}
```


#### Screen Views by Ad Slot
  * `Screen Views` (INTEGER): The total number of screenviews.
  * `Ad Slot` (STRING): The location of the advertisement on the hosting page (Top, RHS, or not set).

``` clojure
{ :met "ch0:ga:screenviews"
  :dim "ga:adSlot"
  :per "last_1_month"}
```


#### Avg. Redirection Time (sec) by AdWords Ad Group ID
  * `Avg. Redirection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in redirects before fetching this page. If there are no redirects, the value for this metric is expected to be 0.
  * Calculated by *(ga:redirectionTime / ga:speedMetricsSample / 1000)*
  * `AdWords Ad Group ID` (STRING): A string. Corresponds to AdWords API AdGroup.id.

``` clojure
{ :met "ch0:ga:avgRedirectionTime"
  :dim "ga:adwordsAdGroupID"
  :per "last_1_month"}
```


#### Margin by Ad Distribution Network
  * `Margin` (PERCENT): The overall transaction profit margin.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / (ga:transactionRevenue + ga:goalValueAll)*
  * `Ad Distribution Network` (STRING): The networks used to deliver your ads (Content, Search, Search partners, etc.).

``` clojure
{ :met "ch0:ga:margin"
  :dim "ga:adDistributionNetwork"
  :per "last_1_month"}
```


#### CTR by Placement Type
  * `CTR` (PERCENT): Click-through-rate for your ad. This is equal to the number of clicks divided by the number of impressions for your ad (e.g. how many times users clicked on one of your ads where that ad appeared).
  * Calculated by *ga:adClicks / ga:impressions*
  * `Placement Type` (STRING): How you manage your ads on the content network. Values are Automatic placements or Managed placements.

``` clojure
{ :met "ch0:ga:CTR"
  :dim "ga:adTargetingOption"
  :per "last_1_month"}
```


#### RPC by Matched Search Query
  * `RPC` (CURRENCY): RPC or revenue-per-click is the average revenue (from ecommerce sales and/or goal value) you received for each click on one of your search ads.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll) / ga:adClicks*
  * `Matched Search Query` (STRING): The search queries that triggered impressions of your AdWords ads.

``` clojure
{ :met "ch0:ga:RPC"
  :dim "ga:adMatchedQuery"
  :per "last_1_month"}
```


#### Page Value by Ad Slot Position
  * `Page Value` (CURRENCY): The average value of this page or set of pages. Page Value is (ga:transactionRevenue + ga:goalValueAll) / ga:uniquePageviews (for the page or set of pages).
  * `Ad Slot Position` (STRING): The ad slot positions in which your AdWords ads appeared (1-8).

``` clojure
{ :met "ch0:ga:pageValue"
  :dim "ga:adSlotPosition"
  :per "last_1_month"}
```


#### Unique Screen Views by Keyword Match Type
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Keyword Match Type` (STRING): The match types applied to your keywords (Phrase, Exact, Broad). Details: https://support.google.com/adwords/answer/2472708?hl=en

``` clojure
{ :met "ch0:ga:uniqueAppviews"
  :dim "ga:adKeywordMatchType"
  :per "last_1_month"}
```


#### CPM by Destination URL
  * `CPM` (CURRENCY): Cost per thousand impressions.
  * Calculated by *ga:adCost / (ga:impressions / 1000)*
  * `Destination URL` (STRING): The URLs to which your AdWords ads referred traffic.

``` clojure
{ :met "ch0:ga:CPM"
  :dim "ga:adDestinationUrl"
  :per "last_1_month"}
```


#### Cost per Conversion by AdWords Creative ID
  * `Cost per Conversion` (CURRENCY): The cost per conversion (including ecommerce and goal conversions) for your property.
  * Calculated by *(ga:adCost) / (ga:transactions  +  ga:goalCompletionsAll)*
  * `AdWords Creative ID` (STRING): A string. Corresponds to AdWords API Ad.id.

``` clojure
{ :met "ch0:ga:costPerConversion"
  :dim "ga:adwordsCreativeID"
  :per "last_1_month"}
```


#### ROI by Ad Group
  * `ROI` (PERCENT): Returns on Investment is overall transaction profit divided by derived advertising cost.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / ga:adCost*
  * `Ad Group` (STRING): The name of your AdWords ad group.

``` clojure
{ :met "ch0:ga:ROI"
  :dim "ga:adGroup"
  :per "last_1_month"}
```


#### Avg. Document Interactive Time (sec) by Query Match Type
  * `Avg. Document Interactive Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document and execute deferred and parser-inserted scripts including the network time from the user's location to your server.
  * Calculated by *(ga:domInteractiveTime / ga:domLatencyMetricsSample / 1000)*
  * `Query Match Type` (STRING): The match types applied for the search term the user had input(Phrase, Exact, Broad, etc.). Ads on the content network are identified as "Content network". Details: https://support.google.com/adwords/answer/2472708?hl=en

``` clojure
{ :met "ch0:ga:avgDomInteractiveTime"
  :dim "ga:adMatchType"
  :per "last_1_month"}
```


#### Cost per Goal Conversion by AdWords Criteria ID
  * `Cost per Goal Conversion` (CURRENCY): The cost per goal conversion for your property.
  * Calculated by *(ga:adCost) / (ga:goalCompletionsAll)*
  * `AdWords Criteria ID` (STRING): A string. Corresponds to AdWords API Criterion.id.

``` clojure
{ :met "ch0:ga:costPerGoalConversion"
  :dim "ga:adwordsCriteriaID"
  :per "last_1_month"}
```


#### Impressions by Ad Format
  * `Impressions` (INTEGER): Total number of campaign impressions.
  * `Ad Format` (STRING): Your AdWords ad formats (Text, Image, Flash, Video, etc.).

``` clojure
{ :met "ch0:ga:impressions"
  :dim "ga:adFormat"
  :per "last_1_month"}
```


#### Clicks by Placement Domain
  * `Clicks` (INTEGER): The total number of times users have clicked on an ad to reach your property.
  * `Placement Domain` (STRING): The domains where your ads on the content network were placed.

``` clojure
{ :met "ch0:ga:adClicks"
  :dim "ga:adPlacementDomain"
  :per "last_1_month"}
```

### Adsense


#### AdSense Ads Clicked by Hour
  * `AdSense Ads Clicked` (INTEGER): The number of times AdSense ads on your site were clicked.
  * `Hour` (STRING): A two-digit hour of the day ranging from 00-23 in the timezone configured for the account. This value is also corrected for daylight savings time, adhering to all local rules for daylight savings time. If your timezone follows daylight savings time, there will be an apparent bump in the number of sessions during the change-over hour (e.g. between 1:00 and 2:00) for the day per year when that hour repeats. A corresponding hour with zero sessions will occur at the opposite changeover. (Google Analytics does not track user time more precisely than hours.)

``` clojure
{ :met "ch0:ga:adsenseAdsClicks"
  :dim "ga:hour"
  :per "last_1_month"}
```


#### AdSense Page Impressions by Timing Category
  * `AdSense Page Impressions` (INTEGER): The number of pageviews during which an AdSense ad was displayed. A page impression can have multiple Ad Units.
  * `Timing Category` (STRING): A string for categorizing all user timing variables into logical groups for easier reporting purposes.

``` clojure
{ :met "ch0:ga:adsensePageImpressions"
  :dim "ga:userTimingCategory"
  :per "last_1_month"}
```


#### AdSense Ads Viewed by Goal Previous Step - 2
  * `AdSense Ads Viewed` (INTEGER): The number of AdSense ads viewed. Multiple ads can be displayed within an Ad Unit.
  * `Goal Previous Step - 2` (STRING): The page path or screen name that matched any destination type goal, two steps prior to the goal completion location.

``` clojure
{ :met "ch0:ga:adsenseAdsViewed"
  :dim "ga:goalPreviousStep2"
  :per "last_1_month"}
```


#### AdSense Revenue by Refined Keyword
  * `AdSense Revenue` (CURRENCY): The total revenue from AdSense ads.
  * `Refined Keyword` (STRING): Subsequent keyword search terms or strings entered by users after a given initial string search.

``` clojure
{ :met "ch0:ga:adsenseRevenue"
  :dim "ga:searchKeywordRefinement"
  :per "last_1_month"}
```


#### AdSense Exits by User Defined Value
  * `AdSense Exits` (INTEGER): The number of sessions that ended due to a user clicking on an AdSense ad.
  * `User Defined Value` (STRING): The value provided when you define custom user segments for your property.

``` clojure
{ :met "ch0:ga:adsenseExits"
  :dim "ga:userDefinedValue"
  :per "last_1_month"}
```


#### AdSense eCPM by Destination Page
  * `AdSense eCPM` (CURRENCY): The estimated cost per thousand page impressions. It is your AdSense Revenue per 1000 page impressions.
  * Calculated by *ga:adsenseRevenue/(ga:adsensePageImpressions/1000)*
  * `Destination Page` (STRING): A page that the user visited after performing an internal search on your property.

``` clojure
{ :met "ch0:ga:adsenseECPM"
  :dim "ga:searchDestinationPage"
  :per "last_1_month"}
```


#### AdSense Ad Units Viewed by Goal Previous Step - 2
  * `AdSense Ad Units Viewed` (INTEGER): The number of AdSense ad units viewed. An Ad unit is a set of ads displayed as a result of one piece of the AdSense ad code. Details: https://support.google.com/adsense/answer/32715?hl=en
  * `Goal Previous Step - 2` (STRING): The page path or screen name that matched any destination type goal, two steps prior to the goal completion location.

``` clojure
{ :met "ch0:ga:adsenseAdUnitsViewed"
  :dim "ga:goalPreviousStep2"
  :per "last_1_month"}
```


#### AdSense CTR by Count of Sessions
  * `AdSense CTR` (PERCENT): The percentage of page impressions that resulted in a click on an AdSense ad.
  * Calculated by *ga:adsenseAdsClicks/ga:adsensePageImpressions*
  * `Count of Sessions` (STRING): The session index for a user to your property. Each session from a unique user will get its own incremental index starting from 1 for the first session. Subsequent sessions do not change previous session indicies. For example, if a certain user has 4 sessions to your website, sessionCount for that user will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:adsenseCTR"
  :dim "ga:sessionCount"
  :per "last_1_month"}
```

### Page Tracking


#### Exits by Page path level 3
  * `Exits` (INTEGER): The number of exits from your property.
  * `Page path level 3` (STRING): This dimension rolls up all the page paths in the third hierarchical level in pagePath.

``` clojure
{ :met "ch0:ga:exits"
  :dim "ga:pagePathLevel3"
  :per "last_1_month"}
```


#### Organic Searches by Page path level 2
  * `Organic Searches` (INTEGER): The number of organic searches that happened within a session. This metric is search engine agnostic.
  * `Page path level 2` (STRING): This dimension rolls up all the page paths in the second hierarchical level in pagePath.

``` clojure
{ :met "ch0:ga:organicSearches"
  :dim "ga:pagePathLevel2"
  :per "last_1_month"}
```


#### Quantity by Page
  * `Quantity` (INTEGER): The total number of items purchased. For example, if users purchase 2 frisbees and 5 tennis balls, 7 items have been purchased.
  * `Page` (STRING): A page on your website specified by path and/or query parameters. Use in conjunction with hostname to get the full URL of the page.

``` clojure
{ :met "ch0:ga:itemQuantity"
  :dim "ga:pagePath"
  :per "last_1_month"}
```


#### Page Value by Next Page Path
  * `Page Value` (CURRENCY): The average value of this page or set of pages. Page Value is (ga:transactionRevenue + ga:goalValueAll) / ga:uniquePageviews (for the page or set of pages).
  * `Next Page Path` (STRING): A page on your website that was visited after another page on your website. Typically used with the previousPagePath dimension.

``` clojure
{ :met "ch0:ga:pageValue"
  :dim "ga:nextPagePath"
  :per "last_1_month"}
```


#### Pages / Session by Page Depth
  * `Pages / Session` (FLOAT): The average number of pages viewed during a session on your property. Repeated views of a single page are counted.
  * Calculated by *ga:pageviews / ga:sessions*
  * `Page Depth` (STRING): The number of pages visited by users during a session. The value is a histogram that counts pageviews across a range of possible values. In this calculation, all sessions will have at least one pageview, and some percentage of sessions will have more.

``` clojure
{ :met "ch0:ga:pageviewsPerSession"
  :dim "ga:pageDepth"
  :per "last_1_month"}
```


#### Pageviews by Page path level 4
  * `Pageviews` (INTEGER): The total number of pageviews for your property.
  * `Page path level 4` (STRING): This dimension rolls up all the page paths into hierarchical levels. Up to 4 pagePath levels maybe specified. All additional levels in the pagePath hierarchy are also rolled up in this dimension.

``` clojure
{ :met "ch0:ga:pageviews"
  :dim "ga:pagePathLevel4"
  :per "last_1_month"}
```


#### Entrances / Pageviews by Landing Page
  * `Entrances / Pageviews` (PERCENT): The percentage of pageviews in which this page was the entrance.
  * Calculated by *ga:entrances / ga:pageviews*
  * `Landing Page` (STRING): The first page in a user's session, or landing page.

``` clojure
{ :met "ch0:ga:entranceRate"
  :dim "ga:landingPagePath"
  :per "last_1_month"}
```


#### Unique Pageviews by Hostname
  * `Unique Pageviews` (INTEGER): The number of different (unique) pages within a session. This takes into both the pagePath and pageTitle to determine uniqueness.
  * `Hostname` (STRING): The hostname from which the tracking request was made.

``` clojure
{ :met "ch0:ga:uniquePageviews"
  :dim "ga:hostname"
  :per "last_1_month"}
```


#### Time on Page by Previous Page Path
  * `Time on Page` (TIME): How long a user spent on a particular page in seconds. Calculated by subtracting the initial view time for a particular page from the initial view time for a subsequent page. Thus, this metric does not apply to exit pages for your property.
  * `Previous Page Path` (STRING): A page on your property that was visited before another page on the same property. Typically used with the pagePath dimension.

``` clojure
{ :met "ch0:ga:timeOnPage"
  :dim "ga:previousPagePath"
  :per "last_1_month"}
```


#### Avg. Time on Page by Exit Page
  * `Avg. Time on Page` (TIME): The average amount of time users spent viewing this page or a set of pages.
  * Calculated by *ga:timeOnPage / (ga:pageviews - ga:exits)*
  * `Exit Page` (STRING): The last page in a user's session, or exit page.

``` clojure
{ :met "ch0:ga:avgTimeOnPage"
  :dim "ga:exitPagePath"
  :per "last_1_month"}
```


#### Search Refinements by Page Title
  * `Search Refinements` (INTEGER): The total number of times a refinement (transition) occurs between internal search keywords within a session. For example if the sequence of keywords is: "shoes", "shoes", "pants", "pants", this metric will be one because the transition between "shoes" and "pants" is different.
  * `Page Title` (STRING): The title of a page. Keep in mind that multiple pages might have the same page title.

``` clojure
{ :met "ch0:ga:searchRefinements"
  :dim "ga:pageTitle"
  :per "last_1_month"}
```


#### Entrances by Page path level 1
  * `Entrances` (INTEGER): The number of entrances to your property measured as the first pageview in a session. Typically used with landingPagePath
  * `Page path level 1` (STRING): This dimension rolls up all the page paths in the first hierarchical level in pagePath.

``` clojure
{ :met "ch0:ga:entrances"
  :dim "ga:pagePathLevel1"
  :per "last_1_month"}
```


#### % Exit by Second Page
  * `% Exit` (PERCENT): The percentage of exits from your property that occurred out of the total page views.
  * Calculated by *ga:exits / (ga:pageviews + ga:screenviews)*
  * `Second Page` (STRING): The second page in a user's session.

``` clojure
{ :met "ch0:ga:exitRate"
  :dim "ga:secondPagePath"
  :per "last_1_month"}
```

### Custom Variables or Columns


#### Custom Metric  Value by Custom Dimension 
  * `Custom Metric  Value` (INTEGER): The name of the requested custom metric, where XX refers the number/index of the custom metric.
  * `Custom Dimension ` (STRING): The name of the requested custom dimension, where XX refers the number/index of the custom dimension.

``` clojure
{ :met "ch0:ga:metricXX"
  :dim "ga:dimensionXX"
  :per "last_1_month"}
```


#### Page Download Time (ms) by Custom Variable (Value 01)
  * `Page Download Time (ms)` (INTEGER): The total amount of time (in milliseconds) to download this page among all samples.
  * `Custom Variable (Value 01)` (STRING): The value for the requested custom variable.

``` clojure
{ :met "ch0:ga:pageDownloadTime"
  :dim "ga:customVarValueXX"
  :per "last_1_month"}
```


#### CPM by Custom Variable (Key 1)
  * `CPM` (CURRENCY): Cost per thousand impressions.
  * Calculated by *ga:adCost / (ga:impressions / 1000)*
  * `Custom Variable (Key 1)` (STRING): The name for the requested custom variable.

``` clojure
{ :met "ch0:ga:CPM"
  :dim "ga:customVarNameXX"
  :per "last_1_month"}
```

### Audience


#### Sessions by Gender
  * `Sessions` (INTEGER): Counts the total number of sessions.
  * `Gender` (STRING): Gender of user.

``` clojure
{ :met "ch0:ga:sessions"
  :dim "ga:userGender"
  :per "last_1_month"}
```


#### DOM Latency Metrics Sample by Other Category
  * `DOM Latency Metrics Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the averages for site speed DOM metrics. This metric is used in the avgDomContentLoadedTime and avgDomInteractiveTime calculations.
  * `Other Category` (STRING): Indicates that users are more likely to be interested in learning about the specified category, and more likely to be ready to purchase.

``` clojure
{ :met "ch0:ga:domLatencyMetricsSample"
  :dim "ga:interestOtherCategory"
  :per "last_1_month"}
```


#### Avg. Document Content Loaded Time (sec) by In-market Segment
  * `Avg. Document Content Loaded Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document.
  * Calculated by *(ga:domContentLoadedTime / ga:domLatencyMetricsSample / 1000)*
  * `In-market Segment` (STRING): Indicates that users are more likely to be ready to purchase products or services in the specified category.

``` clojure
{ :met "ch0:ga:avgDomContentLoadedTime"
  :dim "ga:interestInMarketCategory"
  :per "last_1_month"}
```


#### Local Shipping by Affinity Category (reach)
  * `Local Shipping` (CURRENCY): Transaction shipping cost in local currency.
  * `Affinity Category (reach)` (STRING): Indicates that users are more likely to be interested in learning about the specified category.

``` clojure
{ :met "ch0:ga:localTransactionShipping"
  :dim "ga:interestAffinityCategory"
  :per "last_1_month"}
```


#### Local Product Revenue by Age
  * `Local Product Revenue` (CURRENCY): Product revenue in local currency.
  * `Age` (STRING): Age bracket of user.

``` clojure
{ :met "ch0:ga:localItemRevenue"
  :dim "ga:userAgeBracket"
  :per "last_1_month"}
```

### Goal Conversions


#### Goal 1 Abandoned Funnels by Social User Handle
  * `Goal 1 Abandoned Funnels` (INTEGER): The number of times users started conversion activity on the requested goal number without actually completing it.
  * Calculated by *(ga:goalXXStarts - ga:goalXXCompletions)*
  * `Social User Handle` (STRING): For a social data hub activity, this value represents the social network handle (e.g. name or ID) of the user who initiated the social activity.

``` clojure
{ :met "ch0:ga:goalXXAbandons"
  :dim "ga:socialActivityUserHandle"
  :per "last_1_month"}
```


#### Goal 1 Conversion Rate by Goal Completion Location
  * `Goal 1 Conversion Rate` (PERCENT): The percentage of sessions which resulted in a conversion to the requested goal number.
  * Calculated by *ga:goalXXCompletions / ga:sessions*
  * `Goal Completion Location` (STRING): The page path or screen name that matched any destination type goal completion.

``` clojure
{ :met "ch0:ga:goalXXConversionRate"
  :dim "ga:goalCompletionLocation"
  :per "last_1_month"}
```


#### Goal Completions by AdWords Creative ID
  * `Goal Completions` (INTEGER): The total number of completions for all goals defined for your profile.
  * `AdWords Creative ID` (STRING): A string. Corresponds to AdWords API Ad.id.

``` clojure
{ :met "ch0:ga:goalCompletionsAll"
  :dim "ga:adwordsCreativeID"
  :per "last_1_month"}
```


#### Per Session Goal Value by Goal Previous Step - 1
  * `Per Session Goal Value` (CURRENCY): The average goal value of a session on your property.
  * Calculated by *ga:goalValueAll / ga:sessions*
  * `Goal Previous Step - 1` (STRING): The page path or screen name that matched any destination type goal, one step prior to the goal completion location.

``` clojure
{ :met "ch0:ga:goalValuePerSession"
  :dim "ga:goalPreviousStep1"
  :per "last_1_month"}
```


#### Goal Starts by Longitude
  * `Goal Starts` (INTEGER): The total number of starts for all goals defined for your profile.
  * `Longitude` (STRING): The approximate longitude of the user's city. Derived from IP address. Locations east of the meridian are represented by positive values and locations west of the meridian by negative values.

``` clojure
{ :met "ch0:ga:goalStartsAll"
  :dim "ga:longitude"
  :per "last_1_month"}
```


#### Total Abandonment Rate by Sessions to Transaction
  * `Total Abandonment Rate` (PERCENT): The rate at which goals were abandoned.
  * Calculated by *((ga:goalStartsAll - ga:goalCompletionsAll)) / (ga:goalStartsAll)*
  * `Sessions to Transaction` (STRING): The number of sessions between users' purchases and the related campaigns that lead to the purchases.

``` clojure
{ :met "ch0:ga:goalAbandonRateAll"
  :dim "ga:sessionsToTransaction"
  :per "last_1_month"}
```


#### Abandoned Funnels by Event Action
  * `Abandoned Funnels` (INTEGER): The overall number of times users started goals without actually completing them.
  * Calculated by *(ga:goalStartsAll - ga:goalCompletionsAll)*
  * `Event Action` (STRING): The action of the event.

``` clojure
{ :met "ch0:ga:goalAbandonsAll"
  :dim "ga:eventAction"
  :per "last_1_month"}
```


#### Goal 1 Value by Language
  * `Goal 1 Value` (CURRENCY): The total numeric value for the requested goal number.
  * `Language` (STRING): The language provided by the HTTP Request for the browser. Values are given as an ISO-639 code (e.g. en-gb for British English).

``` clojure
{ :met "ch0:ga:goalXXValue"
  :dim "ga:language"
  :per "last_1_month"}
```


#### Goal 1 Completions by Age
  * `Goal 1 Completions` (INTEGER): The total number of completions for the requested goal number.
  * `Age` (STRING): Age bracket of user.

``` clojure
{ :met "ch0:ga:goalXXCompletions"
  :dim "ga:visitorAgeBracket"
  :per "last_1_month"}
```


#### Goal Value by Goal Previous Step - 3
  * `Goal Value` (CURRENCY): The total numeric value for all goals defined for your profile.
  * `Goal Previous Step - 3` (STRING): The page path or screen name that matched any destination type goal, three steps prior to the goal completion location.

``` clojure
{ :met "ch0:ga:goalValueAll"
  :dim "ga:goalPreviousStep3"
  :per "last_1_month"}
```


#### Goal 1 Abandonment Rate by Count of Sessions
  * `Goal 1 Abandonment Rate` (PERCENT): The rate at which the requested goal number was abandoned.
  * Calculated by *((ga:goalXXStarts - ga:goalXXCompletions)) / (ga:goalXXStarts)*
  * `Count of Sessions` (STRING): The session index for a user to your property. Each session from a unique user will get its own incremental index starting from 1 for the first session. Subsequent sessions do not change previous session indicies. For example, if a certain user has 4 sessions to your website, sessionCount for that user will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:goalXXAbandonRate"
  :dim "ga:sessionCount"
  :per "last_1_month"}
```


#### Goal Conversion Rate by Month Index
  * `Goal Conversion Rate` (PERCENT): The percentage of sessions which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:sessions*
  * `Month Index` (STRING): Index for each month in the specified date range. Index for the first month in the date range is 0, 1 for the second month, and so on. The index corresponds to month entries.

``` clojure
{ :met "ch0:ga:goalConversionRateAll"
  :dim "ga:nthMonth"
  :per "last_1_month"}
```


#### Goal 1 Starts by Social Source Referral
  * `Goal 1 Starts` (INTEGER): The total number of starts for the requested goal number.
  * `Social Source Referral` (STRING): Indicates sessions that arrived to the property from a social source. The possible values are Yes or No where the first letter is capitalized.

``` clojure
{ :met "ch0:ga:goalXXStarts"
  :dim "ga:hasSocialSourceReferral"
  :per "last_1_month"}
```

### Internal Search


#### Results Pageviews / Search by Refined Keyword
  * `Results Pageviews / Search` (FLOAT): The average number of times people viewed a search results page after performing a search.
  * Calculated by *ga:searchResultViews / ga:searchUniques*
  * `Refined Keyword` (STRING): Subsequent keyword search terms or strings entered by users after a given initial string search.

``` clojure
{ :met "ch0:ga:avgSearchResultViews"
  :dim "ga:searchKeywordRefinement"
  :per "last_1_month"}
```


#### Search Depth by App Version
  * `Search Depth` (FLOAT): The average number of pages people viewed after performing a search on your property.
  * Calculated by *ga:searchDepth / ga:searchUniques*
  * `App Version` (STRING): The version of the application.

``` clojure
{ :met "ch0:ga:avgSearchDepth"
  :dim "ga:appVersion"
  :per "last_1_month"}
```


#### Total Unique Searches by Originating Social Action
  * `Total Unique Searches` (INTEGER): The total number of unique keywords from internal searches within a session. For example if "shoes" was searched for 3 times in a session, it will be only counted once.
  * `Originating Social Action` (STRING): For a social data hub activity, this value represents the type of social action associated with the activity (e.g. vote, comment, +1, etc.).

``` clojure
{ :met "ch0:ga:searchUniques"
  :dim "ga:socialActivityAction"
  :per "last_1_month"}
```


#### Search Depth by Site Search Status
  * `Search Depth` (INTEGER): The average number of subsequent page views made on your property after a use of your internal search feature.
  * `Site Search Status` (STRING): A boolean to distinguish whether internal search was used in a session. Values are Visits With Site Search and Visits Without Site Search.

``` clojure
{ :met "ch0:ga:searchDepth"
  :dim "ga:searchUsed"
  :per "last_1_month"}
```


#### Per Search Goal Value by Destination Page
  * `Per Search Goal Value` (CURRENCY): The average goal value of a search on your property.
  * Calculated by *ga:goalValueAll / ga:searchUniques*
  * `Destination Page` (STRING): A page that the user visited after performing an internal search on your property.

``` clojure
{ :met "ch0:ga:goalValueAllPerSearch"
  :dim "ga:searchDestinationPage"
  :per "last_1_month"}
```


#### Results Pageviews by Event Action
  * `Results Pageviews` (INTEGER): The number of times a search result page was viewed after performing a search.
  * `Event Action` (STRING): The action of the event.

``` clojure
{ :met "ch0:ga:searchResultViews"
  :dim "ga:eventAction"
  :per "last_1_month"}
```


#### Time after Search by Placement Domain
  * `Time after Search` (TIME): The session duration on your property where a use of your internal search feature occurred.
  * `Placement Domain` (STRING): The domains where your ads on the content network were placed.

``` clojure
{ :met "ch0:ga:searchDuration"
  :dim "ga:adPlacementDomain"
  :per "last_1_month"}
```


#### Sessions with Search by Flash Version
  * `Sessions with Search` (INTEGER): The total number of sessions that included an internal search
  * `Flash Version` (STRING): The versions of Flash supported by users' browsers, including minor versions.

``` clojure
{ :met "ch0:ga:searchSessions"
  :dim "ga:flashVersion"
  :per "last_1_month"}
```


#### Site Search Goal 1 Conversion Rate by Referral Path
  * `Site Search Goal 1 Conversion Rate` (PERCENT): The percentage of search sessions (i.e., sessions that included at least one search) which resulted in a conversion to the requested goal number.
  * Calculated by *ga:goalXXCompletions / ga:searchUniques*
  * `Referral Path` (STRING): The path of the referring URL (e.g. document.referrer). If someone places a link to your property on their website, this element contains the path of the page that contains the referring link.

``` clojure
{ :met "ch0:ga:searchGoalXXConversionRate"
  :dim "ga:referralPath"
  :per "last_1_month"}
```


#### Site Search Goal Conversion Rate by Day of Week Name
  * `Site Search Goal Conversion Rate` (PERCENT): The percentage of search sessions (i.e., sessions that included at least one search) which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:searchUniques*
  * `Day of Week Name` (STRING): The name of the day of the week (in English).

``` clojure
{ :met "ch0:ga:searchGoalConversionRateAll"
  :dim "ga:dayOfWeekName"
  :per "last_1_month"}
```


#### Search Exits by Screen Colors
  * `Search Exits` (INTEGER): The number of exits on your site that occurred following a search result from your internal search feature.
  * `Screen Colors` (STRING): The color depth of users' monitors, as retrieved from the DOM of the user's browser. For example 4-bit, 8-bit, 24-bit, or undefined-bit.

``` clojure
{ :met "ch0:ga:searchExits"
  :dim "ga:screenColors"
  :per "last_1_month"}
```


#### Time after Search by Hour Index
  * `Time after Search` (TIME): The average amount of time people spent on your property after searching.
  * Calculated by *ga:searchDuration / ga:searchUniques*
  * `Hour Index` (STRING): Index for each hour in the specified date range. Index for the first hour of first day (i.e., start-date) in the date range is 0, 1 for the next hour, and so on.

``` clojure
{ :met "ch0:ga:avgSearchDuration"
  :dim "ga:nthHour"
  :per "last_1_month"}
```


#### % Sessions with Search by Mobile Input Selector
  * `% Sessions with Search` (PERCENT): The percentage of sessions with search.
  * Calculated by *ga:searchSessions / ga:sessions*
  * `Mobile Input Selector` (STRING): Selector used on the mobile device (e.g.: touchscreen, joystick, clickwheel, stylus).

``` clojure
{ :met "ch0:ga:percentSessionsWithSearch"
  :dim "ga:mobileInputSelector"
  :per "last_1_month"}
```


#### Search Refinements by Social Activity Post
  * `Search Refinements` (INTEGER): The total number of times a refinement (transition) occurs between internal search keywords within a session. For example if the sequence of keywords is: "shoes", "shoes", "pants", "pants", this metric will be one because the transition between "shoes" and "pants" is different.
  * `Social Activity Post` (STRING): For a social data hub activity, this value represents the content of the social activity posted by the social network user (e.g. The message content of a Google+ post)

``` clojure
{ :met "ch0:ga:searchRefinements"
  :dim "ga:socialActivityPost"
  :per "last_1_month"}
```


#### % Search Exits by Start Page
  * `% Search Exits` (PERCENT): The percentage of searches that resulted in an immediate exit from your property.
  * Calculated by *ga:searchExits / ga:searchUniques*
  * `Start Page` (STRING): A page where the user initiated an internal search on your property.

``` clojure
{ :met "ch0:ga:searchExitRate"
  :dim "ga:searchStartPage"
  :per "last_1_month"}
```


#### % Search Refinements by Search Term
  * `% Search Refinements` (PERCENT): The percentage of number of times a refinement (i.e., transition) occurs between internal search keywords within a session.
  * Calculated by *ga:searchRefinements / ga:searchResultViews*
  * `Search Term` (STRING): Search terms used by users within your property.

``` clojure
{ :met "ch0:ga:percentSearchRefinements"
  :dim "ga:searchKeyword"
  :per "last_1_month"}
```

### User Timings


#### Avg. User Timing (sec) by Timing Variable
  * `Avg. User Timing (sec)` (FLOAT): The average amount of elapsed time.
  * Calculated by *(ga:userTimingValue / ga:userTimingSample / 1000)*
  * `Timing Variable` (STRING): A value that can be used to add flexibility in visualizing user timings in the reports.

``` clojure
{ :met "ch0:ga:avgUserTimingValue"
  :dim "ga:userTimingVariable"
  :per "last_1_month"}
```


#### User Timing (ms) by Timing Category
  * `User Timing (ms)` (INTEGER): The total number of milliseconds for a user timing.
  * `Timing Category` (STRING): A string for categorizing all user timing variables into logical groups for easier reporting purposes.

``` clojure
{ :met "ch0:ga:userTimingValue"
  :dim "ga:userTimingCategory"
  :per "last_1_month"}
```


#### User Timing Sample by Timing Label
  * `User Timing Sample` (INTEGER): The number of hits that were sent for a particular userTimingCategory, userTimingLabel, and userTimingVariable.
  * `Timing Label` (STRING): The name of the resource's action being tracked.

``` clojure
{ :met "ch0:ga:userTimingSample"
  :dim "ga:userTimingLabel"
  :per "last_1_month"}
```

### Event Tracking


#### Avg. Value by Event Category
  * `Avg. Value` (FLOAT): The average value of an event.
  * Calculated by *ga:eventValue / ga:totalEvents*
  * `Event Category` (STRING): The category of the event.

``` clojure
{ :met "ch0:ga:avgEventValue"
  :dim "ga:eventCategory"
  :per "last_1_month"}
```


#### Events / Session by Event Action
  * `Events / Session` (FLOAT): The average number of events per session with event.
  * Calculated by *ga:totalEvents / ga:sessionsWithEvent*
  * `Event Action` (STRING): The action of the event.

``` clojure
{ :met "ch0:ga:eventsPerSessionWithEvent"
  :dim "ga:eventAction"
  :per "last_1_month"}
```


#### Unique Events by Refined Keyword
  * `Unique Events` (INTEGER): The total number of unique events for the profile, across all categories.
  * `Refined Keyword` (STRING): Subsequent keyword search terms or strings entered by users after a given initial string search.

``` clojure
{ :met "ch0:ga:uniqueEvents"
  :dim "ga:searchKeywordRefinement"
  :per "last_1_month"}
```


#### Event Value by Language
  * `Event Value` (INTEGER): The total value of events for the profile.
  * `Language` (STRING): The language provided by the HTTP Request for the browser. Values are given as an ISO-639 code (e.g. en-gb for British English).

``` clojure
{ :met "ch0:ga:eventValue"
  :dim "ga:language"
  :per "last_1_month"}
```


#### Total Events by Event Category
  * `Total Events` (INTEGER): The total number of events for the profile, across all categories.
  * `Event Category` (STRING): The category of the event.

``` clojure
{ :met "ch0:ga:totalEvents"
  :dim "ga:eventCategory"
  :per "last_1_month"}
```


#### Sessions with Event by Social Network
  * `Sessions with Event` (INTEGER): The total number of sessions with events.
  * `Social Network` (STRING): Name of the social network. This can be related to the referring social network for traffic sources, or to the social network for social data hub activities. E.g. Google+, Blogger, etc.

``` clojure
{ :met "ch0:ga:sessionsWithEvent"
  :dim "ga:socialNetwork"
  :per "last_1_month"}
```

### App Tracking


#### Screen Views by Landing Screen
  * `Screen Views` (INTEGER): The total number of screenviews.
  * `Landing Screen` (STRING): The name of the first screen viewed.

``` clojure
{ :met "ch0:ga:screenviews"
  :dim "ga:landingScreenName"
  :per "last_1_month"}
```


#### Unique Screen Views by App Installer ID
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `App Installer ID` (STRING): ID of the installer (e.g., Google Play Store) from which the app was downloaded. By default, the app installer id is set based on the PackageManager#getInstallerPackageName method.

``` clojure
{ :met "ch0:ga:uniqueScreenviews"
  :dim "ga:appInstallerId"
  :per "last_1_month"}
```


#### Screens / Session by Screen Depth
  * `Screens / Session` (FLOAT): The average number of screenviews per session.
  * Calculated by *ga:screenviews / ga:sessions*
  * `Screen Depth` (STRING): The number of screenviews per session reported as a string. Can be useful for historgrams.

``` clojure
{ :met "ch0:ga:screenviewsPerSession"
  :dim "ga:screenDepth"
  :per "last_1_month"}
```


#### Time on Screen by App Name
  * `Time on Screen` (TIME): The time spent viewing the current screen.
  * `App Name` (STRING): The name of the application.

``` clojure
{ :met "ch0:ga:timeOnScreen"
  :dim "ga:appName"
  :per "last_1_month"}
```


#### Avg. Time on Screen by Screen Name
  * `Avg. Time on Screen` (TIME): The average amount of time users spent on a screen in seconds.
  * `Screen Name` (STRING): The name of the screen.

``` clojure
{ :met "ch0:ga:avgScreenviewDuration"
  :dim "ga:screenName"
  :per "last_1_month"}
```


#### AdSense Exits by Exit Screen
  * `AdSense Exits` (INTEGER): The number of sessions that ended due to a user clicking on an AdSense ad.
  * `Exit Screen` (STRING): The name of the screen when the user exited the application.

``` clojure
{ :met "ch0:ga:adsenseExits"
  :dim "ga:exitScreenName"
  :per "last_1_month"}
```


#### Exceptions by App Version
  * `Exceptions` (INTEGER): The number of exceptions that were sent to Google Analytics.
  * `App Version` (STRING): The version of the application.

``` clojure
{ :met "ch0:ga:exceptions"
  :dim "ga:appVersion"
  :per "last_1_month"}
```


#### Exits by App ID
  * `Exits` (INTEGER): The number of exits from your property.
  * `App ID` (STRING): The ID of the application.

``` clojure
{ :met "ch0:ga:exits"
  :dim "ga:appId"
  :per "last_1_month"}
```

### Ecommerce


#### Tax by Originating Social Action
  * `Tax` (CURRENCY): The total amount of tax.
  * `Originating Social Action` (STRING): For a social data hub activity, this value represents the type of social action associated with the activity (e.g. vote, comment, +1, etc.).

``` clojure
{ :met "ch0:ga:transactionTax"
  :dim "ga:socialActivityAction"
  :per "last_1_month"}
```


#### Local Product Revenue by Sessions to Transaction
  * `Local Product Revenue` (CURRENCY): Product revenue in local currency.
  * `Sessions to Transaction` (STRING): The number of sessions between users' purchases and the related campaigns that lead to the purchases.

``` clojure
{ :met "ch0:ga:localItemRevenue"
  :dim "ga:sessionsToTransaction"
  :per "last_1_month"}
```


#### Shipping by Transaction
  * `Shipping` (CURRENCY): The total cost of shipping.
  * `Transaction` (STRING): The transaction ID for the shopping cart purchase as supplied by your ecommerce tracking method.

``` clojure
{ :met "ch0:ga:transactionShipping"
  :dim "ga:transactionId"
  :per "last_1_month"}
```


#### Average Price by User Type
  * `Average Price` (CURRENCY): The average revenue per item.
  * Calculated by *ga:itemRevenue / ga:itemQuantity*
  * `User Type` (STRING): A boolean indicating if a user is new or returning. Possible values: New Visitor, Returning Visitor.

``` clojure
{ :met "ch0:ga:revenuePerItem"
  :dim "ga:userType"
  :per "last_1_month"}
```


#### Total Value by Day of Week Name
  * `Total Value` (CURRENCY): Total value for your property (including total revenue and total goal value).
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll)*
  * `Day of Week Name` (STRING): The name of the day of the week (in English).

``` clojure
{ :met "ch0:ga:totalValue"
  :dim "ga:dayOfWeekName"
  :per "last_1_month"}
```


#### Average QTY by Social Network
  * `Average QTY` (FLOAT): The average quantity of this item (or group of items) sold per purchase.
  * Calculated by *ga:itemQuantity / ga:uniquePurchases*
  * `Social Network` (STRING): Name of the social network. This can be related to the referring social network for traffic sources, or to the social network for social data hub activities. E.g. Google+, Blogger, etc.

``` clojure
{ :met "ch0:ga:itemsPerPurchase"
  :dim "ga:socialNetwork"
  :per "last_1_month"}
```


#### Quantity by Month Index
  * `Quantity` (INTEGER): The total number of items purchased. For example, if users purchase 2 frisbees and 5 tennis balls, 7 items have been purchased.
  * `Month Index` (STRING): Index for each month in the specified date range. Index for the first month in the date range is 0, 1 for the second month, and so on. The index corresponds to month entries.

``` clojure
{ :met "ch0:ga:itemQuantity"
  :dim "ga:nthMonth"
  :per "last_1_month"}
```


#### Unique Purchases by Product Category
  * `Unique Purchases` (INTEGER): The number of product sets purchased. For example, if users purchase 2 frisbees and 5 tennis balls from your site, 2 unique products have been purchased.
  * `Product Category` (STRING): Any product variations (size, color) for purchased items as supplied by your ecommerce application.

``` clojure
{ :met "ch0:ga:uniquePurchases"
  :dim "ga:productCategory"
  :per "last_1_month"}
```


#### Transactions by Goal Previous Step - 1
  * `Transactions` (INTEGER): The total number of transactions.
  * `Goal Previous Step - 1` (STRING): The page path or screen name that matched any destination type goal, one step prior to the goal completion location.

``` clojure
{ :met "ch0:ga:transactions"
  :dim "ga:goalPreviousStep1"
  :per "last_1_month"}
```


#### Local Shipping by Gender
  * `Local Shipping` (CURRENCY): Transaction shipping cost in local currency.
  * `Gender` (STRING): Gender of user.

``` clojure
{ :met "ch0:ga:localTransactionShipping"
  :dim "ga:userGender"
  :per "last_1_month"}
```


#### Ecommerce Conversion Rate by Product
  * `Ecommerce Conversion Rate` (PERCENT): The average number of transactions for a session on your property.
  * Calculated by *ga:transactions / ga:sessions*
  * `Product` (STRING): The product name for purchased items as supplied by your ecommerce tracking application.

``` clojure
{ :met "ch0:ga:transactionsPerSession"
  :dim "ga:productName"
  :per "last_1_month"}
```


#### Product Revenue by Currency Code
  * `Product Revenue` (CURRENCY): The total revenue from purchased product items on your property.
  * `Currency Code` (STRING): The local currency code of the transaction based on ISO 4217 standard.

``` clojure
{ :met "ch0:ga:itemRevenue"
  :dim "ga:currencyCode"
  :per "last_1_month"}
```


#### Local Revenue by Product SKU
  * `Local Revenue` (CURRENCY): Transaction revenue in local currency.
  * `Product SKU` (STRING): The product sku for purchased items as you have defined them in your ecommerce tracking application.

``` clojure
{ :met "ch0:ga:localTransactionRevenue"
  :dim "ga:productSku"
  :per "last_1_month"}
```


#### Per Session Value by Hour of Day
  * `Per Session Value` (CURRENCY): Average transaction revenue for a session on your property.
  * Calculated by *ga:transactionRevenue / ga:sessions*
  * `Hour of Day` (STRING): Combined values of ga:date and ga:hour.

``` clojure
{ :met "ch0:ga:transactionRevenuePerSession"
  :dim "ga:dateHour"
  :per "last_1_month"}
```


#### Average Order Value by Source / Medium
  * `Average Order Value` (CURRENCY): The average revenue for an e-commerce transaction.
  * Calculated by *ga:transactionRevenue / ga:transactions*
  * `Source / Medium` (STRING): Combined values of ga:source and ga:medium.

``` clojure
{ :met "ch0:ga:revenuePerTransaction"
  :dim "ga:sourceMedium"
  :per "last_1_month"}
```


#### Local Tax by Exit Page
  * `Local Tax` (CURRENCY): Transaction tax in local currency.
  * `Exit Page` (STRING): The last page in a user's session, or exit page.

``` clojure
{ :met "ch0:ga:localTransactionTax"
  :dim "ga:exitPagePath"
  :per "last_1_month"}
```


#### Revenue by Affiliation
  * `Revenue` (CURRENCY): The total sale revenue provided in the transaction excluding shipping and tax.
  * `Affiliation` (STRING): Typically used to designate a supplying company or brick and mortar location; product affiliation.

``` clojure
{ :met "ch0:ga:transactionRevenue"
  :dim "ga:affiliation"
  :per "last_1_month"}
```

### Social Activities


#### Search Depth by Social Activity Post
  * `Search Depth` (FLOAT): The average number of pages people viewed after performing a search on your property.
  * Calculated by *ga:searchDepth / ga:searchUniques*
  * `Social Activity Post` (STRING): For a social data hub activity, this value represents the content of the social activity posted by the social network user (e.g. The message content of a Google+ post)

``` clojure
{ :met "ch0:ga:avgSearchDepth"
  :dim "ga:socialActivityPost"
  :per "last_1_month"}
```


#### Unique Screen Views by Display Name
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Display Name` (STRING): For a social data hub activity, this value represents the title of the social activity posted by the social network user.

``` clojure
{ :met "ch0:ga:uniqueScreenviews"
  :dim "ga:socialActivityDisplayName"
  :per "last_1_month"}
```


#### AdSense CTR by Originating Social Action
  * `AdSense CTR` (PERCENT): The percentage of page impressions that resulted in a click on an AdSense ad.
  * Calculated by *ga:adsenseAdsClicks/ga:adsensePageImpressions*
  * `Originating Social Action` (STRING): For a social data hub activity, this value represents the type of social action associated with the activity (e.g. vote, comment, +1, etc.).

``` clojure
{ :met "ch0:ga:adsenseCTR"
  :dim "ga:socialActivityAction"
  :per "last_1_month"}
```


#### Total Abandonment Rate by Social Tags Summary
  * `Total Abandonment Rate` (PERCENT): The rate at which goals were abandoned.
  * Calculated by *((ga:goalStartsAll - ga:goalCompletionsAll)) / (ga:goalStartsAll)*
  * `Social Tags Summary` (STRING): For a social data hub activity, this is a comma-separated set of tags associated with the social activity.

``` clojure
{ :met "ch0:ga:goalAbandonRateAll"
  :dim "ga:socialActivityTagsSummary"
  :per "last_1_month"}
```


#### Total Value by Shared URL
  * `Total Value` (CURRENCY): Total value for your property (including total revenue and total goal value).
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll)*
  * `Shared URL` (STRING): For a social data hub activity, this value represents the URL shared by the associated social network user.

``` clojure
{ :met "ch0:ga:totalValue"
  :dim "ga:socialActivityContentUrl"
  :per "last_1_month"}
```


#### Quantity by User Photo URL
  * `Quantity` (INTEGER): The total number of items purchased. For example, if users purchase 2 frisbees and 5 tennis balls, 7 items have been purchased.
  * `User Photo URL` (STRING): For a social data hub activity, this value represents the URL of the photo associated with the user's social network profile.

``` clojure
{ :met "ch0:ga:itemQuantity"
  :dim "ga:socialActivityUserPhotoUrl"
  :per "last_1_month"}
```


#### Page Value by Social Activity Timestamp
  * `Page Value` (CURRENCY): The average value of this page or set of pages. Page Value is (ga:transactionRevenue + ga:goalValueAll) / ga:uniquePageviews (for the page or set of pages).
  * `Social Activity Timestamp` (STRING): For a social data hub activity, this value represents when the social activity occurred on the social network.

``` clojure
{ :met "ch0:ga:pageValue"
  :dim "ga:socialActivityTimestamp"
  :per "last_1_month"}
```


#### Data Hub Activities by User Profile URL
  * `Data Hub Activities` (INTEGER): The count of activities where a content URL was shared / mentioned on a social data hub partner network.
  * `User Profile URL` (STRING): For a social data hub activity, this value represents the URL of the associated user's social network profile.

``` clojure
{ :met "ch0:ga:socialActivities"
  :dim "ga:socialActivityUserProfileUrl"
  :per "last_1_month"}
```


#### Server Response Time (ms) by Endorsing URL
  * `Server Response Time (ms)` (INTEGER): The total amount of time (in milliseconds) your server takes to respond to a user request among all samples, including the network time from user's location to your server.
  * `Endorsing URL` (STRING): For a social data hub activity, this value represents the URL of the social activity (e.g. the Google+ post URL, the blog comment URL, etc.)

``` clojure
{ :met "ch0:ga:serverResponseTime"
  :dim "ga:socialActivityEndorsingUrl"
  :per "last_1_month"}
```


#### Avg. Session Duration by Social User Handle
  * `Avg. Session Duration` (TIME): The average duration of user sessions represented in total seconds.
  * Calculated by *ga:sessionDuration / ga:sessions*
  * `Social User Handle` (STRING): For a social data hub activity, this value represents the social network handle (e.g. name or ID) of the user who initiated the social activity.

``` clojure
{ :met "ch0:ga:avgTimeOnSite"
  :dim "ga:socialActivityUserHandle"
  :per "last_1_month"}
```


#### Goal Value by Social Network and Action
  * `Goal Value` (CURRENCY): The total numeric value for all goals defined for your profile.
  * `Social Network and Action` (STRING): For a social data hub activity, this value represents the type of social action and the social network where the activity originated.

``` clojure
{ :met "ch0:ga:goalValueAll"
  :dim "ga:socialActivityNetworkAction"
  :per "last_1_month"}
```

### Social Interactions


#### Unique Social Actions by Social Source and Action
  * `Unique Social Actions` (INTEGER): The number of sessions during which the specified social action(s) occurred at least once. This is based on the the unique combination of socialInteractionNetwork, socialInteractionAction, and socialInteractionTarget.
  * `Social Source and Action` (STRING): For social interactions, a value representing the concatenation of the socialInteractionNetwork and socialInteractionAction action being tracked at this hit level (e.g. Google: +1)

``` clojure
{ :met "ch0:ga:uniqueSocialInteractions"
  :dim "ga:socialInteractionNetworkAction"
  :per "last_1_month"}
```


#### Social Actions by Social Action
  * `Social Actions` (INTEGER): The total number of social interactions on your property.
  * `Social Action` (STRING): For social interactions, a value representing the social action being tracked (e.g. +1, bookmark)

``` clojure
{ :met "ch0:ga:socialInteractions"
  :dim "ga:socialInteractionAction"
  :per "last_1_month"}
```


#### Actions Per Social Session by Social Source
  * `Actions Per Social Session` (FLOAT): The number of social interactions per session on your property.
  * Calculated by *ga:socialInteractions / ga:uniqueSocialInteractions*
  * `Social Source` (STRING): For social interactions, a value representing the social network being tracked.

``` clojure
{ :met "ch0:ga:socialInteractionsPerSession"
  :dim "ga:socialInteractionNetwork"
  :per "last_1_month"}
```


#### Site Search Goal Conversion Rate by Social Entity
  * `Site Search Goal Conversion Rate` (PERCENT): The percentage of search sessions (i.e., sessions that included at least one search) which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:searchUniques*
  * `Social Entity` (STRING): For social interactions, a value representing the URL (or resource) which receives the social network action.

``` clojure
{ :met "ch0:ga:searchGoalConversionRateAll"
  :dim "ga:socialInteractionTarget"
  :per "last_1_month"}
```


#### Crashes / Screen by Social Type
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `Social Type` (STRING): Engagement type. Possible values are "Socially Engaged" or "Not Socially Engaged".

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:socialEngagementType"
  :per "last_1_month"}
```

### Geo Network


#### AdSense CTR by Network Domain
  * `AdSense CTR` (PERCENT): The percentage of page impressions that resulted in a click on an AdSense ad.
  * Calculated by *ga:adsenseAdsClicks/ga:adsensePageImpressions*
  * `Network Domain` (STRING): The domain name of the ISPs used by users to your property. This is derived from the domain name registered to the IP address.

``` clojure
{ :met "ch0:ga:adsenseCTR"
  :dim "ga:networkDomain"
  :per "last_1_month"}
```


#### Actions Per Social Session by City
  * `Actions Per Social Session` (FLOAT): The number of social interactions per session on your property.
  * Calculated by *ga:socialInteractions / ga:uniqueSocialInteractions*
  * `City` (STRING): The cities of property users, derived from IP addresses.

``` clojure
{ :met "ch0:ga:socialInteractionsPerSession"
  :dim "ga:city"
  :per "last_1_month"}
```


#### Transactions by Service Provider
  * `Transactions` (INTEGER): The total number of transactions.
  * `Service Provider` (STRING): The name of service providers used to reach your property. For example, if most users to your website come via the major service providers for cable internet, you will see the names of those cable service providers in this element.

``` clojure
{ :met "ch0:ga:transactions"
  :dim "ga:networkLocation"
  :per "last_1_month"}
```


#### % Sessions with Search by Metro
  * `% Sessions with Search` (PERCENT): The percentage of sessions with search.
  * Calculated by *ga:searchSessions / ga:sessions*
  * `Metro` (STRING): The Designated Market Area (DMA) from where traffic arrived on your property.

``` clojure
{ :met "ch0:ga:percentVisitsWithSearch"
  :dim "ga:metro"
  :per "last_1_month"}
```


#### Unique Screen Views by Continent
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Continent` (STRING): The continents of property users, derived from IP addresses.

``` clojure
{ :met "ch0:ga:uniqueAppviews"
  :dim "ga:continent"
  :per "last_1_month"}
```


#### Time on Page by Country / Territory
  * `Time on Page` (TIME): How long a user spent on a particular page in seconds. Calculated by subtracting the initial view time for a particular page from the initial view time for a subsequent page. Thus, this metric does not apply to exit pages for your property.
  * `Country / Territory` (STRING): The country of users, derived from IP addresses.

``` clojure
{ :met "ch0:ga:timeOnPage"
  :dim "ga:country"
  :per "last_1_month"}
```


#### Avg. Document Interactive Time (sec) by Longitude
  * `Avg. Document Interactive Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document and execute deferred and parser-inserted scripts including the network time from the user's location to your server.
  * Calculated by *(ga:domInteractiveTime / ga:domLatencyMetricsSample / 1000)*
  * `Longitude` (STRING): The approximate longitude of the user's city. Derived from IP address. Locations east of the meridian are represented by positive values and locations west of the meridian by negative values.

``` clojure
{ :met "ch0:ga:avgDomInteractiveTime"
  :dim "ga:longitude"
  :per "last_1_month"}
```


#### AdSense Exits by Region
  * `AdSense Exits` (INTEGER): The number of sessions that ended due to a user clicking on an AdSense ad.
  * `Region` (STRING): The region of users to your property, derived from IP addresses. In the U.S., a region is a state, such as New York.

``` clojure
{ :met "ch0:ga:adsenseExits"
  :dim "ga:region"
  :per "last_1_month"}
```


#### AdSense Revenue by Sub Continent Region
  * `AdSense Revenue` (CURRENCY): The total revenue from AdSense ads.
  * `Sub Continent Region` (STRING): The sub-continent of users, derived from IP addresses. For example, Polynesia or Northern Europe.

``` clojure
{ :met "ch0:ga:adsenseRevenue"
  :dim "ga:subContinent"
  :per "last_1_month"}
```


#### Avg. Time on Screen by Latitude
  * `Avg. Time on Screen` (TIME): The average amount of time users spent on a screen in seconds.
  * `Latitude` (STRING): The approximate latitude of the user's city. Derived from IP address. Locations north of the equator are represented by positive values and locations south of the equator by negative values.

``` clojure
{ :met "ch0:ga:avgScreenviewDuration"
  :dim "ga:latitude"
  :per "last_1_month"}
```

### System


#### Server Response Time (ms) by Java Support
  * `Server Response Time (ms)` (INTEGER): The total amount of time (in milliseconds) your server takes to respond to a user request among all samples, including the network time from user's location to your server.
  * `Java Support` (STRING): Indicates Java support for users' browsers. The possible values are Yes or No where the first letter must be capitalized.

``` clojure
{ :met "ch0:ga:serverResponseTime"
  :dim "ga:javaEnabled"
  :per "last_1_month"}
```


#### Search Exits by Source Property Display Name
  * `Search Exits` (INTEGER): The number of exits on your site that occurred following a search result from your internal search feature.
  * `Source Property Display Name` (STRING): Source property display name of roll-up properties. This is valid only for roll-up properties.

``` clojure
{ :met "ch0:ga:searchExits"
  :dim "ga:sourcePropertyDisplayName"
  :per "last_1_month"}
```


#### % New Sessions by Screen Colors
  * `% New Sessions` (PERCENT): The percentage of sessions by people who had never visited your property before.
  * Calculated by *ga:newUsers / ga:sessions*
  * `Screen Colors` (STRING): The color depth of users' monitors, as retrieved from the DOM of the user's browser. For example 4-bit, 8-bit, 24-bit, or undefined-bit.

``` clojure
{ :met "ch0:ga:percentNewSessions"
  :dim "ga:screenColors"
  :per "last_1_month"}
```


#### Entrances by Screen Resolution
  * `Entrances` (INTEGER): The number of entrances to your property measured as the first pageview in a session. Typically used with landingPagePath
  * `Screen Resolution` (STRING): The screen resolution of users' screens. For example: 1024x738.

``` clojure
{ :met "ch0:ga:entrances"
  :dim "ga:screenResolution"
  :per "last_1_month"}
```


#### Exits by Source Property Tracking ID
  * `Exits` (INTEGER): The number of exits from your property.
  * `Source Property Tracking ID` (STRING): Source property tracking ID of roll-up properties. This is valid only for roll-up properties.

``` clojure
{ :met "ch0:ga:exits"
  :dim "ga:sourcePropertyTrackingId"
  :per "last_1_month"}
```


#### Cost by Language
  * `Cost` (CURRENCY): Derived cost for the advertising campaign. The currency for this value is based on the currency that you set in your AdWords account.
  * `Language` (STRING): The language provided by the HTTP Request for the browser. Values are given as an ISO-639 code (e.g. en-gb for British English).

``` clojure
{ :met "ch0:ga:adCost"
  :dim "ga:language"
  :per "last_1_month"}
```


#### Sessions with Search by Flash Version
  * `Sessions with Search` (INTEGER): The total number of sessions that included an internal search
  * `Flash Version` (STRING): The versions of Flash supported by users' browsers, including minor versions.

``` clojure
{ :met "ch0:ga:searchSessions"
  :dim "ga:flashVersion"
  :per "last_1_month"}
```

### Platform or Device


#### Shipping by Mobile Device Info
  * `Shipping` (CURRENCY): The total cost of shipping.
  * `Mobile Device Info` (STRING): The branding, model, and marketing name used to identify the mobile device.

``` clojure
{ :met "ch0:ga:transactionShipping"
  :dim "ga:mobileDeviceInfo"
  :per "last_1_month"}
```


#### Page Download Time (ms) by Mobile Device Branding
  * `Page Download Time (ms)` (INTEGER): The total amount of time (in milliseconds) to download this page among all samples.
  * `Mobile Device Branding` (STRING): Mobile manufacturer or branded name.

``` clojure
{ :met "ch0:ga:pageDownloadTime"
  :dim "ga:mobileDeviceBranding"
  :per "last_1_month"}
```


#### Exits by Device Category
  * `Exits` (INTEGER): The number of exits from your property.
  * `Device Category` (STRING): The type of device: desktop, tablet, or mobile.

``` clojure
{ :met "ch0:ga:exits"
  :dim "ga:deviceCategory"
  :per "last_1_month"}
```


#### AdSense CTR by Mobile Device Model
  * `AdSense CTR` (PERCENT): The percentage of page impressions that resulted in a click on an AdSense ad.
  * Calculated by *ga:adsenseAdsClicks/ga:adsensePageImpressions*
  * `Mobile Device Model` (STRING): Mobile device model

``` clojure
{ :met "ch0:ga:adsenseCTR"
  :dim "ga:mobileDeviceModel"
  :per "last_1_month"}
```


#### Time after Search by Browser
  * `Time after Search` (TIME): The session duration on your property where a use of your internal search feature occurred.
  * `Browser` (STRING): The names of browsers used by users to your website. For example, Internet Explorer or Firefox.

``` clojure
{ :met "ch0:ga:searchDuration"
  :dim "ga:browser"
  :per "last_1_month"}
```


#### Document Content Loaded Time (ms) by Operating System Version
  * `Document Content Loaded Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document and execute deferred and parser-inserted scripts (DOMContentLoaded), including the network time from the user's location to your server. Parsing of the document is finished, the Document Object Model is ready, but referenced style sheets, images, and subframes may not be finished loading. This event is often the starting point for javascript framework execution, e.g., JQuery's onready() callback, etc.
  * `Operating System Version` (STRING): The version of the operating system used by your users, such as XP for Windows or PPC for Macintosh.

``` clojure
{ :met "ch0:ga:domContentLoadedTime"
  :dim "ga:operatingSystemVersion"
  :per "last_1_month"}
```


#### Unique Purchases by Mobile Device Marketing Name
  * `Unique Purchases` (INTEGER): The number of product sets purchased. For example, if users purchase 2 frisbees and 5 tennis balls from your site, 2 unique products have been purchased.
  * `Mobile Device Marketing Name` (STRING): The marketing name used for the mobile device.

``` clojure
{ :met "ch0:ga:uniquePurchases"
  :dim "ga:mobileDeviceMarketingName"
  :per "last_1_month"}
```


#### Pages / Session by Mobile Input Selector
  * `Pages / Session` (FLOAT): The average number of pages viewed during a session on your property. Repeated views of a single page are counted.
  * Calculated by *ga:pageviews / ga:sessions*
  * `Mobile Input Selector` (STRING): Selector used on the mobile device (e.g.: touchscreen, joystick, clickwheel, stylus).

``` clojure
{ :met "ch0:ga:pageviewsPerVisit"
  :dim "ga:mobileInputSelector"
  :per "last_1_month"}
```


#### % Search Exits by Browser Version
  * `% Search Exits` (PERCENT): The percentage of searches that resulted in an immediate exit from your property.
  * Calculated by *ga:searchExits / ga:searchUniques*
  * `Browser Version` (STRING): The browser versions used by users to your website. For example, 2.0.0.14

``` clojure
{ :met "ch0:ga:searchExitRate"
  :dim "ga:browserVersion"
  :per "last_1_month"}
```


#### Crashes / Screen by Operating System
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `Operating System` (STRING): The operating system used by your users. For example, Windows, Linux , Macintosh, iPhone, iPod.

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:operatingSystem"
  :per "last_1_month"}
```

### Session


#### Bounce Rate by Month of Year
  * `Bounce Rate` (PERCENT): The percentage of single-page session (i.e., session in which the person left your property from the first page).
  * Calculated by *ga:bounces / ga:sessions*
  * `Month of Year` (STRING): Combined values of ga:year and ga:month.

``` clojure
{ :met "ch0:ga:bounceRate"
  :dim "ga:yearMonth"
  :per "last_1_month"}
```


#### Avg. Session Duration by AdWords Criteria ID
  * `Avg. Session Duration` (TIME): The average duration of user sessions represented in total seconds.
  * Calculated by *ga:sessionDuration / ga:sessions*
  * `AdWords Criteria ID` (STRING): A string. Corresponds to AdWords API Criterion.id.

``` clojure
{ :met "ch0:ga:avgSessionDuration"
  :dim "ga:adwordsCriteriaID"
  :per "last_1_month"}
```


#### Session Duration by App Name
  * `Session Duration` (TIME): The total duration of user sessions represented in total seconds.
  * `App Name` (STRING): The name of the application.

``` clojure
{ :met "ch0:ga:sessionDuration"
  :dim "ga:appName"
  :per "last_1_month"}
```


#### Bounces by Ad Distribution Network
  * `Bounces` (INTEGER): The total number of single page (or single engagement hit) sessions for your property.
  * `Ad Distribution Network` (STRING): The networks used to deliver your ads (Content, Search, Search partners, etc.).

``` clojure
{ :met "ch0:ga:bounces"
  :dim "ga:adDistributionNetwork"
  :per "last_1_month"}
```


#### Sessions by AdWords Creative ID
  * `Sessions` (INTEGER): Counts the total number of sessions.
  * `AdWords Creative ID` (STRING): A string. Corresponds to AdWords API Ad.id.

``` clojure
{ :met "ch0:ga:sessions"
  :dim "ga:adwordsCreativeID"
  :per "last_1_month"}
```

### Time


#### Tax by Month Index
  * `Tax` (CURRENCY): The total amount of tax.
  * `Month Index` (STRING): Index for each month in the specified date range. Index for the first month in the date range is 0, 1 for the second month, and so on. The index corresponds to month entries.

``` clojure
{ :met "ch0:ga:transactionTax"
  :dim "ga:nthMonth"
  :per "last_1_month"}
```


#### Domain Lookup Time (ms) by Year
  * `Domain Lookup Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in DNS lookup for this page among all samples.
  * `Year` (STRING): The year of the session. A four-digit year from 2005 to the current year.

``` clojure
{ :met "ch0:ga:domainLookupTime"
  :dim "ga:year"
  :per "last_1_month"}
```


#### Unique Screen Views by Day of Week Name
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Day of Week Name` (STRING): The name of the day of the week (in English).

``` clojure
{ :met "ch0:ga:uniqueScreenviews"
  :dim "ga:dayOfWeekName"
  :per "last_1_month"}
```


#### Screen Views by Date
  * `Screen Views` (INTEGER): The total number of screenviews.
  * `Date` (STRING): The date of the session formatted as YYYYMMDD.

``` clojure
{ :met "ch0:ga:screenviews"
  :dim "ga:date"
  :per "last_1_month"}
```


#### Avg. Redirection Time (sec) by Month of Year
  * `Avg. Redirection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in redirects before fetching this page. If there are no redirects, the value for this metric is expected to be 0.
  * Calculated by *(ga:redirectionTime / ga:speedMetricsSample / 1000)*
  * `Month of Year` (STRING): Combined values of ga:year and ga:month.

``` clojure
{ :met "ch0:ga:avgRedirectionTime"
  :dim "ga:yearMonth"
  :per "last_1_month"}
```


#### Results Pageviews by ISO Year
  * `Results Pageviews` (INTEGER): The number of times a search result page was viewed after performing a search.
  * `ISO Year` (STRING): The ISO year of the session. Details: http://en.wikipedia.org/wiki/ISO_week_date. ga:isoYear should only be used with ga:isoWeek since ga:week represents gregorian calendar.

``` clojure
{ :met "ch0:ga:searchResultViews"
  :dim "ga:isoYear"
  :per "last_1_month"}
```


#### Bounce Rate by ISO Week of the Year
  * `Bounce Rate` (PERCENT): This dimension is deprecated and will be removed soon. Please use ga:bounceRate instead.
  * Calculated by *ga:bounces / ga:entrances*
  * `ISO Week of the Year` (STRING): The ISO week number, where each week starts with a Monday. Details: http://en.wikipedia.org/wiki/ISO_week_date. ga:isoWeek should only be used with ga:isoYear since ga:year represents gregorian calendar.

``` clojure
{ :met "ch0:ga:entranceBounceRate"
  :dim "ga:isoWeek"
  :per "last_1_month"}
```


#### Pages / Session by Minute Index
  * `Pages / Session` (FLOAT): The average number of pages viewed during a session on your property. Repeated views of a single page are counted.
  * Calculated by *ga:pageviews / ga:sessions*
  * `Minute Index` (STRING): Index for each minute in the specified date range. Index for the first minute of first day (i.e., start-date) in the date range is 0, 1 for the next minute, and so on.

``` clojure
{ :met "ch0:ga:pageviewsPerSession"
  :dim "ga:nthMinute"
  :per "last_1_month"}
```


#### Pageviews by Hour Index
  * `Pageviews` (INTEGER): The total number of pageviews for your property.
  * `Hour Index` (STRING): Index for each hour in the specified date range. Index for the first hour of first day (i.e., start-date) in the date range is 0, 1 for the next hour, and so on.

``` clojure
{ :met "ch0:ga:pageviews"
  :dim "ga:nthHour"
  :per "last_1_month"}
```


#### Bounce Rate by Day Index
  * `Bounce Rate` (PERCENT): The percentage of single-page session (i.e., session in which the person left your property from the first page).
  * Calculated by *ga:bounces / ga:sessions*
  * `Day Index` (STRING): Index for each day in the specified date range. Index for the first day (i.e., start-date) in the date range is 0, 1 for the second day, and so on.

``` clojure
{ :met "ch0:ga:visitBounceRate"
  :dim "ga:nthDay"
  :per "last_1_month"}
```


#### New Users by Month of the year
  * `New Users` (INTEGER): The number of users whose session on your property was marked as a first-time session.
  * `Month of the year` (STRING): The month of the session. A two digit integer from 01 to 12.

``` clojure
{ :met "ch0:ga:newVisits"
  :dim "ga:month"
  :per "last_1_month"}
```


#### Time on Page by Day of the month
  * `Time on Page` (TIME): How long a user spent on a particular page in seconds. Calculated by subtracting the initial view time for a particular page from the initial view time for a subsequent page. Thus, this metric does not apply to exit pages for your property.
  * `Day of the month` (STRING): The day of the month. A two-digit number from 01 to 31.

``` clojure
{ :met "ch0:ga:timeOnPage"
  :dim "ga:day"
  :per "last_1_month"}
```


#### Site Search Goal Conversion Rate by ISO Week of ISO Year
  * `Site Search Goal Conversion Rate` (PERCENT): The percentage of search sessions (i.e., sessions that included at least one search) which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:searchUniques*
  * `ISO Week of ISO Year` (STRING): Combined values of ga:isoYear and ga:isoWeek.

``` clojure
{ :met "ch0:ga:searchGoalConversionRateAll"
  :dim "ga:isoYearIsoWeek"
  :per "last_1_month"}
```


#### % Search Exits by Week Index
  * `% Search Exits` (PERCENT): The percentage of searches that resulted in an immediate exit from your property.
  * Calculated by *ga:searchExits / ga:searchUniques*
  * `Week Index` (STRING): Index for each week in the specified date range. Index for the first week in the date range is 0, 1 for the second week, and so on. The index corresponds to week entries.

``` clojure
{ :met "ch0:ga:searchExitRate"
  :dim "ga:nthWeek"
  :per "last_1_month"}
```


#### Cost per Conversion by Day of Week
  * `Cost per Conversion` (CURRENCY): The cost per conversion (including ecommerce and goal conversions) for your property.
  * Calculated by *(ga:adCost) / (ga:transactions  +  ga:goalCompletionsAll)*
  * `Day of Week` (STRING): The day of the week. A one-digit number from 0 (Sunday) to 6 (Saturday).

``` clojure
{ :met "ch0:ga:costPerConversion"
  :dim "ga:dayOfWeek"
  :per "last_1_month"}
```


#### Per Session Value by Minute
  * `Per Session Value` (CURRENCY): Average transaction revenue for a session on your property.
  * Calculated by *ga:transactionRevenue / ga:sessions*
  * `Minute` (STRING): Returns the minute in the hour. The possible values are between 00 and 59.

``` clojure
{ :met "ch0:ga:transactionRevenuePerSession"
  :dim "ga:minute"
  :per "last_1_month"}
```


#### AdSense Revenue by Hour
  * `AdSense Revenue` (CURRENCY): The total revenue from AdSense ads.
  * `Hour` (STRING): A two-digit hour of the day ranging from 00-23 in the timezone configured for the account. This value is also corrected for daylight savings time, adhering to all local rules for daylight savings time. If your timezone follows daylight savings time, there will be an apparent bump in the number of sessions during the change-over hour (e.g. between 1:00 and 2:00) for the day per year when that hour repeats. A corresponding hour with zero sessions will occur at the opposite changeover. (Google Analytics does not track user time more precisely than hours.)

``` clojure
{ :met "ch0:ga:adsenseRevenue"
  :dim "ga:hour"
  :per "last_1_month"}
```


#### AdSense Ads Viewed by Week of Year
  * `AdSense Ads Viewed` (INTEGER): The number of AdSense ads viewed. Multiple ads can be displayed within an Ad Unit.
  * `Week of Year` (STRING): Combined values of ga:year and ga:week.

``` clojure
{ :met "ch0:ga:adsenseAdsViewed"
  :dim "ga:yearWeek"
  :per "last_1_month"}
```


#### Users by Hour of Day
  * `Users` (INTEGER): Total number of users to your property for the requested time period.
  * `Hour of Day` (STRING): Combined values of ga:date and ga:hour.

``` clojure
{ :met "ch0:ga:visitors"
  :dim "ga:dateHour"
  :per "last_1_month"}
```

### Content Experiments


#### Pages / Session by Experiment ID
  * `Pages / Session` (FLOAT): The average number of pages viewed during a session on your property. Repeated views of a single page are counted.
  * Calculated by *ga:pageviews / ga:sessions*
  * `Experiment ID` (STRING): The user-scoped id of the content experiment that the user was exposed to when the metrics were reported.

``` clojure
{ :met "ch0:ga:pageviewsPerVisit"
  :dim "ga:experimentId"
  :per "last_1_month"}
```


#### AdSense Ads Viewed by Variation
  * `AdSense Ads Viewed` (INTEGER): The number of AdSense ads viewed. Multiple ads can be displayed within an Ad Unit.
  * `Variation` (STRING): The user-scoped id of the particular variation that the user was exposed to during a content experiment.

``` clojure
{ :met "ch0:ga:adsenseAdsViewed"
  :dim "ga:experimentVariant"
  :per "last_1_month"}
```

