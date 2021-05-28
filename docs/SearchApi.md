# SearchApi

All URIs are relative to *https://api.clarivate.com/api/woslite*

Method | HTTP request | Description
------------- | ------------- | -------------
[**QueryQueryIdGet**](SearchApi.md#QueryQueryIdGet) | **GET** /query/{queryId} | Fetch record(s) by query identifier
[**RootGet**](SearchApi.md#RootGet) | **GET** / | Submits a user query and returns results


# **QueryQueryIdGet**
> WosLiteResponse QueryQueryIdGet(query.id, count, first.record, sort.field=var.sort.field)

Fetch record(s) by query identifier

This operation returns record(s) identified by a query identifier.

### Example
```R
library(woslite_r_client)

var.query.id <- 56 # integer | Retrieve records based on query identifier.
var.count <- 56 # integer | Number of records to return, must be 0-100.
var.first.record <- 56 # integer | Specific record, if any within the result set to return. Cannot be less than 1 and greater than 100000.
var.sort.field <- 'sort.field_example' # character | Order by field(s). Field name and order by clause separated by '+', use A for ASC and D for DESC, ex: PY+D. Multiple values are separated by comma. If sortField was set on the original query, this parameter should be set as sorting is not a property of the query.

#Fetch record(s) by query identifier
api.instance <- SearchApi$new()
# Configure API key authorization: key
api.instance$apiClient$apiKeys['X-ApiKey'] <- 'TODO_YOUR_API_KEY';
result <- api.instance$QueryQueryIdGet(var.query.id, var.count, var.first.record, sort.field=var.sort.field)
dput(result)
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **query.id** | **integer**| Retrieve records based on query identifier. | 
 **count** | **integer**| Number of records to return, must be 0-100. | 
 **first.record** | **integer**| Specific record, if any within the result set to return. Cannot be less than 1 and greater than 100000. | 
 **sort.field** | **character**| Order by field(s). Field name and order by clause separated by &#39;+&#39;, use A for ASC and D for DESC, ex: PY+D. Multiple values are separated by comma. If sortField was set on the original query, this parameter should be set as sorting is not a property of the query. | [optional] 

### Return type

[**WosLiteResponse**](WosLiteResponse.md)

### Authorization

[key](../README.md#key)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/xml

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success |  * X-RateLimit-Remaining-second - The number of requests left for the second window. <br>  * X-RateLimit-Limit-second - The number of requests limit per second. <br>  * x-paginate-by-query-id - The url of the next page in case your &#x60;RecordsFound &gt; count + firstRecord&#x60; Please use this url for pagination. The QueryId will live for four hours in case if inactivity.  <br>  |
| **0** | Error response 400+ |  * X-RateLimit-Remaining-second - The number of requests left for the second window. <br>  * X-RateLimit-Limit-second - The number of requests limit per second. <br>  |

# **RootGet**
> WosLiteResponse RootGet(database.id, usr.query, count, first.record, lang=var.lang, edition=var.edition, publish.time.span=var.publish.time.span, load.time.span=var.load.time.span, sort.field=var.sort.field)

Submits a user query and returns results

The search operation submits a search query to the specified database edition and retrieves data. This operation returns a query ID that can be used in subsequent operations to retrieve more records.

### Example
```R
library(woslite_r_client)

var.database.id <- 'database.id_example' # character | Database to search. Must be a valid database ID, one of the following: BCI/BIOABS/BIOSIS/CCC/DCI/DIIDW/MEDLINE/WOK/WOS/ZOOREC. WOK represents all databases.
var.usr.query <- 'usr.query_example' # character | User query for requesting data, ex: TS=(cadmium). The query parser will return errors for invalid queries.
var.count <- 56 # integer | Number of records to return, must be 0-100.
var.first.record <- 56 # integer | Specific record, if any within the result set to return. Cannot be less than 1 and greater than 100000.
var.lang <- 'lang_example' # character | Language of search. This element can take only one value: en for English. If no language is specified, English is passed by default.
var.edition <- 'edition_example' # character | Edition(s) to be searched. If null, user permissions will be substituted. Must include the name of the collection and edition name separated by '+', ex: WOS+SCI. Multiple editions are separated by ','. Editions available for collection(WOS) - AHCI,CCR,IC,ISSHP,ISTP,SCI,SSCI,BHCI,BSCI and ESCI.
var.publish.time.span <- 'publish.time.span_example' # character | This element specifies a range of publication dates. If publishTimeSpan is used, the loadTimeSpan parameter must be omitted. If publishTimeSpan and loadTimeSpan are both omitted, then the maximum time span will be inferred from the editions data. Beginning and end dates should be specified in the yyyy-mm-dd format separated by +, ex: 1993-01-01+2009-12-31.
var.load.time.span <- 'load.time.span_example' # character | Load time span (otherwise described as symbolic time span) defines a range of load dates. The load date is the date a record was added to the database. If load date is specified, the publishTimeSpan parameter must be omitted. If both publishTimeSpan and loadTimeSpan are omitted, the maximum publication date will be inferred from the editions data. Any of D/W/M/Y prefixed with a number where D-Day, M-Month, W-Week, Y-Year allowed. Acceptable value range for Day(0-6), Week(1-52), Month(1-12) and Year(0-10), ex: 5D,30W,10M,8Y.
var.sort.field <- 'sort.field_example' # character | Order by field(s). Field name and order by clause separated by '+', use A for ASC and D for DESC, ex: PY+D. Multiple values are separated by comma.

#Submits a user query and returns results
api.instance <- SearchApi$new()
# Configure API key authorization: key
api.instance$apiClient$apiKeys['X-ApiKey'] <- 'TODO_YOUR_API_KEY';
result <- api.instance$RootGet(var.database.id, var.usr.query, var.count, var.first.record, lang=var.lang, edition=var.edition, publish.time.span=var.publish.time.span, load.time.span=var.load.time.span, sort.field=var.sort.field)
dput(result)
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **database.id** | **character**| Database to search. Must be a valid database ID, one of the following: BCI/BIOABS/BIOSIS/CCC/DCI/DIIDW/MEDLINE/WOK/WOS/ZOOREC. WOK represents all databases. | 
 **usr.query** | **character**| User query for requesting data, ex: TS&#x3D;(cadmium). The query parser will return errors for invalid queries. | 
 **count** | **integer**| Number of records to return, must be 0-100. | 
 **first.record** | **integer**| Specific record, if any within the result set to return. Cannot be less than 1 and greater than 100000. | 
 **lang** | **character**| Language of search. This element can take only one value: en for English. If no language is specified, English is passed by default. | [optional] 
 **edition** | **character**| Edition(s) to be searched. If null, user permissions will be substituted. Must include the name of the collection and edition name separated by &#39;+&#39;, ex: WOS+SCI. Multiple editions are separated by &#39;,&#39;. Editions available for collection(WOS) - AHCI,CCR,IC,ISSHP,ISTP,SCI,SSCI,BHCI,BSCI and ESCI. | [optional] 
 **publish.time.span** | **character**| This element specifies a range of publication dates. If publishTimeSpan is used, the loadTimeSpan parameter must be omitted. If publishTimeSpan and loadTimeSpan are both omitted, then the maximum time span will be inferred from the editions data. Beginning and end dates should be specified in the yyyy-mm-dd format separated by +, ex: 1993-01-01+2009-12-31. | [optional] 
 **load.time.span** | **character**| Load time span (otherwise described as symbolic time span) defines a range of load dates. The load date is the date a record was added to the database. If load date is specified, the publishTimeSpan parameter must be omitted. If both publishTimeSpan and loadTimeSpan are omitted, the maximum publication date will be inferred from the editions data. Any of D/W/M/Y prefixed with a number where D-Day, M-Month, W-Week, Y-Year allowed. Acceptable value range for Day(0-6), Week(1-52), Month(1-12) and Year(0-10), ex: 5D,30W,10M,8Y. | [optional] 
 **sort.field** | **character**| Order by field(s). Field name and order by clause separated by &#39;+&#39;, use A for ASC and D for DESC, ex: PY+D. Multiple values are separated by comma. | [optional] 

### Return type

[**WosLiteResponse**](WosLiteResponse.md)

### Authorization

[key](../README.md#key)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/xml

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success |  * X-RateLimit-Remaining-second - The number of requests left for the second window. <br>  * X-RateLimit-Limit-second - The number of requests limit per second. <br>  * x-paginate-by-query-id - The url of the next page in case your &#x60;RecordsFound &gt; count + firstRecord&#x60; Please use this url for pagination. The QueryId will live for four hours in case if inactivity.  <br>  |
| **0** | Error response 400+ |  * X-RateLimit-Remaining-second - The number of requests left for the second window. <br>  * X-RateLimit-Limit-second - The number of requests limit per second. <br>  |

