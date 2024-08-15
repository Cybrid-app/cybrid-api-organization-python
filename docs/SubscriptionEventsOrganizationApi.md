# cybrid_api_organization.SubscriptionEventsOrganizationApi

All URIs are relative to *https://organization.sandbox.cybrid.app*

Method | HTTP request | Description
------------- | ------------- | -------------
[**get_subscription_event**](SubscriptionEventsOrganizationApi.md#get_subscription_event) | **GET** /api/subscription_events/{subscription_event_guid} | Get Subscription Event 
[**list_subscription_events**](SubscriptionEventsOrganizationApi.md#list_subscription_events) | **GET** /api/subscription_events | Get subscription events list


# **get_subscription_event**
> SubscriptionEvent get_subscription_event(subscription_event_guid)

Get Subscription Event 

Retrieves a Subscription Event.  Required scope: **subscription_events:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscription_events_organization_api
from cybrid_api_organization.model.subscription_event import SubscriptionEvent
from cybrid_api_organization.model.error_response import ErrorResponse
from pprint import pprint
# Defining the host is optional and defaults to https://organization.sandbox.cybrid.app
# See configuration.py for a list of all supported configuration parameters.
configuration = cybrid_api_organization.Configuration(
    host = "https://organization.sandbox.cybrid.app"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure Bearer authorization (JWT): BearerAuth
configuration = cybrid_api_organization.Configuration(
    access_token = 'YOUR_BEARER_TOKEN'
)

# Configure OAuth2 access token for authorization: oauth2
configuration = cybrid_api_organization.Configuration(
    host = "https://organization.sandbox.cybrid.app"
)
configuration.access_token = 'YOUR_ACCESS_TOKEN'

# Enter a context with an instance of the API client
with cybrid_api_organization.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = subscription_events_organization_api.SubscriptionEventsOrganizationApi(api_client)
    subscription_event_guid = "subscription_event_guid_example" # str | Identifier for the Subscription Event.

    # example passing only required values which don't have defaults set
    try:
        # Get Subscription Event 
        api_response = api_instance.get_subscription_event(subscription_event_guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionEventsOrganizationApi->get_subscription_event: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_event_guid** | **str**| Identifier for the Subscription Event. |

### Return type

[**SubscriptionEvent**](SubscriptionEvent.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Subscription Event found |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |
**404** | Subscription Event not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_subscription_events**
> SubscriptionEventList list_subscription_events()

Get subscription events list

Retrieves a listing of subscription events s.  Required scope: **subscription_events:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscription_events_organization_api
from cybrid_api_organization.model.subscription_event_list import SubscriptionEventList
from cybrid_api_organization.model.error_response import ErrorResponse
from pprint import pprint
# Defining the host is optional and defaults to https://organization.sandbox.cybrid.app
# See configuration.py for a list of all supported configuration parameters.
configuration = cybrid_api_organization.Configuration(
    host = "https://organization.sandbox.cybrid.app"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure Bearer authorization (JWT): BearerAuth
configuration = cybrid_api_organization.Configuration(
    access_token = 'YOUR_BEARER_TOKEN'
)

# Configure OAuth2 access token for authorization: oauth2
configuration = cybrid_api_organization.Configuration(
    host = "https://organization.sandbox.cybrid.app"
)
configuration.access_token = 'YOUR_ACCESS_TOKEN'

# Enter a context with an instance of the API client
with cybrid_api_organization.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = subscription_events_organization_api.SubscriptionEventsOrganizationApi(api_client)
    page = ListRequestPage(0) # int | The page index to retrieve. (optional)
    per_page = ListRequestPerPage(1) # int | The number of entities per page to return. (optional)
    guid = "guid_example" # str | Comma separated subscription_event_guids to list subscription events for. (optional)

    # example passing only required values which don't have defaults set
    # and optional values
    try:
        # Get subscription events list
        api_response = api_instance.list_subscription_events(page=page, per_page=per_page, guid=guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionEventsOrganizationApi->list_subscription_events: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| The page index to retrieve. | [optional]
 **per_page** | **int**| The number of entities per page to return. | [optional]
 **guid** | **str**| Comma separated subscription_event_guids to list subscription events for. | [optional]

### Return type

[**SubscriptionEventList**](SubscriptionEventList.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Get list of subscription events |  -  |
**400** | Invalid requests |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

