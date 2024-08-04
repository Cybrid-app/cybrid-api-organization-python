# SubscriptionEvent


## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**guid** | **str** | Auto-generated unique identifier for the subscription event. | 
**event_type** | **str** | The type of the subscription event. One of transfer.created or transfer.updated. | 
**object_guid** | **str** | The object guid for which the event is received. | 
**organization_guid** | **str** | The organization guid of the subscription event. | 
**created_at** | **datetime** | ISO8601 datetime the record was created at. | 
**environment** | **str** | The environment that the subscription event is configured for; one of sandbox or production. | [optional] 
**updated_at** | **datetime** | ISO8601 datetime the record was last updated at. | [optional] 
**any string name** | **bool, date, datetime, dict, float, int, list, str, none_type** | any string name can be used but the value must be the correct type | [optional]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


