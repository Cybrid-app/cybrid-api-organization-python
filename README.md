# cybrid-api-organization-python
# Cybrid API documentation

Welcome to Cybrid, an all-in-one crypto platform that enables you to easily **build** and **launch** white-label crypto products or services.

In these documents, you'll find details on how our REST API operates and generally how our platform functions.

If you're looking for our UI SDK Widgets for Web or Mobile (iOS/Android), generated API clients, or demo applications, head over to our [Github repo](https://github.com/Cybrid-app).

💡 We recommend bookmarking the [Cybrid LinkTree](https://linktr.ee/cybridtechnologies) which contains many helpful links to platform resources.

## Getting Started

This is Cybrid's public interactive API documentation, which allows you to fully test our APIs. If you'd like to use a different tool to exercise our APIs, you can download the [Open API 3.0 yaml](https://bank.production.cybrid.app/api/schema/v1/swagger.yaml) for import.

If you're new to our APIs and the Cybrid Platform, follow the below guides to get set up and familiar with the platform:

1. [Introduction](https://docs.cybrid.xyz/docs/introduction)
2. [Platform Introduction](https://docs.cybrid.xyz/docs/how-is-cybrid-architected)
3. [Testing with Hosted Web Demo App](https://docs.cybrid.xyz/docs/testing-with-hosted-web-demo-app)

In [Getting Started in the Cybrid Sandbox](https://docs.cybrid.xyz/docs/how-do-i-get-started-with-the-sandbox), we walk you through how to use the [Cybrid Sandbox](https://id.sandbox.cybrid.app/) to create a test bank and generate API keys. In [Getting Ready for Trading](https://kb.cybrid.xyz/getting-ready-for-trading), we walk through creating customers, customer identities, accounts, as well as executing quotes and trades.

## Working with the Cybrid Platform

There are three primary ways you can interact with the Cybrid platform:

1. Directly via our RESTful API (this documentation)
2. Using our API clients available in a variety of languages ([Angular](https://github.com/Cybrid-app/cybrid-api-bank-angular), [Java](https://github.com/Cybrid-app/cybrid-api-bank-java), [Kotlin](https://github.com/Cybrid-app/cybrid-api-bank-kotlin), [Python](https://github.com/Cybrid-app/cybrid-api-bank-python), [Ruby](https://github.com/Cybrid-app/cybrid-api-bank-ruby), [Swift](https://github.com/Cybrid-app/cybrid-api-bank-swift) or [Typescript](https://github.com/Cybrid-app/cybrid-api-bank-typescript))
3. Integrating a platform specific SDK ([Web](https://github.com/Cybrid-app/cybrid-sdk-web), [Android](https://github.com/Cybrid-app/cybrid-sdk-android), [iOS](https://github.com/Cybrid-app/cybrid-sdk-ios))

Our complete set of APIs allows you to manage resources across three distinct areas: your `Organization`, your `Banks` and your `Identities`. For most of your testing and interaction you'll be using the `Bank` API, which is where the majority of APIs reside.

*The complete set of APIs can be found on the following pages:*

| API                                                              | Description                                                 |
|------------------------------------------------------------------|-------------------------------------------------------------|
| [Organization API](https://organization.production.cybrid.app/api/schema/swagger-ui)   | APIs to manage organizations                                |
| [Bank API](https://bank.production.cybrid.app/api/schema/swagger-ui)                   | APIs to manage banks (and all downstream customer activity) |
| [Identities API](https://id.production.cybrid.app/api/schema/swagger-ui)                       | APIs to manage organization and bank identities             |

For questions please contact [Support](mailto:support@cybrid.xyz) at any time for assistance, or contact the [Product Team](mailto:product@cybrid.xyz) for product suggestions.

## Authenticating with the API

The Cybrid Platform uses OAuth 2.0 Bearer Tokens to authenticate requests to the platform. Credentials to create `Organization` and `Bank` tokens can be generated via the [Cybrid Sandbox](https://id.production.cybrid.app). Access tokens can be generated for a `Customer` as well via the [Cybrid IdP](https://id.production.cybrid.app) as well.

An `Organization` access token applies broadly to the whole Organization and all of its `Banks`, whereas, a `Bank` access token is specific to an individual Bank. `Customer` tokens, similarly, are scoped to a specific customer in a bank.

Both `Organization` and `Bank` tokens can be created using the OAuth Client Credential Grant flow. Each Organization and Bank has its own unique `Client ID` and `Secret` that allows for machine-to-machine authentication.

A `Bank` can then generate `Customer` access tokens via API using our [Identities API](https://id.production.cybrid.app/api/schema/swagger-ui).

<font color=\"orange\">**⚠️ Never share your Client ID or Secret publicly or in your source code repository.**</font>

Your `Client ID` and `Secret` can be exchanged for a time-limited `Bearer Token` by interacting with the Cybrid Identity Provider or through interacting with the **Authorize** button in this document.

The following curl command can be used to quickly generate a `Bearer Token` for use in testing the API or demo applications.

```
# Example request when using Bank credentials
curl -X POST https://id.production.cybrid.app/oauth/token -d '{
    \"grant_type\": \"client_credentials\",
    \"client_id\": \"<Your Client ID>\",
    \"client_secret\": \"<Your Secret>\",
    \"scope\": \"banks:read banks:write bank_applications:execute accounts:read accounts:execute counterparties:read counterparties:pii:read counterparties:write counterparties:execute customers:read customers:pii:read customers:write customers:execute prices:read quotes:execute quotes:read trades:execute trades:read transfers:execute transfers:read transfers:write external_bank_accounts:read external_bank_accounts:pii:read external_bank_accounts:write external_bank_accounts:execute external_wallets:read external_wallets:execute workflows:read workflows:execute deposit_addresses:read deposit_addresses:execute deposit_bank_accounts:read deposit_bank_accounts:execute invoices:read invoices:write invoices:execute identity_verifications:read identity_verifications:pii:read identity_verifications:write identity_verifications:execute persona_sessions:execute files:read files:pii:read files:execute\"
  }' -H \"Content-Type: application/json\"

# When using Organization credentials set `scope` to 'organizations:read organizations:write organization_applications:execute banks:read banks:write banks:execute bank_applications:execute users:read users:write users:execute counterparties:read counterparties:pii:read customers:read customers:pii:read accounts:read prices:read quotes:execute quotes:read trades:execute trades:read transfers:read transfers:write transfers:execute external_bank_accounts:read external_bank_accounts:pii:read external_wallets:read workflows:read deposit_addresses:read deposit_bank_accounts:read invoices:read subscriptions:read subscriptions:write subscriptions:execute subscription_events:read subscription_events:execute identity_verifications:read identity_verifications:pii:read identity_verifications:execute persona_sessions:execute files:read files:pii:read files:execute'
```
<font color=\"orange\">**⚠️ Note: The above curl will create a bearer token with full scope access. Delete scopes if you'd like to restrict access.**</font>

## Authentication Scopes

The Cybrid platform supports the use of scopes to control the level of access a token is limited to. Scopes do not grant access to resources; instead, they provide limits, in support of the least privilege principal.

The following scopes are available on the platform and can be requested when generating either an Organization, Bank or Customer token. Generally speaking, the _Read_ scope is required to read and list resources, the _Write_ scope is required to update a resource and the _Execute_ scope is required to create a resource.

| Resource              | Read scope (Token Type)                                    | Write scope (Token Type)                      | Execute scope (Token Type)                       |
|-----------------------|------------------------------------------------------------|-----------------------------------------------|--------------------------------------------------|
| Account               | accounts:read (Organization, Bank, Customer)               |                                               | accounts:execute (Bank, Customer)                |
| Bank                  | banks:read (Organization, Bank)                            | banks:write (Organization, Bank)              | banks:execute (Organization)                     |
| Customer              | customers:read (Organization, Bank, Customer)              | customers:write (Bank, Customer)              | customers:execute (Bank)                         |
| Counterparty          | counterparties:read (Organization, Bank, Customer)         | counterparties:write (Bank, Customer)         | counterparties:execute (Bank)                    |
| Deposit Address       | deposit_addresses:read (Organization, Bank, Customer)      | deposit_addresses:write (Bank, Customer)      | deposit_addresses:execute (Bank, Customer)       |
| External Bank Account | external_bank_accounts:read (Organization, Bank, Customer) | external_bank_accounts:write (Bank, Customer) | external_bank_accounts:execute (Bank, Customer)  |
| External Wallet       | external_wallet:read (Organization, Bank, Customer)        |                                               | external_wallet:execute (Bank, Customer)         |
| Organization          | organizations:read (Organization)                          | organizations:write (Organization)            |                                                  |
| User                  | users:read (Organization)                                  |                                               | users:execute (Organization)                     |
| Price                 | prices:read (Bank, Customer)                               |                                               |                                                  |
| Quote                 | quotes:read (Organization, Bank, Customer)                 |                                               | quotes:execute (Organization, Bank, Customer)    |
| Trade                 | trades:read (Organization, Bank, Customer)                 |                                               | trades:execute (Organization, Bank, Customer)    |
| Transfer              | transfers:read (Organization, Bank, Customer)              |                                               | transfers:execute (Organization, Bank, Customer) |
| Workflow              | workflows:read (Organization, Bank, Customer)              |                                               | workflows:execute (Bank, Customer)               |
| Invoice               | invoices:read (Organization, Bank, Customer)               | invoices:write (Bank, Customer)               | invoices:execute (Bank, Customer)                |

## Available Endpoints

The available APIs for the [Identity](https://id.production.cybrid.app/api/schema/swagger-ui), [Organization](https://organization.production.cybrid.app/api/schema/swagger-ui) and [Bank](https://bank.production.cybrid.app/api/schema/swagger-ui) API services are listed below:

| API Service  | Model                | API Endpoint Path              | Description                                                                                       |
|--------------|----------------------|--------------------------------|---------------------------------------------------------------------------------------------------|
| Identity     | Bank                 | /api/bank_applications         | Create and list banks                                                                             |
| Identity     | CustomerToken        | /api/customer_tokens           | Create customer JWT access tokens                                                                 |
| Identity     | Organization         | /api/organization_applications | Create and list organizations                                                                     |
| Identity     | Organization         | /api/users                     | Create and list organization users                                                                |
| Organization | Organization         | /api/organizations             | APIs to retrieve and update organization name                                                     |
| Bank         | Account              | /api/accounts                  | Create and list accounts, which hold a specific asset for a customers                             |
| Bank         | Asset                | /api/assets                    | Get a list of assets supported by the platform (ex: BTC, ETH)                                     |
| Bank         | Bank                 | /api/banks                     | Create, update and list banks, the parent to customers, accounts, etc                             |
| Bank         | Customer             | /api/customers                 | Create and list customers                                                                         |
| Bank         | Counterparty         | /api/counterparties            | Create and list counterparties                                                                    |
| Bank         | DepositAddress       | /api/deposit_addresses         | Create, get and list deposit addresses                                                            |
| Bank         | ExternalBankAccount  | /api/external_bank_accounts    | Create, get and list external bank accounts, which connect customer bank accounts to the platform |
| Bank         | ExternalWallet       | /api/external_wallets          | Create, get, list and delete external wallets, which connect customer wallets to the platform     |
| Bank         | IdentityVerification | /api/identity_verifications    | Create and list identity verifications, which are performed on customers for KYC                  |
| Bank         | Invoice              | /api/invoices                  | Create, get, cancel and list invoices                                                             |
| Bank         | PaymentInstruction   | /api/payment_instructions      | Create, get and list payment instructions for invoices                                            |
| Bank         | Price                | /api/prices                    | Get the current prices for assets on the platform                                                 |
| Bank         | Quote                | /api/quotes                    | Create and list quotes, which are required to execute trades                                      |
| Bank         | Symbol               | /api/symbols                   | Get a list of symbols supported for trade (ex: BTC-USD)                                           |
| Bank         | Trade                | /api/trades                    | Create and list trades, which buy or sell cryptocurrency                                          |
| Bank         | Transfer             | /api/transfers                 | Create, get and list transfers (e.g., funding, book)                                              |
| Bank         | Workflow             | /api/workflows                 | Create, get and list workflows                                                                    |

## Understanding Object Models & Endpoints

**Organizations**

An `Organization` is meant to represent the organization partnering with Cybrid to use our platform.

An `Organization` typically does not directly interact with `customers`. Instead, an Organization has one or more `banks`, which encompass the financial service offerings of the platform.

**Banks**

A `Bank` is owned by an `Organization` and can be thought of as an environment or container for `customers` and product offerings. Banks are created in either `Sandbox` or `Production` mode, where `Sandbox` is the environment that you would test, prototype and build in prior to moving to `Production`.

An `Organization` can have multiple `banks`, in either `Sandbox` or `Production` environments. A `Sandbox Bank` will be backed by stubbed data and process flows. For instance, funding source transfer processes as well as trades will be simulated rather than performed, however asset prices are representative of real-world values. You have an unlimited amount of simulated fiat currency for testing purposes.

**Customers**

`Customers` represent your banking users on the platform. At present, we offer support for `Individuals` as Customers.

`Customers` must be verified (i.e., KYC'd) in our system before they can play any part on the platform, which means they must have an associated and a passing `Identity Verification`. See the Identity Verifications section for more details on how a customer can be verified.

`Customers` must also have an `Account` to be able to transact, in the desired asset class. See the Accounts APIs for more details on setting up accounts for the customer.


This Python package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: v0.124.42
- Package version: 1.0.0
- Build package: org.openapitools.codegen.languages.PythonClientCodegen

## Requirements.

Python >=3.6

## Installation & Usage
### pip install

If the python package is hosted on a repository, you can install directly using:

```sh
pip install git+https://github.com/GIT_USER_ID/GIT_REPO_ID.git
```
(you may need to run `pip` with root permission: `sudo pip install git+https://github.com/GIT_USER_ID/GIT_REPO_ID.git`)

Then import the package:
```python
import cybrid_api_organization
```

### Setuptools

Install via [Setuptools](http://pypi.python.org/pypi/setuptools).

```sh
python setup.py install --user
```
(or `sudo python setup.py install` to install the package for all users)

Then import the package:
```python
import cybrid_api_organization
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```python

import time
import cybrid_api_organization
from pprint import pprint
from cybrid_api_organization.api import organizations_organization_api
from cybrid_api_organization.model.error_response import ErrorResponse
from cybrid_api_organization.model.organization import Organization
from cybrid_api_organization.model.patch_organization import PatchOrganization
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

    try:
        # Get organization
        api_response = api_instance.get_organization(organization_guid)
        pprint(api_response)
    except cybrid_api_organization.ApiException as e:
        print("Exception when calling OrganizationsOrganizationApi->get_organization: %s\n" % e)
```

## Documentation for API Endpoints

All URIs are relative to *https://organization.sandbox.cybrid.app*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*OrganizationsOrganizationApi* | [**get_organization**](docs/OrganizationsOrganizationApi.md#get_organization) | **GET** /api/organizations/{organization_guid} | Get organization
*OrganizationsOrganizationApi* | [**update_organization**](docs/OrganizationsOrganizationApi.md#update_organization) | **PATCH** /api/organizations/{organization_guid} | Patch organization
*SubscriptionDeliveriesOrganizationApi* | [**create_subscription_delivery**](docs/SubscriptionDeliveriesOrganizationApi.md#create_subscription_delivery) | **POST** /api/subscription_deliveries/ | Create SubscriptionDelivery
*SubscriptionDeliveriesOrganizationApi* | [**get_subscription_delivery**](docs/SubscriptionDeliveriesOrganizationApi.md#get_subscription_delivery) | **GET** /api/subscription_deliveries/{subscription_delivery_guid} | Get Subscription Delivery 
*SubscriptionDeliveriesOrganizationApi* | [**list_subscription_deliveries**](docs/SubscriptionDeliveriesOrganizationApi.md#list_subscription_deliveries) | **GET** /api/subscription_deliveries | Get subscription deliveries list
*SubscriptionEventsOrganizationApi* | [**get_subscription_event**](docs/SubscriptionEventsOrganizationApi.md#get_subscription_event) | **GET** /api/subscription_events/{subscription_event_guid} | Get Subscription Event 
*SubscriptionEventsOrganizationApi* | [**list_subscription_events**](docs/SubscriptionEventsOrganizationApi.md#list_subscription_events) | **GET** /api/subscription_events | Get subscription events list
*SubscriptionsOrganizationApi* | [**create_subscription**](docs/SubscriptionsOrganizationApi.md#create_subscription) | **POST** /api/subscriptions/ | Create Subscription
*SubscriptionsOrganizationApi* | [**delete_subscription**](docs/SubscriptionsOrganizationApi.md#delete_subscription) | **DELETE** /api/subscriptions/{subscription_guid} | Delete Subscription
*SubscriptionsOrganizationApi* | [**get_subscription**](docs/SubscriptionsOrganizationApi.md#get_subscription) | **GET** /api/subscriptions/{subscription_guid} | Get Subscription 
*SubscriptionsOrganizationApi* | [**list_subscriptions**](docs/SubscriptionsOrganizationApi.md#list_subscriptions) | **GET** /api/subscriptions | Get subscriptions list


## Documentation For Models

 - [ErrorResponse](docs/ErrorResponse.md)
 - [ListRequestPage](docs/ListRequestPage.md)
 - [ListRequestPerPage](docs/ListRequestPerPage.md)
 - [Organization](docs/Organization.md)
 - [PatchOrganization](docs/PatchOrganization.md)
 - [PostSubscription](docs/PostSubscription.md)
 - [PostSubscriptionDelivery](docs/PostSubscriptionDelivery.md)
 - [Subscription](docs/Subscription.md)
 - [SubscriptionDelivery](docs/SubscriptionDelivery.md)
 - [SubscriptionDeliveryList](docs/SubscriptionDeliveryList.md)
 - [SubscriptionEnvironment](docs/SubscriptionEnvironment.md)
 - [SubscriptionEvent](docs/SubscriptionEvent.md)
 - [SubscriptionEventList](docs/SubscriptionEventList.md)
 - [SubscriptionList](docs/SubscriptionList.md)
 - [SubscriptionState](docs/SubscriptionState.md)
 - [SubscriptionType](docs/SubscriptionType.md)


## Documentation For Authorization


## BearerAuth

- **Type**: Bearer authentication (JWT)


## oauth2

- **Type**: OAuth
- **Flow**: application
- **Authorization URL**: 
- **Scopes**: 
 - **organizations:write**: organizations write
 - **organizations:read**: organizations read
 - **subscriptions:write**: subscriptions write
 - **subscriptions:read**: subscriptions read
 - **subscriptions:execute**: subscriptions execute
 - **subscription_events:read**: subscription_events read
 - **subscription_events:execute**: subscription_events execute


## Author

support@cybrid.app


## Notes for Large OpenAPI documents
If the OpenAPI document is large, imports in cybrid_api_organization.apis and cybrid_api_organization.models may fail with a
RecursionError indicating the maximum recursion limit has been exceeded. In that case, there are a couple of solutions:

Solution 1:
Use specific imports for apis and models like:
- `from cybrid_api_organization.api.default_api import DefaultApi`
- `from cybrid_api_organization.model.pet import Pet`

Solution 2:
Before importing the package, adjust the maximum recursion limit as shown below:
```
import sys
sys.setrecursionlimit(1500)
import cybrid_api_organization
from cybrid_api_organization.apis import *
from cybrid_api_organization.models import *
```

