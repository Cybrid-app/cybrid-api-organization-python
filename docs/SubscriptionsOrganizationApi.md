# cybrid_api_organization.SubscriptionsOrganizationApi

All URIs are relative to *https://organization.sandbox.cybrid.app*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_subscription**](SubscriptionsOrganizationApi.md#create_subscription) | **POST** /api/subscriptions/ | Create Subscription
[**delete_subscription**](SubscriptionsOrganizationApi.md#delete_subscription) | **DELETE** /api/subscriptions/{subscription_guid} | Delete Subscription
[**get_subscription**](SubscriptionsOrganizationApi.md#get_subscription) | **GET** /api/subscriptions/{subscription_guid} | Get Subscription 
[**list_subscriptions**](SubscriptionsOrganizationApi.md#list_subscriptions) | **GET** /api/subscriptions | Get subscriptions list


# **create_subscription**
> Subscription create_subscription(post_subscription)

Create Subscription

Creates a Subscription.  ## Subscription creation  Subscriptions can be created for webhook endpoints.  ## State  | State | Description | |-------|-------------| | storing | The Platform is storing the subscription details in our private store | | completed | The Platform has created the subscription | | failed | The Platform was not able to successfully create the subscription |    Required scope: **subscriptions:execute

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscriptions_organization_api
from cybrid_api_organization.model.subscription import Subscription
from cybrid_api_organization.model.post_subscription import PostSubscription
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
    api_instance = subscriptions_organization_api.SubscriptionsOrganizationApi(api_client)
    post_subscription = PostSubscription(
        name="name_example",
        type="webhook",
        url="url_example",
        environment="environment_example",
    ) # PostSubscription | 

    # example passing only required values which don't have defaults set
    try:
        # Create Subscription
        api_response = api_instance.create_subscription(post_subscription)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionsOrganizationApi->create_subscription: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **post_subscription** | [**PostSubscription**](PostSubscription.md)|  |

### Return type

[**Subscription**](Subscription.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Subscription created |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete_subscription**
> delete_subscription(subscription_guid)

Delete Subscription

Deletes a subscription.  Required scope: **subscriptions:execute**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscriptions_organization_api
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
    api_instance = subscriptions_organization_api.SubscriptionsOrganizationApi(api_client)
    subscription_guid = "subscription_guid_example" # str | Identifier for the subscription.

    # example passing only required values which don't have defaults set
    try:
        # Delete Subscription
        api_instance.delete_subscription(subscription_guid)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionsOrganizationApi->delete_subscription: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_guid** | **str**| Identifier for the subscription. |

### Return type

void (empty response body)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**204** | Subscription deleted |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |
**404** | Subscription not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_subscription**
> Subscription get_subscription(subscription_guid)

Get Subscription 

Retrieves a subscription.  Required scope: **subscriptions:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscriptions_organization_api
from cybrid_api_organization.model.subscription import Subscription
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
    api_instance = subscriptions_organization_api.SubscriptionsOrganizationApi(api_client)
    subscription_guid = "subscription_guid_example" # str | Identifier for the subscription.
    include_signing_key = True # bool | Flag to include signing key in the response. (optional)

    # example passing only required values which don't have defaults set
    try:
        # Get Subscription 
        api_response = api_instance.get_subscription(subscription_guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionsOrganizationApi->get_subscription: %s\n" % e)

    # example passing only required values which don't have defaults set
    # and optional values
    try:
        # Get Subscription 
        api_response = api_instance.get_subscription(subscription_guid, include_signing_key=include_signing_key)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionsOrganizationApi->get_subscription: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **subscription_guid** | **str**| Identifier for the subscription. |
 **include_signing_key** | **bool**| Flag to include signing key in the response. | [optional]

### Return type

[**Subscription**](Subscription.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Subscription found |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |
**404** | Subscription not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_subscriptions**
> SubscriptionList list_subscriptions()

Get subscriptions list

Retrieves a listing of subscriptions.  Required scope: **subscriptions:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import subscriptions_organization_api
from cybrid_api_organization.model.subscription_list import SubscriptionList
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
    api_instance = subscriptions_organization_api.SubscriptionsOrganizationApi(api_client)
    page = ListRequestPage(0) # int | The page index to retrieve. (optional)
    per_page = ListRequestPerPage(1) # int | The number of entities per page to return. (optional)
    guid = "guid_example" # str | Comma separated subscription_guids to list subscriptions for. (optional)
    include_signing_key = True # bool | Flag to include signing key in the response. (optional)

    # example passing only required values which don't have defaults set
    # and optional values
    try:
        # Get subscriptions list
        api_response = api_instance.list_subscriptions(page=page, per_page=per_page, guid=guid, include_signing_key=include_signing_key)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling SubscriptionsOrganizationApi->list_subscriptions: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| The page index to retrieve. | [optional]
 **per_page** | **int**| The number of entities per page to return. | [optional]
 **guid** | **str**| Comma separated subscription_guids to list subscriptions for. | [optional]
 **include_signing_key** | **bool**| Flag to include signing key in the response. | [optional]

### Return type

[**SubscriptionList**](SubscriptionList.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Get list of subscriptions |  -  |
**400** | Invalid requests |  -  |
**401** | Unauthorized - Authentication failed,  |  -  |
**403** | Invalid scope |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

