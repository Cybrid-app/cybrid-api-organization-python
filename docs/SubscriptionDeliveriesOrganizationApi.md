# cybrid_api_organization.SubscriptionDeliveriesOrganizationApi

All URIs are relative to *https://organization.sandbox.cybrid.app*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_subscription_delivery**](SubscriptionDeliveriesOrganizationApi.md#create_subscription_delivery) | **POST** /api/subscription_deliveries/ | Create SubscriptionDelivery
[**get_subscription_delivery**](SubscriptionDeliveriesOrganizationApi.md#get_subscription_delivery) | **GET** /api/subscription_deliveries/{subscription_delivery_guid} | Get Subscription Delivery 
[**list_subscription_deliveries**](SubscriptionDeliveriesOrganizationApi.md#list_subscription_deliveries) | **GET** /api/subscription_deliveries | Get subscription deliveries list


# **create_subscription_delivery**
> SubscriptionDelivery create_subscription_delivery(post_subscription_delivery)

Create SubscriptionDelivery

Creates a SubscriptionDelivery.  post  Required scope: **subscription_events:execute

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscription_deliveries_organization_api
from cybrid_api_organization.model.post_subscription_delivery import PostSubscriptionDelivery
from cybrid_api_organization.model.subscription_delivery import SubscriptionDelivery
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
    api_instance = subscription_deliveries_organization_api.SubscriptionDeliveriesOrganizationApi(api_client)
    post_subscription_delivery = PostSubscriptionDelivery(
        subscription_event_guid="subscription_event_guid_example",
        subscription_guid="subscription_guid_example",
    ) # PostSubscriptionDelivery | 

    # example passing only required values which don't have defaults set
    try:
        # Create SubscriptionDelivery
        api_response = api_instance.create_subscription_delivery(post_subscription_delivery)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionDeliveriesOrganizationApi->create_subscription_delivery: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **post_subscription_delivery** | [**PostSubscriptionDelivery**](PostSubscriptionDelivery.md)|  |

### Return type

[**SubscriptionDelivery**](SubscriptionDelivery.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | SubscriptionDelivery created |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_subscription_delivery**
> SubscriptionDelivery get_subscription_delivery(subscription_delivery_guid)

Get Subscription Delivery 

Retrieves a subscription delivery.  Required scope: **subscription_events:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscription_deliveries_organization_api
from cybrid_api_organization.model.subscription_delivery import SubscriptionDelivery
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
    api_instance = subscription_deliveries_organization_api.SubscriptionDeliveriesOrganizationApi(api_client)
    subscription_delivery_guid = "subscription_delivery_guid_example" # str | Identifier for the subscription delivery.

    # example passing only required values which don't have defaults set
    try:
        # Get Subscription Delivery 
        api_response = api_instance.get_subscription_delivery(subscription_delivery_guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionDeliveriesOrganizationApi->get_subscription_delivery: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_delivery_guid** | **str**| Identifier for the subscription delivery. |

### Return type

[**SubscriptionDelivery**](SubscriptionDelivery.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Subscription delivery found |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |
**404** | Subscription delivery not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_subscription_deliveries**
> SubscriptionDeliveryList list_subscription_deliveries()

Get subscription deliveries list

Retrieves a listing of subscription deliveries s.  Required scope: **subscription_events:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscription_deliveries_organization_api
from cybrid_api_organization.model.subscription_delivery_list import SubscriptionDeliveryList
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
    api_instance = subscription_deliveries_organization_api.SubscriptionDeliveriesOrganizationApi(api_client)
    page = ListRequestPage(0) # int | The page index to retrieve. (optional)
    per_page = ListRequestPerPage(1) # int | The number of entities per page to return. (optional)
    guid = "guid_example" # str | Comma separated subscription_delivery_guids to list subscription deliveries for. (optional)
    subscription_event_guid = "subscription_event_guid_example" # str | Comma separated subscription_event_guids to list subscription deliveries for. (optional)
    subscription_guid = "subscription_guid_example" # str | Comma separated subscription_guids to list subscription deliveries for. (optional)

    # example passing only required values which don't have defaults set
    # and optional values
    try:
        # Get subscription deliveries list
        api_response = api_instance.list_subscription_deliveries(page=page, per_page=per_page, guid=guid, subscription_event_guid=subscription_event_guid, subscription_guid=subscription_guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionDeliveriesOrganizationApi->list_subscription_deliveries: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| The page index to retrieve. | [optional]
 **per_page** | **int**| The number of entities per page to return. | [optional]
 **guid** | **str**| Comma separated subscription_delivery_guids to list subscription deliveries for. | [optional]
 **subscription_event_guid** | **str**| Comma separated subscription_event_guids to list subscription deliveries for. | [optional]
 **subscription_guid** | **str**| Comma separated subscription_guids to list subscription deliveries for. | [optional]

### Return type

[**SubscriptionDeliveryList**](SubscriptionDeliveryList.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Get list of subscription deliveries |  -  |
**400** | Invalid requests |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

