# deleteCustomLiveStreamRecordTemplate


## Description
Delete user customized record template

## Request Method
DELETE

## Request Address
https://live.jdcloud-api.com/v1/recordCustoms/{template}

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**template**|String|True| |Record Template Customized Name|

## Request Parameter
None


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**requestId**|String|ruquestId|


## Return Code
|Return Code|Description|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|