# Subscription


## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**guid** | **str** | Auto-generated unique identifier for the subscription. | 
**name** | **str** | Name provided for the subscription. | 
**url** | **str** | The url for the subscription. | 
**environment** | **str** | The environment that the subscription is configured for; one of sandbox or production. | 
**state** | **str** | The state of the subscription; one of storing, completed, or failed. | 
**type** | **str** | The type of subscription. | defaults to "webhook"
**organization_guid** | **str** | The organization guid for the subscription. | [optional] 
**signing_key** | **str** | Subscription private signing key. | [optional] 
**deliveries_failing_since** | **datetime, none_type** | ISO8601 datetime the deliveries started failing. | [optional] 
**failure_code** | **str, none_type** | The failure code of a subscription (if any) | [optional] 
**created_at** | **datetime** | ISO8601 datetime the record was created at. | [optional] 
**updated_at** | **datetime** | ISO8601 datetime the record was last updated at. | [optional] 
**any string name** | **bool, date, datetime, dict, float, int, list, str, none_type** | any string name can be used but the value must be the correct type | [optional]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


