# cybrid_api_organization.OrganizationsOrganizationApi

All URIs are relative to *https://organization.sandbox.cybrid.app*

Method | HTTP request | Description
------------- | ------------- | -------------
[**get_organization**](OrganizationsOrganizationApi.md#get_organization) | **GET** /api/organizations/{organization_guid} | Get organization
[**update_organization**](OrganizationsOrganizationApi.md#update_organization) | **PATCH** /api/organizations/{organization_guid} | Patch organization


# **get_organization**
> Organization get_organization(organization_guid)

Get organization

Retrieve an organization.  Required scope: **organizations:read**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import organizations_organization_api
from cybrid_api_organization.model.organization import Organization
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
    api_instance = organizations_organization_api.OrganizationsOrganizationApi(api_client)
    organization_guid = "organization_guid_example" # str | Identifier for the organization.

    # example passing only required values which don't have defaults set
    try:
        # Get organization
        api_response = api_instance.get_organization(organization_guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling OrganizationsOrganizationApi->get_organization: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **organization_guid** | **str**| Identifier for the organization. |

### Return type

[**Organization**](Organization.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | organization found |  -  |
**401** | Unauthorized |  -  |
**403** | Forbidden |  -  |
**404** | Not Found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **update_organization**
> Organization update_organization(organization_guid, patch_organization)

Patch organization

Update an organization.  Required scope: **organizations:write**

### Example

* Bearer (JWT) Authentication (BearerAuth):
* OAuth Authentication (oauth2):

```python
import time
import cybrid_api_organization
from cybrid_api_organization.api import organizations_organization_api
from cybrid_api_organization.model.organization import Organization
from cybrid_api_organization.model.error_response import ErrorResponse
from cybrid_api_organization.model.patch_organization import PatchOrganization
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
    api_instance = organizations_organization_api.OrganizationsOrganizationApi(api_client)
    organization_guid = "organization_guid_example" # str | Identifier for the organization.
    patch_organization = PatchOrganization(
        name="name_example",
    ) # PatchOrganization | 

    # example passing only required values which don't have defaults set
    try:
        # Patch organization
        api_response = api_instance.update_organization(organization_guid, patch_organization)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling OrganizationsOrganizationApi->update_organization: %s\n" % e)
```


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **organization_guid** | **str**| Identifier for the organization. |
 **patch_organization** | [**PatchOrganization**](PatchOrganization.md)|  |

### Return type

[**Organization**](Organization.md)

### Authorization

[BearerAuth](../README.md#BearerAuth), [oauth2](../README.md#oauth2)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | organization found |  -  |
**400** | Bad Request |  -  |
**401** | Unauthorized |  -  |
**403** | Forbidden |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

