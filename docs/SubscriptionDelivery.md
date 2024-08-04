# SubscriptionDelivery


## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**guid** | **str** | Auto-generated unique identifier for the subscription delivery. | 
**subscription_event_guid** | **str** | The subscription event guid of the subscription delivery. | 
**subscription_guid** | **str** | The subscription guid of the subscription delivery. | 
**state** | **str** | The state of the subscription delivery. | 
**attempt_count** | **int** | The number of attempts made to deliver the event. | 
**response** | **str, none_type** | The response of the subscription delivery. | [optional] 
**next_attempt_at** | **datetime, none_type** | ISO8601 datetime the next attempt will be made. | [optional] 
**completed_at** | **datetime, none_type** | ISO8601 datetime the event was delivered. | [optional] 
**failed_at** | **datetime, none_type** | ISO8601 datetime the event delivery was marked as failed. | [optional] 
**created_at** | **datetime** | ISO8601 datetime the record was created at. | [optional] 
**updated_at** | **datetime** | ISO8601 datetime the record was last updated at. | [optional] 
**any string name** | **bool, date, datetime, dict, float, int, list, str, none_type** | any string name can be used but the value must be the correct type | [optional]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


