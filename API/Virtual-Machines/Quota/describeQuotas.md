# describeQuotas


## Description
Current support to query the quota of VM, image, key pair, launch template and image share operation.


## Request method
GET

## Request address
https://vm.jdcloud-api.com/v1/regions/{regionId}/quotas

|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## Request parameter
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**filters**|Filter[]|False| |resourceTypes - Resource types, multiple support [instance, keyair, image, instanceTemplate]<br>|
|**imageId**|String|False| |Private image Id, this parameter must be uploaded when querying imageShare quota|

### Filter
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**name**|String|True| |Name of Filter Requirements|
|**operator**|String|False| |Operator of filter requirements is eq by default|
|**values**|String[]|True| |Value of Filter Requirements|

## Response parameter
|Name|Type|Description|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|Name|Type|Description|
|---|---|---|
|**quotas**|Quota[]|Quota list|
### Quota
|Name|Type|Description|
|---|---|---|
|**resourceType**|String|Source Type [instance, keypair, image, instanceTemplate]|
|**limit**|Integer|Upper Quota Limit|
|**used**|Integer|Used Quota|

## Response code
|Return code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|