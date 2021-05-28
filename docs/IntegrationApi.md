# IntegrationApi

All URIs are relative to *https://api.clarivate.com/api/woslite*

Method | HTTP request | Description
------------- | ------------- | -------------
[**IdUniqueIdGet**](IntegrationApi.md#IdUniqueIdGet) | **GET** /id/{uniqueId} | Find record(s) by specific id


# **IdUniqueIdGet**
> WosLiteResponse IdUniqueIdGet(database.id, unique.id, count, first.record, lang=var.lang, sort.field=var.sort.field)

Find record(s) by specific id

This operation returns a record identified by a unique identifier. You may specify multiple identifiers in a single request.

### Example
```R
library(woslite_r_client)

var.database.id <- 'database.id_example' # character | Database to search. Must be a valid database ID, one of the following: BCI/BIOABS/BIOSIS/CCC/DCI/DIIDW/MEDLINE/WOK/WOS/ZOOREC. WOK represents all databases.
var.unique.id <- 'unique.id_example' # character | Primary item(s) id to be searched, ex: WOS:000270372400005. Cannot be null or an empty string. Multiple values are separated by comma.
var.count <- 10 # integer | Number of records returned in the request
var.first.record <- 56 # integer | Specific record, if any within the result set to return. Cannot be less than 1 and greater than 100000.
var.lang <- 'lang_example' # character | Language of search. This element can take only one value: en for English. If no language is specified, English is passed by default.
var.sort.field <- 'sort.field_example' # character | Order by field(s). Field name and order by clause separated by '+', use A for ASC and D for DESC, ex: PY+D. Multiple values are separated by comma.

#Find record(s) by specific id
api.instance <- IntegrationApi$new()
# Configure API key authorization: key
api.instance$apiClient$apiKeys['X-ApiKey'] <- 'TODO_YOUR_API_KEY';
result <- api.instance$IdUniqueIdGet(var.database.id, var.unique.id, var.count, var.first.record, lang=var.lang, sort.field=var.sort.field)
dput(result)
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **database.id** | **character**| Database to search. Must be a valid database ID, one of the following: BCI/BIOABS/BIOSIS/CCC/DCI/DIIDW/MEDLINE/WOK/WOS/ZOOREC. WOK represents all databases. | 
 **unique.id** | **character**| Primary item(s) id to be searched, ex: WOS:000270372400005. Cannot be null or an empty string. Multiple values are separated by comma. | 
 **count** | **integer**| Number of records returned in the request | 
 **first.record** | **integer**| Specific record, if any within the result set to return. Cannot be less than 1 and greater than 100000. | 
 **lang** | **character**| Language of search. This element can take only one value: en for English. If no language is specified, English is passed by default. | [optional] 
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

