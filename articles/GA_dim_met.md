---
title: "GA metrics and dimensions overview"
desc: "Loganis Queries using GA Dimensions and Metrics overview"
layout: article
---

##Overview of GA metrics and dimensions
* This guides provides an overview of GA dimensions and metrics by example
* Based on GA Metadata API
* 1 Metric, 1 Dimension and 1 LQuery for each example

### Visitor


#### Unique Visitors by Visitor Type
  * `Unique Visitors` (INTEGER): Total number of visitors to your property for the requested time period.
  * `Visitor Type` (STRING): A boolean indicating if a visitor is new or returning. Possible values: New Visitor, Returning Visitor.

``` clojure
{ :met "ch0:ga:visitors"
  :dim "ga:visitorType"
  :per "last_1_month"}
```


#### % New Visits by User Defined Value
  * `% New Visits` (PERCENT): The percentage of visits by people who had never visited your property before.
  * Calculated by *ga:newVisits / ga:visits*
  * `User Defined Value` (STRING): The value provided when you define custom visitor segments for your property.

``` clojure
{ :met "ch0:ga:percentNewVisits"
  :dim "ga:userDefinedValue"
  :per "last_1_month"}
```


#### New Visits by Days Since Last Visit
  * `New Visits` (INTEGER): The number of visitors whose visit to your property was marked as a first-time visit.
  * `Days Since Last Visit` (STRING): The number of days elapsed since visitors last visited your property. Used to calculate visitor loyalty.

``` clojure
{ :met "ch0:ga:newVisits"
  :dim "ga:daysSinceLastVisit"
  :per "last_1_month"}
```


#### Avg. Visit Duration by Count of Visits
  * `Avg. Visit Duration` (TIME): The average duration visitor sessions represented in total seconds.
  * Calculated by *ga:timeOnSite / ga:visits*
  * `Count of Visits` (STRING): The visit index for a visitor to your property. Each visit from a unique visitor will get its own incremental index starting from 1 for the first visit. Subsequent visits do not change previous visit indicies. For example, if a certain visitor has 4 visits to your website, visitCount for that visitor will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:avgTimeOnSite"
  :dim "ga:visitCount"
  :per "last_1_month"}
```

### Exceptions


#### Crashes by Start Page
  * `Crashes` (INTEGER): The number of exceptions where isFatal is set to true.
  * `Start Page` (STRING): A page where the user initiated an internal search on your property.

``` clojure
{ :met "ch0:ga:fatalExceptions"
  :dim "ga:searchStartPage"
  :per "last_1_month"}
```


#### Crashes / Screen by AdWords Customer ID
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `AdWords Customer ID` (STRING): A string. Corresponds to AdWords API AccountInfo.customerId.

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:adwordsCustomerID"
  :per "last_1_month"}
```


#### Exceptions / Screen by Operating System
  * `Exceptions / Screen` (PERCENT): The number of exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:exceptions / ga:screenviews*
  * `Operating System` (STRING): The operating system used by your visitors. For example, Windows, Linux , Macintosh, iPhone, iPod.

``` clojure
{ :met "ch0:ga:exceptionsPerScreenview"
  :dim "ga:operatingSystem"
  :per "last_1_month"}
```


#### Exceptions by Hour
  * `Exceptions` (INTEGER): The number of exceptions that were sent to Google Analytics.
  * `Hour` (STRING): A two-digit hour of the day ranging from 00-23 in the timezone configured for the account. This value is also corrected for daylight savings time, adhering to all local rules for daylight savings time. If your timezone follows daylight savings time, there will be an apparent bump in the number of visits during the change-over hour (e.g. between 1:00 and 2:00) for the day per year when that hour repeats. A corresponding hour with zero visits will occur at the opposite changeover. (Google Analytics does not track visitor time more precisely than hours.)

``` clojure
{ :met "ch0:ga:exceptions"
  :dim "ga:hour"
  :per "last_1_month"}
```

### Traffic Sources


#### Organic Searches by Source / Medium
  * `Organic Searches` (INTEGER): The number of organic searches that happened within a session. This metric is search engine agnostic.
  * `Source / Medium` (STRING): Combined values of ga:source and ga:medium.

``` clojure
{ :met "ch0:ga:organicSearches"
  :dim "ga:sourceMedium"
  :per "last_1_month"}
```


#### % New Visits by Keyword
  * `% New Visits` (PERCENT): The percentage of visits by people who had never visited your property before.
  * Calculated by *ga:newVisits / ga:visits*
  * `Keyword` (STRING): When using manual campaign tracking, the value of the utm_term campaign tracking parameter. When using AdWords autotagging or if a visitor used organic search to reach your property, the keywords used by visitors to reach your property. Otherwise the value is (not set).

``` clojure
{ :met "ch0:ga:percentNewVisits"
  :dim "ga:keyword"
  :per "last_1_month"}
```


#### AdSense Ads Viewed by Campaign
  * `AdSense Ads Viewed` (INTEGER): The number of AdSense ads viewed. Multiple ads can be displayed within an Ad Unit.
  * `Campaign` (STRING): When using manual campaign tracking, the value of the utm_campaign campaign tracking parameter. When using AdWords autotagging, the name(s) of the online ad campaign that you use for your property. Otherwise the value (not set) is used.

``` clojure
{ :met "ch0:ga:adsenseAdsViewed"
  :dim "ga:campaign"
  :per "last_1_month"}
```


#### Results Pageviews / Search by Social Network
  * `Results Pageviews / Search` (FLOAT): The average number of times people viewed a search results page after performing a search.
  * Calculated by *ga:searchResultViews / ga:searchUniques*
  * `Social Network` (STRING): Name of the social network. This can be related to the referring social network for traffic sources, or to the social network for social data hub activities. E.g. Google+, Blogger, etc.

``` clojure
{ :met "ch0:ga:avgSearchResultViews"
  :dim "ga:socialNetwork"
  :per "last_1_month"}
```


#### Goal 1 Abandonment Rate by Full Referrer
  * `Goal 1 Abandonment Rate` (PERCENT): The rate at which the requested goal number was abandoned.
  * Calculated by *((ga:goalXXStarts - ga:goalXXCompletions)) / (ga:goalXXStarts)*
  * `Full Referrer` (STRING): The full referring URL including the hostname and path.

``` clojure
{ :met "ch0:ga:goalXXAbandonRate"
  :dim "ga:fullReferrer"
  :per "last_1_month"}
```


#### Actions Per Social Visit by Medium
  * `Actions Per Social Visit` (FLOAT): The number of social interactions per visit to your property.
  * Calculated by *ga:socialInteractions / ga:uniqueSocialInteractions*
  * `Medium` (STRING): The type of referrals to your property. When using manual campaign tracking, the value of the utm_medium campaign tracking parameter. When using AdWords autotagging, the value is ppc. If the user comes from a search engine detected by Google Analytics, the value is organic. If the referrer is not a search engine, the value is referral. If the visitor came directly to the property, and document.referrer is empty, the value is (none).

``` clojure
{ :met "ch0:ga:socialInteractionsPerVisit"
  :dim "ga:medium"
  :per "last_1_month"}
```


#### AdSense eCPM by Social Source Referral
  * `AdSense eCPM` (CURRENCY): The estimated cost per thousand page impressions. It is your AdSense Revenue per 1000 page impressions.
  * Calculated by *ga:adsenseRevenue/(ga:adsensePageImpressions/1000)*
  * `Social Source Referral` (STRING): Indicates visits that arrived to the property from a social source. The possible values are Yes or No where the first letter is capitalized.

``` clojure
{ :met "ch0:ga:adsenseECPM"
  :dim "ga:hasSocialSourceReferral"
  :per "last_1_month"}
```


#### Goal 1 Completions by Referral Path
  * `Goal 1 Completions` (INTEGER): The total number of completions for the requested goal number.
  * `Referral Path` (STRING): The path of the referring URL (e.g. document.referrer). If someone places a link to your property on their website, this element contains the path of the page that contains the referring link.

``` clojure
{ :met "ch0:ga:goalXXCompletions"
  :dim "ga:referralPath"
  :per "last_1_month"}
```


#### Goal Completions by Source
  * `Goal Completions` (INTEGER): The total number of completions for all goals defined for your profile.
  * `Source` (STRING): The source of referrals to your property. When using manual campaign tracking, the value of the utm_source campaign tracking parameter. When using AdWords autotagging, the value is google. Otherwise the domain of the source referring the visitor to your property (e.g. document.referrer). The value may also contain a port address. If the visitor arrived without a referrer, the value is (direct)

``` clojure
{ :met "ch0:ga:goalCompletionsAll"
  :dim "ga:source"
  :per "last_1_month"}
```

### Site Speed


#### Speed Metrics Sample by Campaign
  * `Speed Metrics Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the averages for site speed metrics. This metric is used in all site speed average calculations including avgDomainLookupTime, avgPageDownloadTime, avgRedirectionTime, avgServerConnectionTime, and avgServerResponseTime.
  * `Campaign` (STRING): When using manual campaign tracking, the value of the utm_campaign campaign tracking parameter. When using AdWords autotagging, the name(s) of the online ad campaign that you use for your property. Otherwise the value (not set) is used.

``` clojure
{ :met "ch0:ga:speedMetricsSample"
  :dim "ga:campaign"
  :per "last_1_month"}
```


#### Domain Lookup Time (ms) by Targeting Type
  * `Domain Lookup Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in DNS lookup for this page among all samples.
  * `Targeting Type` (STRING): How your AdWords ads were targeted (keyword, placement, and vertical targeting, etc.).

``` clojure
{ :met "ch0:ga:domainLookupTime"
  :dim "ga:adTargetingType"
  :per "last_1_month"}
```


#### Page Download Time (ms) by Mobile (Including Tablet)
  * `Page Download Time (ms)` (INTEGER): The total amount of time (in milliseconds) to download this page among all samples.
  * `Mobile (Including Tablet)` (STRING): This dimension is deprecated and will be removed soon. Please use ga:deviceCategory instead (e.g., ga:deviceCategory==mobile).

``` clojure
{ :met "ch0:ga:pageDownloadTime"
  :dim "ga:isMobile"
  :per "last_1_month"}
```


#### Avg. Server Connection Time (sec) by Count of Visits
  * `Avg. Server Connection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in establishing TCP connection for this page.
  * Calculated by *(ga:serverConnectionTime / ga:speedMetricsSample / 1000)*
  * `Count of Visits` (STRING): The visit index for a visitor to your property. Each visit from a unique visitor will get its own incremental index starting from 1 for the first visit. Subsequent visits do not change previous visit indicies. For example, if a certain visitor has 4 visits to your website, visitCount for that visitor will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:avgServerConnectionTime"
  :dim "ga:visitCount"
  :per "last_1_month"}
```


#### Avg. Domain Lookup Time (sec) by Product
  * `Avg. Domain Lookup Time (sec)` (FLOAT): The average amount of time (in seconds) spent in DNS lookup for this page.
  * Calculated by *(ga:domainLookupTime / ga:speedMetricsSample / 1000)*
  * `Product` (STRING): The product name for purchased items as supplied by your ecommerce tracking application.

``` clojure
{ :met "ch0:ga:avgDomainLookupTime"
  :dim "ga:productName"
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


#### Document Content Loaded Time (ms) by Operating System Version
  * `Document Content Loaded Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document and execute deferred and parser-inserted scripts (DOMContentLoaded), including the network time from the user's location to your server. Parsing of the document is finished, the Document Object Model is ready, but referenced style sheets, images, and subframes may not be finished loading. This event is often the starting point for javascript framework execution, e.g., JQuery's onready() callback, etc.
  * `Operating System Version` (STRING): The version of the operating system used by your visitors, such as XP for Windows or PPC for Macintosh.

``` clojure
{ :met "ch0:ga:domContentLoadedTime"
  :dim "ga:operatingSystemVersion"
  :per "last_1_month"}
```


#### DOM Latency Metrics Sample by Keyword
  * `DOM Latency Metrics Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the averages for site speed DOM metrics. This metric is used in the avgDomContentLoadedTime and avgDomInteractiveTime calculations.
  * `Keyword` (STRING): When using manual campaign tracking, the value of the utm_term campaign tracking parameter. When using AdWords autotagging or if a visitor used organic search to reach your property, the keywords used by visitors to reach your property. Otherwise the value is (not set).

``` clojure
{ :met "ch0:ga:domLatencyMetricsSample"
  :dim "ga:keyword"
  :per "last_1_month"}
```


#### Server Connection Time (ms) by User Profile URL
  * `Server Connection Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in establishing TCP connection for this page among all samples.
  * `User Profile URL` (STRING): For a social data hub activity, this value represents the URL of the associated user's social network profile.

``` clojure
{ :met "ch0:ga:serverConnectionTime"
  :dim "ga:socialActivityUserProfileUrl"
  :per "last_1_month"}
```


#### Server Response Time (ms) by Second Page
  * `Server Response Time (ms)` (INTEGER): The total amount of time (in milliseconds) your server takes to respond to a user request among all samples, including the network time from user's location to your server.
  * `Second Page` (STRING): The second page in a user's session.

``` clojure
{ :met "ch0:ga:serverResponseTime"
  :dim "ga:secondPagePath"
  :per "last_1_month"}
```


#### Document Interactive Time (ms) by Week of the Year
  * `Document Interactive Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document (DOMInteractive), including the network time from the user's location to your server. At this time, the user can interact with the Document Object Model even though it is not fully loaded.
  * `Week of the Year` (STRING): The week of the visit. A two-digit number from 01 to 53. Each week starts on Sunday.

``` clojure
{ :met "ch0:ga:domInteractiveTime"
  :dim "ga:week"
  :per "last_1_month"}
```


#### Avg. Page Download Time (sec) by App Version
  * `Avg. Page Download Time (sec)` (FLOAT): The average amount of time (in seconds) to download this page.
  * Calculated by *(ga:pageDownloadTime / ga:speedMetricsSample / 1000)*
  * `App Version` (STRING): The version of the application.

``` clojure
{ :met "ch0:ga:avgPageDownloadTime"
  :dim "ga:appVersion"
  :per "last_1_month"}
```


#### Page Load Time (ms) by Social Source and Action
  * `Page Load Time (ms)` (INTEGER): Total Page Load Time is the amount of time (in milliseconds) it takes for pages from the sample set to load, from initiation of the pageview (e.g. click on a page link) to load completion in the browser.
  * `Social Source and Action` (STRING): For social interactions, a value representing the concatenation of the socialInteractionNetwork and socialInteractionAction action being tracked at this hit level (e.g. Google: +1)

``` clojure
{ :met "ch0:ga:pageLoadTime"
  :dim "ga:socialInteractionNetworkAction"
  :per "last_1_month"}
```


#### Page Load Sample by Shared URL
  * `Page Load Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the average page load time.
  * `Shared URL` (STRING): For a social data hub activity, this value represents the URL shared by the associated social network user.

``` clojure
{ :met "ch0:ga:pageLoadSample"
  :dim "ga:socialActivityContentUrl"
  :per "last_1_month"}
```


#### Avg. Document Interactive Time (sec) by Source / Medium
  * `Avg. Document Interactive Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document and execute deferred and parser-inserted scripts including the network time from the user's location to your server.
  * Calculated by *(ga:domInteractiveTime / ga:domLatencyMetricsSample / 1000)*
  * `Source / Medium` (STRING): Combined values of ga:source and ga:medium.

``` clojure
{ :met "ch0:ga:avgDomInteractiveTime"
  :dim "ga:sourceMedium"
  :per "last_1_month"}
```


#### Redirection Time (ms) by Ad Content
  * `Redirection Time (ms)` (INTEGER): The total amount of time (in milliseconds) spent in redirects before fetching this page among all samples. If there are no redirects, the value for this metric is expected to be 0.
  * `Ad Content` (STRING): When using manual campaign tracking, the value of the utm_content campaign tracking parameter. When using AdWords autotagging, the first line of the text for your online Ad campaign. If you are using mad libs for your AdWords content, this field displays the keywords you provided for the mad libs keyword match. Otherwise the value is (not set)

``` clojure
{ :met "ch0:ga:redirectionTime"
  :dim "ga:adContent"
  :per "last_1_month"}
```


#### Avg. Page Load Time (sec) by Operating System Version
  * `Avg. Page Load Time (sec)` (FLOAT): The average amount of time (in seconds) it takes for pages from the sample set to load, from initiation of the pageview (e.g. click on a page link) to load completion in the browser.
  * Calculated by *(ga:pageLoadTime / ga:pageLoadSample / 1000)*
  * `Operating System Version` (STRING): The version of the operating system used by your visitors, such as XP for Windows or PPC for Macintosh.

``` clojure
{ :met "ch0:ga:avgPageLoadTime"
  :dim "ga:operatingSystemVersion"
  :per "last_1_month"}
```


#### Avg. Document Content Loaded Time (sec) by Visit Duration
  * `Avg. Document Content Loaded Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document.
  * Calculated by *(ga:domContentLoadedTime / ga:domLatencyMetricsSample / 1000)*
  * `Visit Duration` (STRING): The length of a visit to your property measured in seconds and reported in second increments. The value returned is a string.

``` clojure
{ :met "ch0:ga:avgDomContentLoadedTime"
  :dim "ga:visitLength"
  :per "last_1_month"}
```


#### Avg. Server Response Time (sec) by Latitude
  * `Avg. Server Response Time (sec)` (FLOAT): The average amount of time (in seconds) your server takes to respond to a user request, including the network time from user's location to your server.
  * Calculated by *(ga:serverResponseTime / ga:speedMetricsSample / 1000)*
  * `Latitude` (STRING): The approximate latitude of the visitor's city. Derived from IP address. Locations north of the equator are represented by positive values and locations south of the equator by negative values.

``` clojure
{ :met "ch0:ga:avgServerResponseTime"
  :dim "ga:latitude"
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


#### Cost by Ad Format
  * `Cost` (CURRENCY): Derived cost for the advertising campaign. The currency for this value is based on the currency that you set in your AdWords account.
  * `Ad Format` (STRING): Your AdWords ad formats (Text, Image, Flash, Video, etc.).

``` clojure
{ :met "ch0:ga:adCost"
  :dim "ga:adFormat"
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


#### Avg. Domain Lookup Time (sec) by Keyword Match Type
  * `Avg. Domain Lookup Time (sec)` (FLOAT): The average amount of time (in seconds) spent in DNS lookup for this page.
  * Calculated by *(ga:domainLookupTime / ga:speedMetricsSample / 1000)*
  * `Keyword Match Type` (STRING): The match types applied to your keywords (Phrase, Exact, Broad). Details: https://support.google.com/adwords/answer/2472708?hl=en

``` clojure
{ :met "ch0:ga:avgDomainLookupTime"
  :dim "ga:adKeywordMatchType"
  :per "last_1_month"}
```


#### Margin by AdWords Creative ID
  * `Margin` (PERCENT): The overall transaction profit margin.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / (ga:transactionRevenue + ga:goalValueAll)*
  * `AdWords Creative ID` (STRING): A string. Corresponds to AdWords API Ad.id.

``` clojure
{ :met "ch0:ga:margin"
  :dim "ga:adwordsCreativeID"
  :per "last_1_month"}
```


#### Total Value by AdWords Ad Group ID
  * `Total Value` (CURRENCY): Total value for your property (including total revenue and total goal value).
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll)*
  * `AdWords Ad Group ID` (STRING): A string. Corresponds to AdWords API AdGroup.id.

``` clojure
{ :met "ch0:ga:totalValue"
  :dim "ga:adwordsAdGroupID"
  :per "last_1_month"}
```


#### CTR by Ad Distribution Network
  * `CTR` (PERCENT): Click-through-rate for your ad. This is equal to the number of clicks divided by the number of impressions for your ad (e.g. how many times users clicked on one of your ads where that ad appeared).
  * Calculated by *ga:adClicks / ga:impressions*
  * `Ad Distribution Network` (STRING): The networks used to deliver your ads (Content, Search, Search partners, etc.).

``` clojure
{ :met "ch0:ga:CTR"
  :dim "ga:adDistributionNetwork"
  :per "last_1_month"}
```


#### RPC by AdWords Criteria ID
  * `RPC` (CURRENCY): RPC or revenue-per-click is the average revenue (from ecommerce sales and/or goal value) you received for each click on one of your search ads.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll) / ga:adClicks*
  * `AdWords Criteria ID` (STRING): A string. Corresponds to AdWords API Criterion.id.

``` clojure
{ :met "ch0:ga:RPC"
  :dim "ga:adwordsCriteriaID"
  :per "last_1_month"}
```


#### Unique Purchases by Placement URL
  * `Unique Purchases` (INTEGER): The number of product sets purchased. For example, if users purchase 2 frisbees and 5 tennis balls from your site, 2 unique products have been purchased.
  * `Placement URL` (STRING): The URLs where your ads on the content network were placed.

``` clojure
{ :met "ch0:ga:uniquePurchases"
  :dim "ga:adPlacementUrl"
  :per "last_1_month"}
```


#### CPM by Ad Group
  * `CPM` (CURRENCY): Cost per thousand impressions.
  * Calculated by *ga:adCost / (ga:impressions / 1000)*
  * `Ad Group` (STRING): The name of your AdWords ad group.

``` clojure
{ :met "ch0:ga:CPM"
  :dim "ga:adGroup"
  :per "last_1_month"}
```


#### Search Exits by Display URL
  * `Search Exits` (INTEGER): The number of exits on your site that occurred following a search result from your internal search feature.
  * `Display URL` (STRING): The URLs your AdWords ads displayed.

``` clojure
{ :met "ch0:ga:searchExits"
  :dim "ga:adDisplayUrl"
  :per "last_1_month"}
```


#### Visits with Event by Query Match Type
  * `Visits with Event` (INTEGER): The total number of visits with events.
  * `Query Match Type` (STRING): The match types applied for the search term the user had input(Phrase, Exact, Broad, etc.). Ads on the content network are identified as "Content network". Details: https://support.google.com/adwords/answer/2472708?hl=en

``` clojure
{ :met "ch0:ga:visitsWithEvent"
  :dim "ga:adMatchType"
  :per "last_1_month"}
```


#### Cost per Conversion by Matched Search Query
  * `Cost per Conversion` (CURRENCY): The cost per conversion (including ecommerce and goal conversions) for your property.
  * Calculated by *(ga:adCost) / (ga:transactions  +  ga:goalCompletionsAll)*
  * `Matched Search Query` (STRING): The search queries that triggered impressions of your AdWords ads.

``` clojure
{ :met "ch0:ga:costPerConversion"
  :dim "ga:adMatchedQuery"
  :per "last_1_month"}
```


#### ROI by Placement Type
  * `ROI` (PERCENT): Returns on Investment is overall transaction profit divided by derived advertising cost.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / ga:adCost*
  * `Placement Type` (STRING): How you manage your ads on the content network. Values are Automatic placements or Managed placements.

``` clojure
{ :met "ch0:ga:ROI"
  :dim "ga:adTargetingOption"
  :per "last_1_month"}
```


#### Cost per Goal Conversion by Targeting Type
  * `Cost per Goal Conversion` (CURRENCY): The cost per goal conversion for your property.
  * Calculated by *(ga:adCost) / (ga:goalCompletionsAll)*
  * `Targeting Type` (STRING): How your AdWords ads were targeted (keyword, placement, and vertical targeting, etc.).

``` clojure
{ :met "ch0:ga:costPerGoalConversion"
  :dim "ga:adTargetingType"
  :per "last_1_month"}
```


#### Impressions by Destination URL
  * `Impressions` (INTEGER): Total number of campaign impressions.
  * `Destination URL` (STRING): The URLs to which your AdWords ads referred traffic.

``` clojure
{ :met "ch0:ga:impressions"
  :dim "ga:adDestinationUrl"
  :per "last_1_month"}
```


#### Event Value by Ad Slot
  * `Event Value` (INTEGER): The total value of events for the profile.
  * `Ad Slot` (STRING): The location of the advertisement on the hosting page (Top, RHS, or not set).

``` clojure
{ :met "ch0:ga:eventValue"
  :dim "ga:adSlot"
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


#### AdSense Ads Clicked by Day of Week
  * `AdSense Ads Clicked` (INTEGER): The number of times AdSense ads on your site were clicked.
  * `Day of Week` (STRING): The day of the week. A one-digit number from 0 (Sunday) to 6 (Saturday).

``` clojure
{ :met "ch0:ga:adsenseAdsClicks"
  :dim "ga:dayOfWeek"
  :per "last_1_month"}
```


#### AdSense Page Impressions by AdWords Customer ID
  * `AdSense Page Impressions` (INTEGER): The number of pageviews during which an AdSense ad was displayed. A page impression can have multiple Ad Units.
  * `AdWords Customer ID` (STRING): A string. Corresponds to AdWords API AccountInfo.customerId.

``` clojure
{ :met "ch0:ga:adsensePageImpressions"
  :dim "ga:adwordsCustomerID"
  :per "last_1_month"}
```


#### AdSense Ads Viewed by Query Match Type
  * `AdSense Ads Viewed` (INTEGER): The number of AdSense ads viewed. Multiple ads can be displayed within an Ad Unit.
  * `Query Match Type` (STRING): The match types applied for the search term the user had input(Phrase, Exact, Broad, etc.). Ads on the content network are identified as "Content network". Details: https://support.google.com/adwords/answer/2472708?hl=en

``` clojure
{ :met "ch0:ga:adsenseAdsViewed"
  :dim "ga:adMatchType"
  :per "last_1_month"}
```


#### AdSense Revenue by Landing Screen
  * `AdSense Revenue` (CURRENCY): The total revenue from AdSense ads.
  * `Landing Screen` (STRING): The name of the first screen viewed.

``` clojure
{ :met "ch0:ga:adsenseRevenue"
  :dim "ga:landingScreenName"
  :per "last_1_month"}
```


#### AdSense Exits by ISO Year
  * `AdSense Exits` (INTEGER): The number of sessions that ended due to a user clicking on an AdSense ad.
  * `ISO Year` (STRING): The ISO year of the visit. Details: http://en.wikipedia.org/wiki/ISO_week_date. ga:isoYear should only be used with ga:isoWeek since ga:week represents gregorian calendar.

``` clojure
{ :met "ch0:ga:adsenseExits"
  :dim "ga:isoYear"
  :per "last_1_month"}
```


#### AdSense eCPM by Previous Page Path
  * `AdSense eCPM` (CURRENCY): The estimated cost per thousand page impressions. It is your AdSense Revenue per 1000 page impressions.
  * Calculated by *ga:adsenseRevenue/(ga:adsensePageImpressions/1000)*
  * `Previous Page Path` (STRING): A page on your property that was visited before another page on the same property. Typically used with the pagePath dimension.

``` clojure
{ :met "ch0:ga:adsenseECPM"
  :dim "ga:previousPagePath"
  :per "last_1_month"}
```


#### AdSense Ad Units Viewed by User Photo URL
  * `AdSense Ad Units Viewed` (INTEGER): The number of AdSense ad units viewed. An Ad unit is a set of ads displayed as a result of one piece of the AdSense ad code. Details: https://support.google.com/adsense/answer/32715?hl=en
  * `User Photo URL` (STRING): For a social data hub activity, this value represents the URL of the photo associated with the user's social network profile.

``` clojure
{ :met "ch0:ga:adsenseAdUnitsViewed"
  :dim "ga:socialActivityUserPhotoUrl"
  :per "last_1_month"}
```


#### AdSense CTR by Social Entity
  * `AdSense CTR` (PERCENT): The percentage of page impressions that resulted in a click on an AdSense ad.
  * Calculated by *ga:adsenseAdsClicks/ga:adsensePageImpressions*
  * `Social Entity` (STRING): For social interactions, a value representing the URL (or resource) which receives the social network action.

``` clojure
{ :met "ch0:ga:adsenseCTR"
  :dim "ga:socialInteractionTarget"
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


#### Page Value by Second Page
  * `Page Value` (CURRENCY): The average value of this page or set of pages. Page Value is (ga:transactionRevenue + ga:goalValueAll) / ga:uniquePageviews (for the page or set of pages).
  * `Second Page` (STRING): The second page in a user's session.

``` clojure
{ :met "ch0:ga:pageValue"
  :dim "ga:secondPagePath"
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


#### Entrances / Pageviews by Exit Page
  * `Entrances / Pageviews` (PERCENT): The percentage of pageviews in which this page was the entrance.
  * Calculated by *ga:entrances / ga:pageviews*
  * `Exit Page` (STRING): The last page in a user's session, or exit page.

``` clojure
{ :met "ch0:ga:entranceRate"
  :dim "ga:exitPagePath"
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
  * `Time on Page` (TIME): How long a visitor spent on a particular page in seconds. Calculated by subtracting the initial view time for a particular page from the initial view time for a subsequent page. Thus, this metric does not apply to exit pages for your property.
  * `Previous Page Path` (STRING): A page on your property that was visited before another page on the same property. Typically used with the pagePath dimension.

``` clojure
{ :met "ch0:ga:timeOnPage"
  :dim "ga:previousPagePath"
  :per "last_1_month"}
```


#### Local Shipping by Page Title
  * `Local Shipping` (CURRENCY): Transaction shipping cost in local currency.
  * `Page Title` (STRING): The title of a page. Keep in mind that multiple pages might have the same page title.

``` clojure
{ :met "ch0:ga:localTransactionShipping"
  :dim "ga:pageTitle"
  :per "last_1_month"}
```


#### Pages / Visit by Next Page Path
  * `Pages / Visit` (FLOAT): The average number of pages viewed during a visit to your property. Repeated views of a single page are counted.
  * Calculated by *ga:pageviews / ga:visits*
  * `Next Page Path` (STRING): A page on your website that was visited after another page on your website. Typically used with the previousPagePath dimension.

``` clojure
{ :met "ch0:ga:pageviewsPerVisit"
  :dim "ga:nextPagePath"
  :per "last_1_month"}
```


#### Avg. Time on Page by Page Depth
  * `Avg. Time on Page` (TIME): The average amount of time visitors spent viewing this page or a set of pages.
  * Calculated by *ga:timeOnPage / (ga:pageviews - ga:exits)*
  * `Page Depth` (STRING): The number of pages visited by visitors during a session (visit). The value is a histogram that counts pageviews across a range of possible values. In this calculation, all visits will have at least one pageview, and some percentage of visits will have more.

``` clojure
{ :met "ch0:ga:avgTimeOnPage"
  :dim "ga:pageDepth"
  :per "last_1_month"}
```


#### Screen Views by Page
  * `Screen Views` (INTEGER): The total number of screenviews.
  * `Page` (STRING): A page on your website specified by path and/or query parameters. Use in conjunction with hostname to get the full URL of the page.

``` clojure
{ :met "ch0:ga:appviews"
  :dim "ga:pagePath"
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


#### Avg. Time on Screen by Page path level 2
  * `Avg. Time on Screen` (TIME): The average amount of time users spent on a screen in seconds.
  * `Page path level 2` (STRING): This dimension rolls up all the page paths in the second hierarchical level in pagePath.

``` clojure
{ :met "ch0:ga:avgScreenviewDuration"
  :dim "ga:pagePathLevel2"
  :per "last_1_month"}
```


#### % Exit by Landing Page
  * `% Exit` (PERCENT): The percentage of exits from your property that occurred out of the total page views.
  * Calculated by *ga:exits / (ga:pageviews + ga:screenviews)*
  * `Landing Page` (STRING): The first page in a user's session, or landing page.

``` clojure
{ :met "ch0:ga:exitRate"
  :dim "ga:landingPagePath"
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


#### Time on Page by Custom Variable (Value 01)
  * `Time on Page` (TIME): How long a visitor spent on a particular page in seconds. Calculated by subtracting the initial view time for a particular page from the initial view time for a subsequent page. Thus, this metric does not apply to exit pages for your property.
  * `Custom Variable (Value 01)` (STRING): The value for the requested custom variable.

``` clojure
{ :met "ch0:ga:timeOnPage"
  :dim "ga:customVarValueXX"
  :per "last_1_month"}
```


#### Avg. Redirection Time (sec) by Custom Variable (Key 1)
  * `Avg. Redirection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in redirects before fetching this page. If there are no redirects, the value for this metric is expected to be 0.
  * Calculated by *(ga:redirectionTime / ga:speedMetricsSample / 1000)*
  * `Custom Variable (Key 1)` (STRING): The name for the requested custom variable.

``` clojure
{ :met "ch0:ga:avgRedirectionTime"
  :dim "ga:customVarNameXX"
  :per "last_1_month"}
```

### Audience


#### Goal 1 Value by Age
  * `Goal 1 Value` (CURRENCY): The total numeric value for the requested goal number.
  * `Age` (STRING): Age bracket of visitor.

``` clojure
{ :met "ch0:ga:goalXXValue"
  :dim "ga:visitorAgeBracket"
  :per "last_1_month"}
```


#### AdSense Ad Units Viewed by Gender
  * `AdSense Ad Units Viewed` (INTEGER): The number of AdSense ad units viewed. An Ad unit is a set of ads displayed as a result of one piece of the AdSense ad code. Details: https://support.google.com/adsense/answer/32715?hl=en
  * `Gender` (STRING): Gender of visitor.

``` clojure
{ :met "ch0:ga:adsenseAdUnitsViewed"
  :dim "ga:visitorGender"
  :per "last_1_month"}
```


#### AdSense eCPM by Other Category
  * `AdSense eCPM` (CURRENCY): The estimated cost per thousand page impressions. It is your AdSense Revenue per 1000 page impressions.
  * Calculated by *ga:adsenseRevenue/(ga:adsensePageImpressions/1000)*
  * `Other Category` (STRING): Indicates that users are more likely to be interested in learning about the specified category, and more likely to be ready to purchase.

``` clojure
{ :met "ch0:ga:adsenseECPM"
  :dim "ga:interestOtherCategory"
  :per "last_1_month"}
```


#### Search Depth by In-market Segment
  * `Search Depth` (FLOAT): The average number of pages people viewed after performing a search on your property.
  * Calculated by *ga:searchDepth / ga:searchUniques*
  * `In-market Segment` (STRING): Indicates that users are more likely to be ready to purchase products or services in the specified category.

``` clojure
{ :met "ch0:ga:avgSearchDepth"
  :dim "ga:interestInMarketCategory"
  :per "last_1_month"}
```


#### Screen Views by Affinity Category (reach)
  * `Screen Views` (INTEGER): The total number of screenviews.
  * `Affinity Category (reach)` (STRING): Indicates that users are more likely to be interested in learning about the specified category.

``` clojure
{ :met "ch0:ga:screenviews"
  :dim "ga:interestAffinityCategory"
  :per "last_1_month"}
```

### Goal Conversions


#### Goal 1 Abandoned Funnels by Landing Screen
  * `Goal 1 Abandoned Funnels` (INTEGER): The number of times visitors started conversion activity on the requested goal number without actually completing it.
  * Calculated by *(ga:goalXXStarts - ga:goalXXCompletions)*
  * `Landing Screen` (STRING): The name of the first screen viewed.

``` clojure
{ :met "ch0:ga:goalXXAbandons"
  :dim "ga:landingScreenName"
  :per "last_1_month"}
```


#### Goal 1 Conversion Rate by Mobile Device Marketing Name
  * `Goal 1 Conversion Rate` (PERCENT): The percentage of visits which resulted in a conversion to the requested goal number.
  * Calculated by *ga:goalXXCompletions / ga:visits*
  * `Mobile Device Marketing Name` (STRING): The marketing name used for the mobile device.

``` clojure
{ :met "ch0:ga:goalXXConversionRate"
  :dim "ga:mobileDeviceMarketingName"
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


#### Goal Starts by Originating Social Action
  * `Goal Starts` (INTEGER): The total number of starts for all goals defined for your profile.
  * `Originating Social Action` (STRING): For a social data hub activity, this value represents the type of social action associated with the activity (e.g. vote, comment, +1, etc.).

``` clojure
{ :met "ch0:ga:goalStartsAll"
  :dim "ga:socialActivityAction"
  :per "last_1_month"}
```


#### Total Abandonment Rate by Day Index
  * `Total Abandonment Rate` (PERCENT): The rate at which goals were abandoned.
  * Calculated by *((ga:goalStartsAll - ga:goalCompletionsAll)) / (ga:goalStartsAll)*
  * `Day Index` (STRING): Index for each day in the specified date range. Index for the first day (i.e., start-date) in the date range is 0, 1 for the second day, and so on.

``` clojure
{ :met "ch0:ga:goalAbandonRateAll"
  :dim "ga:nthDay"
  :per "last_1_month"}
```


#### Abandoned Funnels by Device Category
  * `Abandoned Funnels` (INTEGER): The overall number of times visitors started goals without actually completing them.
  * Calculated by *(ga:goalStartsAll - ga:goalCompletionsAll)*
  * `Device Category` (STRING): The type of device: desktop, tablet, or mobile.

``` clojure
{ :met "ch0:ga:goalAbandonsAll"
  :dim "ga:deviceCategory"
  :per "last_1_month"}
```


#### Goal 1 Value by App ID
  * `Goal 1 Value` (CURRENCY): The total numeric value for the requested goal number.
  * `App ID` (STRING): The ID of the application.

``` clojure
{ :met "ch0:ga:goalXXValue"
  :dim "ga:appId"
  :per "last_1_month"}
```


#### Goal 1 Completions by Custom Dimension 
  * `Goal 1 Completions` (INTEGER): The total number of completions for the requested goal number.
  * `Custom Dimension ` (STRING): The name of the requested custom dimension, where XX refers the number/index of the custom dimension.

``` clojure
{ :met "ch0:ga:goalXXCompletions"
  :dim "ga:dimensionXX"
  :per "last_1_month"}
```


#### Per Visit Goal Value by Goal Completion Location
  * `Per Visit Goal Value` (CURRENCY): The average goal value of a visit to your property.
  * Calculated by *(ga:goalValueAll / ga:visits)*
  * `Goal Completion Location` (STRING): The page path or screen name that matched any destination type goal completion.

``` clojure
{ :met "ch0:ga:goalValuePerVisit"
  :dim "ga:goalCompletionLocation"
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


#### Goal 1 Abandonment Rate by Visitor Type
  * `Goal 1 Abandonment Rate` (PERCENT): The rate at which the requested goal number was abandoned.
  * Calculated by *((ga:goalXXStarts - ga:goalXXCompletions)) / (ga:goalXXStarts)*
  * `Visitor Type` (STRING): A boolean indicating if a visitor is new or returning. Possible values: New Visitor, Returning Visitor.

``` clojure
{ :met "ch0:ga:goalXXAbandonRate"
  :dim "ga:visitorType"
  :per "last_1_month"}
```


#### Goal Conversion Rate by Goal Previous Step - 1
  * `Goal Conversion Rate` (PERCENT): The percentage of visits which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:visits*
  * `Goal Previous Step - 1` (STRING): The page path or screen name that matched any destination type goal, one step prior to the goal completion location.

``` clojure
{ :met "ch0:ga:goalConversionRateAll"
  :dim "ga:goalPreviousStep1"
  :per "last_1_month"}
```


#### Goal 1 Starts by AdWords Criteria ID
  * `Goal 1 Starts` (INTEGER): The total number of starts for the requested goal number.
  * `AdWords Criteria ID` (STRING): A string. Corresponds to AdWords API Criterion.id.

``` clojure
{ :met "ch0:ga:goalXXStarts"
  :dim "ga:adwordsCriteriaID"
  :per "last_1_month"}
```

### Internal Search


#### Results Pageviews / Search by Start Page
  * `Results Pageviews / Search` (FLOAT): The average number of times people viewed a search results page after performing a search.
  * Calculated by *ga:searchResultViews / ga:searchUniques*
  * `Start Page` (STRING): A page where the user initiated an internal search on your property.

``` clojure
{ :met "ch0:ga:avgSearchResultViews"
  :dim "ga:searchStartPage"
  :per "last_1_month"}
```


#### Search Depth by Social Network
  * `Search Depth` (FLOAT): The average number of pages people viewed after performing a search on your property.
  * Calculated by *ga:searchDepth / ga:searchUniques*
  * `Social Network` (STRING): Name of the social network. This can be related to the referring social network for traffic sources, or to the social network for social data hub activities. E.g. Google+, Blogger, etc.

``` clojure
{ :met "ch0:ga:avgSearchDepth"
  :dim "ga:socialNetwork"
  :per "last_1_month"}
```


#### Total Unique Searches by Custom Variable (Key 1)
  * `Total Unique Searches` (INTEGER): The total number of unique keywords from internal searches within a session. For example if "shoes" was searched for 3 times in a session, it will be only counted once.
  * `Custom Variable (Key 1)` (STRING): The name for the requested custom variable.

``` clojure
{ :met "ch0:ga:searchUniques"
  :dim "ga:customVarNameXX"
  :per "last_1_month"}
```


#### Search Depth by Search Term
  * `Search Depth` (INTEGER): The average number of subsequent page views made on your property after a use of your internal search feature.
  * `Search Term` (STRING): Search terms used by visitors within your property.

``` clojure
{ :met "ch0:ga:searchDepth"
  :dim "ga:searchKeyword"
  :per "last_1_month"}
```


#### Per Search Goal Value by Event Action
  * `Per Search Goal Value` (CURRENCY): The average goal value of a search on your property.
  * Calculated by *ga:goalValueAll / ga:searchUniques*
  * `Event Action` (STRING): The action of the event.

``` clojure
{ :met "ch0:ga:goalValueAllPerSearch"
  :dim "ga:eventAction"
  :per "last_1_month"}
```


#### Results Pageviews by Medium
  * `Results Pageviews` (INTEGER): The number of times a search result page was viewed after performing a search.
  * `Medium` (STRING): The type of referrals to your property. When using manual campaign tracking, the value of the utm_medium campaign tracking parameter. When using AdWords autotagging, the value is ppc. If the user comes from a search engine detected by Google Analytics, the value is organic. If the referrer is not a search engine, the value is referral. If the visitor came directly to the property, and document.referrer is empty, the value is (none).

``` clojure
{ :met "ch0:ga:searchResultViews"
  :dim "ga:medium"
  :per "last_1_month"}
```


#### Time after Search by Site Search Status
  * `Time after Search` (TIME): The visit duration to your property where a use of your internal search feature occurred.
  * `Site Search Status` (STRING): A boolean to distinguish whether internal search was used in a session. Values are Visits With Site Search and Visits Without Site Search.

``` clojure
{ :met "ch0:ga:searchDuration"
  :dim "ga:searchUsed"
  :per "last_1_month"}
```


#### % Visits with Search by Day of Week Name
  * `% Visits with Search` (PERCENT): The percentage of visits with search.
  * Calculated by *ga:searchVisits / ga:visits*
  * `Day of Week Name` (STRING): The name of the day of the week (in English).

``` clojure
{ :met "ch0:ga:percentVisitsWithSearch"
  :dim "ga:dayOfWeekName"
  :per "last_1_month"}
```


#### Site Search Goal 1 Conversion Rate by Language
  * `Site Search Goal 1 Conversion Rate` (PERCENT): The percentage of search visits (i.e., visits that included at least one search) which resulted in a conversion to the requested goal number.
  * Calculated by *ga:goalXXCompletions / ga:searchUniques*
  * `Language` (STRING): The language provided by the HTTP Request for the browser. Values are given as an ISO-639 code (e.g. en-gb for British English).

``` clojure
{ :met "ch0:ga:searchGoalXXConversionRate"
  :dim "ga:language"
  :per "last_1_month"}
```


#### Site Search Goal Conversion Rate by Timing Label
  * `Site Search Goal Conversion Rate` (PERCENT): The percentage of search visits (i.e., visits that included at least one search) which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:searchUniques*
  * `Timing Label` (STRING): The name of the resource's action being tracked.

``` clojure
{ :met "ch0:ga:searchGoalConversionRateAll"
  :dim "ga:userTimingLabel"
  :per "last_1_month"}
```


#### Search Exits by Day of Week Name
  * `Search Exits` (INTEGER): The number of exits on your site that occurred following a search result from your internal search feature.
  * `Day of Week Name` (STRING): The name of the day of the week (in English).

``` clojure
{ :met "ch0:ga:searchExits"
  :dim "ga:dayOfWeekName"
  :per "last_1_month"}
```


#### Time after Search by Operating System Version
  * `Time after Search` (TIME): The average amount of time people spent on your property after searching.
  * Calculated by *ga:searchDuration / ga:searchUniques*
  * `Operating System Version` (STRING): The version of the operating system used by your visitors, such as XP for Windows or PPC for Macintosh.

``` clojure
{ :met "ch0:ga:avgSearchDuration"
  :dim "ga:operatingSystemVersion"
  :per "last_1_month"}
```


#### Search Refinements by Count of Visits
  * `Search Refinements` (INTEGER): The total number of times a refinement (transition) occurs between internal search keywords within a session. For example if the sequence of keywords is: "shoes", "shoes", "pants", "pants", this metric will be one because the transition between "shoes" and "pants" is different.
  * `Count of Visits` (STRING): The visit index for a visitor to your property. Each visit from a unique visitor will get its own incremental index starting from 1 for the first visit. Subsequent visits do not change previous visit indicies. For example, if a certain visitor has 4 visits to your website, visitCount for that visitor will have 4 distinct values of '1' through '4'.

``` clojure
{ :met "ch0:ga:searchRefinements"
  :dim "ga:visitCount"
  :per "last_1_month"}
```


#### % Search Exits by Destination Page
  * `% Search Exits` (PERCENT): The percentage of searches that resulted in an immediate exit from your property.
  * Calculated by *ga:searchExits / ga:searchUniques*
  * `Destination Page` (STRING): A page that the user visited after performing an internal search on your property.

``` clojure
{ :met "ch0:ga:searchExitRate"
  :dim "ga:searchDestinationPage"
  :per "last_1_month"}
```


#### % Search Refinements by Refined Keyword
  * `% Search Refinements` (PERCENT): The percentage of number of times a refinement (i.e., transition) occurs between internal search keywords within a session.
  * Calculated by *ga:searchRefinements / ga:searchResultViews*
  * `Refined Keyword` (STRING): Subsequent keyword search terms or strings entered by users after a given initial string search.

``` clojure
{ :met "ch0:ga:percentSearchRefinements"
  :dim "ga:searchKeywordRefinement"
  :per "last_1_month"}
```


#### Visits with Search by Targeting Type
  * `Visits with Search` (INTEGER): The total number of sessions that included an internal search
  * `Targeting Type` (STRING): How your AdWords ads were targeted (keyword, placement, and vertical targeting, etc.).

``` clojure
{ :met "ch0:ga:searchVisits"
  :dim "ga:adTargetingType"
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


#### Unique Events by Event Action
  * `Unique Events` (INTEGER): The total number of unique events for the profile, across all categories.
  * `Event Action` (STRING): The action of the event.

``` clojure
{ :met "ch0:ga:uniqueEvents"
  :dim "ga:eventAction"
  :per "last_1_month"}
```


#### Event Value by App Name
  * `Event Value` (INTEGER): The total value of events for the profile.
  * `App Name` (STRING): The name of the application.

``` clojure
{ :met "ch0:ga:eventValue"
  :dim "ga:appName"
  :per "last_1_month"}
```


#### Total Events by Targeting Type
  * `Total Events` (INTEGER): The total number of events for the profile, across all categories.
  * `Targeting Type` (STRING): How your AdWords ads were targeted (keyword, placement, and vertical targeting, etc.).

``` clojure
{ :met "ch0:ga:totalEvents"
  :dim "ga:adTargetingType"
  :per "last_1_month"}
```


#### Events / Visit by Ad Slot Position
  * `Events / Visit` (FLOAT): The average number of events per visit with event.
  * Calculated by *ga:totalEvents / ga:visitsWithEvent*
  * `Ad Slot Position` (STRING): The ad slot positions in which your AdWords ads appeared (1-8).

``` clojure
{ :met "ch0:ga:eventsPerVisitWithEvent"
  :dim "ga:adSlotPosition"
  :per "last_1_month"}
```


#### Visits with Event by AdWords Criteria ID
  * `Visits with Event` (INTEGER): The total number of visits with events.
  * `AdWords Criteria ID` (STRING): A string. Corresponds to AdWords API Criterion.id.

``` clojure
{ :met "ch0:ga:visitsWithEvent"
  :dim "ga:adwordsCriteriaID"
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
  * Calculated by *ga:screenviews / ga:visits*
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


#### Entrances / Pageviews by Exit Screen
  * `Entrances / Pageviews` (PERCENT): The percentage of pageviews in which this page was the entrance.
  * Calculated by *ga:entrances / ga:pageviews*
  * `Exit Screen` (STRING): The name of the screen when the user exited the application.

``` clojure
{ :met "ch0:ga:entranceRate"
  :dim "ga:exitScreenName"
  :per "last_1_month"}
```


#### Time after Search by App Version
  * `Time after Search` (TIME): The visit duration to your property where a use of your internal search feature occurred.
  * `App Version` (STRING): The version of the application.

``` clojure
{ :met "ch0:ga:searchDuration"
  :dim "ga:appVersion"
  :per "last_1_month"}
```


#### Goal Starts by App ID
  * `Goal Starts` (INTEGER): The total number of starts for all goals defined for your profile.
  * `App ID` (STRING): The ID of the application.

``` clojure
{ :met "ch0:ga:goalStartsAll"
  :dim "ga:appId"
  :per "last_1_month"}
```

### Ecommerce


#### Tax by Display Name
  * `Tax` (CURRENCY): The total amount of tax.
  * `Display Name` (STRING): For a social data hub activity, this value represents the title of the social activity posted by the social network user.

``` clojure
{ :met "ch0:ga:transactionTax"
  :dim "ga:socialActivityDisplayName"
  :per "last_1_month"}
```


#### Local Product Revenue by Affiliation
  * `Local Product Revenue` (CURRENCY): Product revenue in local currency.
  * `Affiliation` (STRING): Typically used to designate a supplying company or brick and mortar location; product affiliation.

``` clojure
{ :met "ch0:ga:localItemRevenue"
  :dim "ga:affiliation"
  :per "last_1_month"}
```


#### Shipping by Visits to Transaction
  * `Shipping` (CURRENCY): The total cost of shipping.
  * `Visits to Transaction` (STRING): The number of visits between users' purchases and the related campaigns that lead to the purchases.

``` clojure
{ :met "ch0:ga:transactionShipping"
  :dim "ga:visitsToTransaction"
  :per "last_1_month"}
```


#### Average Price by Landing Screen
  * `Average Price` (CURRENCY): The average revenue per item.
  * Calculated by *ga:itemRevenue / ga:itemQuantity*
  * `Landing Screen` (STRING): The name of the first screen viewed.

``` clojure
{ :met "ch0:ga:revenuePerItem"
  :dim "ga:landingScreenName"
  :per "last_1_month"}
```


#### Total Value by Continent
  * `Total Value` (CURRENCY): Total value for your property (including total revenue and total goal value).
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll)*
  * `Continent` (STRING): The continents of property visitors, derived from IP addresses.

``` clojure
{ :met "ch0:ga:totalValue"
  :dim "ga:continent"
  :per "last_1_month"}
```


#### Average QTY by Language
  * `Average QTY` (FLOAT): The average quantity of this item (or group of items) sold per purchase.
  * Calculated by *ga:itemQuantity / ga:uniquePurchases*
  * `Language` (STRING): The language provided by the HTTP Request for the browser. Values are given as an ISO-639 code (e.g. en-gb for British English).

``` clojure
{ :met "ch0:ga:itemsPerPurchase"
  :dim "ga:language"
  :per "last_1_month"}
```


#### Quantity by Keyword
  * `Quantity` (INTEGER): The total number of items purchased. For example, if users purchase 2 frisbees and 5 tennis balls, 7 items have been purchased.
  * `Keyword` (STRING): When using manual campaign tracking, the value of the utm_term campaign tracking parameter. When using AdWords autotagging or if a visitor used organic search to reach your property, the keywords used by visitors to reach your property. Otherwise the value is (not set).

``` clojure
{ :met "ch0:ga:itemQuantity"
  :dim "ga:keyword"
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


#### Transactions by Product
  * `Transactions` (INTEGER): The total number of transactions.
  * `Product` (STRING): The product name for purchased items as supplied by your ecommerce tracking application.

``` clojure
{ :met "ch0:ga:transactions"
  :dim "ga:productName"
  :per "last_1_month"}
```


#### Per Visit Value by Days to Transaction
  * `Per Visit Value` (CURRENCY): Average transaction revenue for a visit to your property.
  * Calculated by *ga:transactionRevenue / ga:visits*
  * `Days to Transaction` (STRING): The number of days between users' purchases and the related campaigns that lead to the purchases.

``` clojure
{ :met "ch0:ga:transactionRevenuePerVisit"
  :dim "ga:daysToTransaction"
  :per "last_1_month"}
```


#### Local Shipping by AdWords Criteria ID
  * `Local Shipping` (CURRENCY): Transaction shipping cost in local currency.
  * `AdWords Criteria ID` (STRING): A string. Corresponds to AdWords API Criterion.id.

``` clojure
{ :met "ch0:ga:localTransactionShipping"
  :dim "ga:adwordsCriteriaID"
  :per "last_1_month"}
```


#### Ecommerce Conversion Rate by Product
  * `Ecommerce Conversion Rate` (PERCENT): The average number of transactions for a visit to your property.
  * Calculated by *ga:transactions / ga:visits*
  * `Product` (STRING): The product name for purchased items as supplied by your ecommerce tracking application.

``` clojure
{ :met "ch0:ga:transactionsPerVisit"
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


#### Average Order Value by Gender
  * `Average Order Value` (CURRENCY): The average revenue for an e-commerce transaction.
  * Calculated by *ga:transactionRevenue / ga:transactions*
  * `Gender` (STRING): Gender of visitor.

``` clojure
{ :met "ch0:ga:revenuePerTransaction"
  :dim "ga:visitorGender"
  :per "last_1_month"}
```


#### Local Tax by Social Action
  * `Local Tax` (CURRENCY): Transaction tax in local currency.
  * `Social Action` (STRING): For social interactions, a value representing the social action being tracked (e.g. +1, bookmark)

``` clojure
{ :met "ch0:ga:localTransactionTax"
  :dim "ga:socialInteractionAction"
  :per "last_1_month"}
```


#### Revenue by Landing Screen
  * `Revenue` (CURRENCY): The total sale revenue provided in the transaction excluding shipping and tax.
  * `Landing Screen` (STRING): The name of the first screen viewed.

``` clojure
{ :met "ch0:ga:transactionRevenue"
  :dim "ga:landingScreenName"
  :per "last_1_month"}
```

### Social Activities


#### Visit Duration by Originating Social Action
  * `Visit Duration` (TIME): The total duration of visitor sessions represented in total seconds.
  * `Originating Social Action` (STRING): For a social data hub activity, this value represents the type of social action associated with the activity (e.g. vote, comment, +1, etc.).

``` clojure
{ :met "ch0:ga:timeOnSite"
  :dim "ga:socialActivityAction"
  :per "last_1_month"}
```


#### Avg. Server Connection Time (sec) by Social Network and Action
  * `Avg. Server Connection Time (sec)` (FLOAT): The average amount of time (in seconds) spent in establishing TCP connection for this page.
  * Calculated by *(ga:serverConnectionTime / ga:speedMetricsSample / 1000)*
  * `Social Network and Action` (STRING): For a social data hub activity, this value represents the type of social action and the social network where the activity originated.

``` clojure
{ :met "ch0:ga:avgServerConnectionTime"
  :dim "ga:socialActivityNetworkAction"
  :per "last_1_month"}
```


#### Search Depth by Social User Handle
  * `Search Depth` (INTEGER): The average number of subsequent page views made on your property after a use of your internal search feature.
  * `Social User Handle` (STRING): For a social data hub activity, this value represents the social network handle (e.g. name or ID) of the user who initiated the social activity.

``` clojure
{ :met "ch0:ga:searchDepth"
  :dim "ga:socialActivityUserHandle"
  :per "last_1_month"}
```


#### Total Abandonment Rate by Display Name
  * `Total Abandonment Rate` (PERCENT): The rate at which goals were abandoned.
  * Calculated by *((ga:goalStartsAll - ga:goalCompletionsAll)) / (ga:goalStartsAll)*
  * `Display Name` (STRING): For a social data hub activity, this value represents the title of the social activity posted by the social network user.

``` clojure
{ :met "ch0:ga:goalAbandonRateAll"
  :dim "ga:socialActivityDisplayName"
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


#### % Visits with Search by Social Activity Timestamp
  * `% Visits with Search` (PERCENT): The percentage of visits with search.
  * Calculated by *ga:searchVisits / ga:visits*
  * `Social Activity Timestamp` (STRING): For a social data hub activity, this value represents when the social activity occurred on the social network.

``` clojure
{ :met "ch0:ga:percentVisitsWithSearch"
  :dim "ga:socialActivityTimestamp"
  :per "last_1_month"}
```


#### Unique Screen Views by Social Tags Summary
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Social Tags Summary` (STRING): For a social data hub activity, this is a comma-separated set of tags associated with the social activity.

``` clojure
{ :met "ch0:ga:uniqueAppviews"
  :dim "ga:socialActivityTagsSummary"
  :per "last_1_month"}
```


#### Visits with Event by Shared URL
  * `Visits with Event` (INTEGER): The total number of visits with events.
  * `Shared URL` (STRING): For a social data hub activity, this value represents the URL shared by the associated social network user.

``` clojure
{ :met "ch0:ga:visitsWithEvent"
  :dim "ga:socialActivityContentUrl"
  :per "last_1_month"}
```


#### Avg. Document Interactive Time (sec) by Endorsing URL
  * `Avg. Document Interactive Time (sec)` (FLOAT): The average time (in seconds) it takes the browser to parse the document and execute deferred and parser-inserted scripts including the network time from the user's location to your server.
  * Calculated by *(ga:domInteractiveTime / ga:domLatencyMetricsSample / 1000)*
  * `Endorsing URL` (STRING): For a social data hub activity, this value represents the URL of the social activity (e.g. the Google+ post URL, the blog comment URL, etc.)

``` clojure
{ :met "ch0:ga:avgDomInteractiveTime"
  :dim "ga:socialActivityEndorsingUrl"
  :per "last_1_month"}
```


#### Crashes / Screen by Social Activity Post
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `Social Activity Post` (STRING): For a social data hub activity, this value represents the content of the social activity posted by the social network user (e.g. The message content of a Google+ post)

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:socialActivityPost"
  :per "last_1_month"}
```


#### Clicks by User Photo URL
  * `Clicks` (INTEGER): The total number of times users have clicked on an ad to reach your property.
  * `User Photo URL` (STRING): For a social data hub activity, this value represents the URL of the photo associated with the user's social network profile.

``` clojure
{ :met "ch0:ga:adClicks"
  :dim "ga:socialActivityUserPhotoUrl"
  :per "last_1_month"}
```

### Social Interactions


#### Actions Per Social Visit by Social Source and Action
  * `Actions Per Social Visit` (FLOAT): The number of social interactions per visit to your property.
  * Calculated by *ga:socialInteractions / ga:uniqueSocialInteractions*
  * `Social Source and Action` (STRING): For social interactions, a value representing the concatenation of the socialInteractionNetwork and socialInteractionAction action being tracked at this hit level (e.g. Google: +1)

``` clojure
{ :met "ch0:ga:socialInteractionsPerVisit"
  :dim "ga:socialInteractionNetworkAction"
  :per "last_1_month"}
```


#### Unique Social Actions by Social Action
  * `Unique Social Actions` (INTEGER): The number of sessions during which the specified social action(s) occurred at least once. This is based on the the unique combination of socialInteractionNetwork, socialInteractionAction, and socialInteractionTarget.
  * `Social Action` (STRING): For social interactions, a value representing the social action being tracked (e.g. +1, bookmark)

``` clojure
{ :met "ch0:ga:uniqueSocialInteractions"
  :dim "ga:socialInteractionAction"
  :per "last_1_month"}
```


#### Social Actions by Social Source
  * `Social Actions` (INTEGER): The total number of social interactions on your property.
  * `Social Source` (STRING): For social interactions, a value representing the social network being tracked.

``` clojure
{ :met "ch0:ga:socialInteractions"
  :dim "ga:socialInteractionNetwork"
  :per "last_1_month"}
```


#### Custom Metric  Value by Social Entity
  * `Custom Metric  Value` (INTEGER): The name of the requested custom metric, where XX refers the number/index of the custom metric.
  * `Social Entity` (STRING): For social interactions, a value representing the URL (or resource) which receives the social network action.

``` clojure
{ :met "ch0:ga:metricXX"
  :dim "ga:socialInteractionTarget"
  :per "last_1_month"}
```


#### Screens / Session by Social Type
  * `Screens / Session` (FLOAT): The average number of screenviews per session.
  * Calculated by *ga:screenviews / ga:visits*
  * `Social Type` (STRING): Engagement type. Possible values are "Socially Engaged" or "Not Socially Engaged".

``` clojure
{ :met "ch0:ga:appviewsPerVisit"
  :dim "ga:socialEngagementType"
  :per "last_1_month"}
```

### Geo Network


#### Bounce Rate by Latitude
  * `Bounce Rate` (PERCENT): The percentage of single-page visits (i.e., visits in which the person left your property from the first page).
  * Calculated by *ga:bounces / ga:visits*
  * `Latitude` (STRING): The approximate latitude of the visitor's city. Derived from IP address. Locations north of the equator are represented by positive values and locations south of the equator by negative values.

``` clojure
{ :met "ch0:ga:visitBounceRate"
  :dim "ga:latitude"
  :per "last_1_month"}
```


#### New Visits by Region
  * `New Visits` (INTEGER): The number of visitors whose visit to your property was marked as a first-time visit.
  * `Region` (STRING): The region of visitors to your property, derived from IP addresses. In the U.S., a region is a state, such as New York.

``` clojure
{ :met "ch0:ga:newVisits"
  :dim "ga:region"
  :per "last_1_month"}
```


#### Entrances / Pageviews by City
  * `Entrances / Pageviews` (PERCENT): The percentage of pageviews in which this page was the entrance.
  * Calculated by *ga:entrances / ga:pageviews*
  * `City` (STRING): The cities of property visitors, derived from IP addresses.

``` clojure
{ :met "ch0:ga:entranceRate"
  :dim "ga:city"
  :per "last_1_month"}
```


#### Document Interactive Time (ms) by Metro
  * `Document Interactive Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document (DOMInteractive), including the network time from the user's location to your server. At this time, the user can interact with the Document Object Model even though it is not fully loaded.
  * `Metro` (STRING): The Designated Market Area (DMA) from where traffic arrived on your property.

``` clojure
{ :met "ch0:ga:domInteractiveTime"
  :dim "ga:metro"
  :per "last_1_month"}
```


#### Local Shipping by Country / Territory
  * `Local Shipping` (CURRENCY): Transaction shipping cost in local currency.
  * `Country / Territory` (STRING): The countries of website visitors, derived from IP addresses.

``` clojure
{ :met "ch0:ga:localTransactionShipping"
  :dim "ga:country"
  :per "last_1_month"}
```


#### Screens / Session by Continent
  * `Screens / Session` (FLOAT): The average number of screenviews per session.
  * Calculated by *ga:screenviews / ga:visits*
  * `Continent` (STRING): The continents of property visitors, derived from IP addresses.

``` clojure
{ :met "ch0:ga:appviewsPerVisit"
  :dim "ga:continent"
  :per "last_1_month"}
```


#### Local Revenue by Network Domain
  * `Local Revenue` (CURRENCY): Transaction revenue in local currency.
  * `Network Domain` (STRING): The domain name of the ISPs used by visitors to your property. This is derived from the domain name registered to the IP address.

``` clojure
{ :met "ch0:ga:localTransactionRevenue"
  :dim "ga:networkDomain"
  :per "last_1_month"}
```


#### AdSense Revenue by Sub Continent Region
  * `AdSense Revenue` (CURRENCY): The total revenue from AdSense ads.
  * `Sub Continent Region` (STRING): The sub-continent of visitors, derived from IP addresses. For example, Polynesia or Northern Europe.

``` clojure
{ :met "ch0:ga:adsenseRevenue"
  :dim "ga:subContinent"
  :per "last_1_month"}
```


#### % Exit by Longitude
  * `% Exit` (PERCENT): The percentage of exits from your property that occurred out of the total page views.
  * Calculated by *ga:exits / (ga:pageviews + ga:screenviews)*
  * `Longitude` (STRING): The approximate longitude of the visitor's city. Derived from IP address. Locations east of the meridian are represented by positive values and locations west of the meridian by negative values.

``` clojure
{ :met "ch0:ga:exitRate"
  :dim "ga:longitude"
  :per "last_1_month"}
```


#### Crashes / Screen by Service Provider
  * `Crashes / Screen` (PERCENT): The number of fatal exceptions thrown divided by the number of screenviews.
  * Calculated by *ga:fatalExceptions / ga:screenviews*
  * `Service Provider` (STRING): The name of service providers used to reach your property. For example, if most visitors to your website come via the major service providers for cable internet, you will see the names of those cable service providers in this element.

``` clojure
{ :met "ch0:ga:fatalExceptionsPerScreenview"
  :dim "ga:networkLocation"
  :per "last_1_month"}
```

### System


#### AdSense Page Impressions by Flash Version
  * `AdSense Page Impressions` (INTEGER): The number of pageviews during which an AdSense ad was displayed. A page impression can have multiple Ad Units.
  * `Flash Version` (STRING): The versions of Flash supported by visitors' browsers, including minor versions.

``` clojure
{ :met "ch0:ga:adsensePageImpressions"
  :dim "ga:flashVersion"
  :per "last_1_month"}
```


#### Margin by Java Support
  * `Margin` (PERCENT): The overall transaction profit margin.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / (ga:transactionRevenue + ga:goalValueAll)*
  * `Java Support` (STRING): Indicates Java support for visitors' browsers. The possible values are Yes or No where the first letter must be capitalized.

``` clojure
{ :met "ch0:ga:margin"
  :dim "ga:javaEnabled"
  :per "last_1_month"}
```


#### Page Download Time (ms) by Screen Resolution
  * `Page Download Time (ms)` (INTEGER): The total amount of time (in milliseconds) to download this page among all samples.
  * `Screen Resolution` (STRING): The screen resolution of visitors' monitors, as retrieved from the DOM of the visitor's browser. For example: 1024x738.

``` clojure
{ :met "ch0:ga:pageDownloadTime"
  :dim "ga:screenResolution"
  :per "last_1_month"}
```


#### Goal Conversion Rate by Language
  * `Goal Conversion Rate` (PERCENT): The percentage of visits which resulted in a conversion to at least one of your goals.
  * Calculated by *ga:goalCompletionsAll / ga:visits*
  * `Language` (STRING): The language provided by the HTTP Request for the browser. Values are given as an ISO-639 code (e.g. en-gb for British English).

``` clojure
{ :met "ch0:ga:goalConversionRateAll"
  :dim "ga:language"
  :per "last_1_month"}
```


#### Unique Pageviews by Screen Colors
  * `Unique Pageviews` (INTEGER): The number of different (unique) pages within a session. This takes into both the pagePath and pageTitle to determine uniqueness.
  * `Screen Colors` (STRING): The color depth of visitors' monitors, as retrieved from the DOM of the visitor's browser. For example 4-bit, 8-bit, 24-bit, or undefined-bit.

``` clojure
{ :met "ch0:ga:uniquePageviews"
  :dim "ga:screenColors"
  :per "last_1_month"}
```

### Platform or Device


#### Search Depth by Mobile Device Model
  * `Search Depth` (INTEGER): The average number of subsequent page views made on your property after a use of your internal search feature.
  * `Mobile Device Model` (STRING): Mobile device model

``` clojure
{ :met "ch0:ga:searchDepth"
  :dim "ga:mobileDeviceModel"
  :per "last_1_month"}
```


#### Per Visit Value by Mobile Device Branding
  * `Per Visit Value` (CURRENCY): Average transaction revenue for a visit to your property.
  * Calculated by *ga:transactionRevenue / ga:visits*
  * `Mobile Device Branding` (STRING): Mobile manufacturer or branded name.

``` clojure
{ :met "ch0:ga:transactionRevenuePerVisit"
  :dim "ga:mobileDeviceBranding"
  :per "last_1_month"}
```


#### Document Interactive Time (ms) by Mobile Input Selector
  * `Document Interactive Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document (DOMInteractive), including the network time from the user's location to your server. At this time, the user can interact with the Document Object Model even though it is not fully loaded.
  * `Mobile Input Selector` (STRING): Selector used on the mobile device (e.g.: touchscreen, joystick, clickwheel, stylus).

``` clojure
{ :met "ch0:ga:domInteractiveTime"
  :dim "ga:mobileInputSelector"
  :per "last_1_month"}
```


#### Time after Search by Mobile Device Info
  * `Time after Search` (TIME): The average amount of time people spent on your property after searching.
  * Calculated by *ga:searchDuration / ga:searchUniques*
  * `Mobile Device Info` (STRING): The branding, model, and marketing name used to identify the mobile device.

``` clojure
{ :met "ch0:ga:avgSearchDuration"
  :dim "ga:mobileDeviceInfo"
  :per "last_1_month"}
```


#### Visits with Event by Browser Version
  * `Visits with Event` (INTEGER): The total number of visits with events.
  * `Browser Version` (STRING): The browser versions used by visitors to your website. For example, 2.0.0.14

``` clojure
{ :met "ch0:ga:visitsWithEvent"
  :dim "ga:browserVersion"
  :per "last_1_month"}
```


#### Screens / Session by Device Category
  * `Screens / Session` (FLOAT): The average number of screenviews per session.
  * Calculated by *ga:screenviews / ga:visits*
  * `Device Category` (STRING): The type of device: desktop, tablet, or mobile.

``` clojure
{ :met "ch0:ga:screenviewsPerSession"
  :dim "ga:deviceCategory"
  :per "last_1_month"}
```


#### ROI by Browser
  * `ROI` (PERCENT): Returns on Investment is overall transaction profit divided by derived advertising cost.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / ga:adCost*
  * `Browser` (STRING): The names of browsers used by visitors to your website. For example, Internet Explorer or Firefox.

``` clojure
{ :met "ch0:ga:ROI"
  :dim "ga:browser"
  :per "last_1_month"}
```


#### Average Order Value by Operating System Version
  * `Average Order Value` (CURRENCY): The average revenue for an e-commerce transaction.
  * Calculated by *ga:transactionRevenue / ga:transactions*
  * `Operating System Version` (STRING): The version of the operating system used by your visitors, such as XP for Windows or PPC for Macintosh.

``` clojure
{ :met "ch0:ga:revenuePerTransaction"
  :dim "ga:operatingSystemVersion"
  :per "last_1_month"}
```


#### Entrances by Mobile Device Marketing Name
  * `Entrances` (INTEGER): The number of entrances to your property measured as the first pageview in a session. Typically used with landingPagePath
  * `Mobile Device Marketing Name` (STRING): The marketing name used for the mobile device.

``` clojure
{ :met "ch0:ga:entrances"
  :dim "ga:mobileDeviceMarketingName"
  :per "last_1_month"}
```


#### Avg. Time on Screen by Operating System
  * `Avg. Time on Screen` (TIME): The average amount of time users spent on a screen in seconds.
  * `Operating System` (STRING): The operating system used by your visitors. For example, Windows, Linux , Macintosh, iPhone, iPod.

``` clojure
{ :met "ch0:ga:avgScreenviewDuration"
  :dim "ga:operatingSystem"
  :per "last_1_month"}
```

### Session


#### Visits by Screen Depth
  * `Visits` (INTEGER): Counts the total number of sessions.
  * `Screen Depth` (STRING): The number of screenviews per session reported as a string. Can be useful for historgrams.

``` clojure
{ :met "ch0:ga:visits"
  :dim "ga:screenDepth"
  :per "last_1_month"}
```


#### Visit Duration by Week of Year
  * `Visit Duration` (TIME): The total duration of visitor sessions represented in total seconds.
  * `Week of Year` (STRING): Combined values of ga:year and ga:week.

``` clojure
{ :met "ch0:ga:timeOnSite"
  :dim "ga:yearWeek"
  :per "last_1_month"}
```


#### Avg. Visit Duration by Currency Code
  * `Avg. Visit Duration` (TIME): The average duration visitor sessions represented in total seconds.
  * Calculated by *ga:timeOnSite / ga:visits*
  * `Currency Code` (STRING): The local currency code of the transaction based on ISO 4217 standard.

``` clojure
{ :met "ch0:ga:avgTimeOnSite"
  :dim "ga:currencyCode"
  :per "last_1_month"}
```


#### Bounces by Browser
  * `Bounces` (INTEGER): The total number of single page (or single engagement hit) sessions for your property.
  * `Browser` (STRING): The names of browsers used by visitors to your website. For example, Internet Explorer or Firefox.

``` clojure
{ :met "ch0:ga:bounces"
  :dim "ga:browser"
  :per "last_1_month"}
```


#### Bounce Rate by Region
  * `Bounce Rate` (PERCENT): The percentage of single-page visits (i.e., visits in which the person left your property from the first page).
  * Calculated by *ga:bounces / ga:visits*
  * `Region` (STRING): The region of visitors to your property, derived from IP addresses. In the U.S., a region is a state, such as New York.

``` clojure
{ :met "ch0:ga:visitBounceRate"
  :dim "ga:region"
  :per "last_1_month"}
```

### Time


#### Unique Screen Views by Date
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Date` (STRING): The date of the visit formatted as YYYYMMDD.

``` clojure
{ :met "ch0:ga:uniqueScreenviews"
  :dim "ga:date"
  :per "last_1_month"}
```


#### Exits by Month of the year
  * `Exits` (INTEGER): The number of exits from your property.
  * `Month of the year` (STRING): The month of the visit. A two digit integer from 01 to 12.

``` clojure
{ :met "ch0:ga:exits"
  :dim "ga:month"
  :per "last_1_month"}
```


#### Avg. Domain Lookup Time (sec) by ISO Week of ISO Year
  * `Avg. Domain Lookup Time (sec)` (FLOAT): The average amount of time (in seconds) spent in DNS lookup for this page.
  * Calculated by *(ga:domainLookupTime / ga:speedMetricsSample / 1000)*
  * `ISO Week of ISO Year` (STRING): Combined values of ga:isoYear and ga:isoWeek.

``` clojure
{ :met "ch0:ga:avgDomainLookupTime"
  :dim "ga:isoYearIsoWeek"
  :per "last_1_month"}
```


#### Search Depth by Minute Index
  * `Search Depth` (INTEGER): The average number of subsequent page views made on your property after a use of your internal search feature.
  * `Minute Index` (STRING): Index for each minute in the specified date range. Index for the first minute of first day (i.e., start-date) in the date range is 0, 1 for the next minute, and so on.

``` clojure
{ :met "ch0:ga:searchDepth"
  :dim "ga:nthMinute"
  :per "last_1_month"}
```


#### User Timing Sample by Week of the Year
  * `User Timing Sample` (INTEGER): The number of hits that were sent for a particular userTimingCategory, userTimingLabel, and userTimingVariable.
  * `Week of the Year` (STRING): The week of the visit. A two-digit number from 01 to 53. Each week starts on Sunday.

``` clojure
{ :met "ch0:ga:userTimingSample"
  :dim "ga:week"
  :per "last_1_month"}
```


#### Document Content Loaded Time (ms) by Hour of Day
  * `Document Content Loaded Time (ms)` (INTEGER): The time the browser takes (in milliseconds) to parse the document and execute deferred and parser-inserted scripts (DOMContentLoaded), including the network time from the user's location to your server. Parsing of the document is finished, the Document Object Model is ready, but referenced style sheets, images, and subframes may not be finished loading. This event is often the starting point for javascript framework execution, e.g., JQuery's onready() callback, etc.
  * `Hour of Day` (STRING): Combined values of ga:date and ga:hour.

``` clojure
{ :met "ch0:ga:domContentLoadedTime"
  :dim "ga:dateHour"
  :per "last_1_month"}
```


#### Bounces by Day of Week
  * `Bounces` (INTEGER): The total number of single page (or single engagement hit) sessions for your property.
  * `Day of Week` (STRING): The day of the week. A one-digit number from 0 (Sunday) to 6 (Saturday).

``` clojure
{ :met "ch0:ga:bounces"
  :dim "ga:dayOfWeek"
  :per "last_1_month"}
```


#### DOM Latency Metrics Sample by Hour
  * `DOM Latency Metrics Sample` (INTEGER): The sample set (or count) of pageviews used to calculate the averages for site speed DOM metrics. This metric is used in the avgDomContentLoadedTime and avgDomInteractiveTime calculations.
  * `Hour` (STRING): A two-digit hour of the day ranging from 00-23 in the timezone configured for the account. This value is also corrected for daylight savings time, adhering to all local rules for daylight savings time. If your timezone follows daylight savings time, there will be an apparent bump in the number of visits during the change-over hour (e.g. between 1:00 and 2:00) for the day per year when that hour repeats. A corresponding hour with zero visits will occur at the opposite changeover. (Google Analytics does not track visitor time more precisely than hours.)

``` clojure
{ :met "ch0:ga:domLatencyMetricsSample"
  :dim "ga:hour"
  :per "last_1_month"}
```


#### Unique Screen Views by Month Index
  * `Unique Screen Views` (INTEGER): The number of different (unique) screenviews within a session.
  * `Month Index` (STRING): Index for each month in the specified date range. Index for the first month in the date range is 0, 1 for the second month, and so on. The index corresponds to month entries.

``` clojure
{ :met "ch0:ga:uniqueAppviews"
  :dim "ga:nthMonth"
  :per "last_1_month"}
```


#### Time on Page by Week Index
  * `Time on Page` (TIME): How long a visitor spent on a particular page in seconds. Calculated by subtracting the initial view time for a particular page from the initial view time for a subsequent page. Thus, this metric does not apply to exit pages for your property.
  * `Week Index` (STRING): Index for each week in the specified date range. Index for the first week in the date range is 0, 1 for the second week, and so on. The index corresponds to week entries.

``` clojure
{ :met "ch0:ga:timeOnPage"
  :dim "ga:nthWeek"
  :per "last_1_month"}
```


#### Server Response Time (ms) by Day of Week Name
  * `Server Response Time (ms)` (INTEGER): The total amount of time (in milliseconds) your server takes to respond to a user request among all samples, including the network time from user's location to your server.
  * `Day of Week Name` (STRING): The name of the day of the week (in English).

``` clojure
{ :met "ch0:ga:serverResponseTime"
  :dim "ga:dayOfWeekName"
  :per "last_1_month"}
```


#### Avg. Time on Page by ISO Week of the Year
  * `Avg. Time on Page` (TIME): The average amount of time visitors spent viewing this page or a set of pages.
  * Calculated by *ga:timeOnPage / (ga:pageviews - ga:exits)*
  * `ISO Week of the Year` (STRING): The ISO week number, where each week starts with a Monday. Details: http://en.wikipedia.org/wiki/ISO_week_date. ga:isoWeek should only be used with ga:isoYear since ga:year represents gregorian calendar.

``` clojure
{ :met "ch0:ga:avgTimeOnPage"
  :dim "ga:isoWeek"
  :per "last_1_month"}
```


#### ROI by Day of the month
  * `ROI` (PERCENT): Returns on Investment is overall transaction profit divided by derived advertising cost.
  * Calculated by *(ga:transactionRevenue + ga:goalValueAll - ga:adCost) / ga:adCost*
  * `Day of the month` (STRING): The day of the month. A two-digit number from 01 to 31.

``` clojure
{ :met "ch0:ga:ROI"
  :dim "ga:day"
  :per "last_1_month"}
```


#### Average Order Value by Day Index
  * `Average Order Value` (CURRENCY): The average revenue for an e-commerce transaction.
  * Calculated by *ga:transactionRevenue / ga:transactions*
  * `Day Index` (STRING): Index for each day in the specified date range. Index for the first day (i.e., start-date) in the date range is 0, 1 for the second day, and so on.

``` clojure
{ :met "ch0:ga:revenuePerTransaction"
  :dim "ga:nthDay"
  :per "last_1_month"}
```


#### AdSense Revenue by ISO Year
  * `AdSense Revenue` (CURRENCY): The total revenue from AdSense ads.
  * `ISO Year` (STRING): The ISO year of the visit. Details: http://en.wikipedia.org/wiki/ISO_week_date. ga:isoYear should only be used with ga:isoWeek since ga:week represents gregorian calendar.

``` clojure
{ :met "ch0:ga:adsenseRevenue"
  :dim "ga:isoYear"
  :per "last_1_month"}
```


#### Avg. Time on Screen by Week of Year
  * `Avg. Time on Screen` (TIME): The average amount of time users spent on a screen in seconds.
  * `Week of Year` (STRING): Combined values of ga:year and ga:week.

``` clojure
{ :met "ch0:ga:avgScreenviewDuration"
  :dim "ga:yearWeek"
  :per "last_1_month"}
```


#### AdSense Ads Viewed by Year
  * `AdSense Ads Viewed` (INTEGER): The number of AdSense ads viewed. Multiple ads can be displayed within an Ad Unit.
  * `Year` (STRING): The year of the visit. A four-digit year from 2005 to the current year.

``` clojure
{ :met "ch0:ga:adsenseAdsViewed"
  :dim "ga:year"
  :per "last_1_month"}
```

### Content Experiments


#### Average QTY by Experiment ID
  * `Average QTY` (FLOAT): The average quantity of this item (or group of items) sold per purchase.
  * Calculated by *ga:itemQuantity / ga:uniquePurchases*
  * `Experiment ID` (STRING): The visitor-scoped id of the content experiment that the user was exposed to when the metrics were reported.

``` clojure
{ :met "ch0:ga:itemsPerPurchase"
  :dim "ga:experimentId"
  :per "last_1_month"}
```


#### Goal 1 Abandonment Rate by Variation
  * `Goal 1 Abandonment Rate` (PERCENT): The rate at which the requested goal number was abandoned.
  * Calculated by *((ga:goalXXStarts - ga:goalXXCompletions)) / (ga:goalXXStarts)*
  * `Variation` (STRING): The visitor-scoped id of the particular variation that the user was exposed to during a content experiment.

``` clojure
{ :met "ch0:ga:goalXXAbandonRate"
  :dim "ga:experimentVariant"
  :per "last_1_month"}
```

