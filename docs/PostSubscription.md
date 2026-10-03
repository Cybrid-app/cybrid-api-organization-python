# PostSubscription

Request body for subscription creation.

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**environment** | **str** | The environment that the subscription is configured for. | 
**type** | **str** | Type of the subscription. | 
**name** | **str** | Name provided for the subscription. | 
**event_types** | **[str], none_type** | Event types delivered to the subscription, within those its channel supports; omitted or null means no narrowing. | [optional] 
**url** | **str, none_type** | URL provided for the subscription. Required when type is webhook. | [optional] 
**recipient** | **str, none_type** | Recipient email address. Required when type is email. | [optional] 
**any string name** | **bool, date, datetime, dict, float, int, list, str, none_type** | any string name can be used but the value must be the correct type | [optional]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


