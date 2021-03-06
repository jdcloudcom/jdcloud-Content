# modifyElasticIpBandwidth


## Description
Modify elastic IP bandwidth


## Request Method
PUT

## Request Address
https://cps.jdcloud-api.com/v1/regions/{regionId}/elasticIps/{elasticIpId}:modifyElasticIpBandwidth

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID, call API (describeRegiones) to get regions supported by Cloud Physical Server|
|**elasticIpId**|String|True| |Elastic IPID|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**clientToken**|String|False| |Generated by the client to guarantee idempotence of request, and the length cannot exceed 36 characters;<br/><br>if multiple requests use the same clientToken, only the first request will be executed and the following requests will directly return the result of the first request<br/><br>|
|**bandwidth**|Integer|True| |Bandwidth, unit Mbps, value range [1,200]|


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](modifyelasticipbandwidth#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**success**|Boolean|Whether the bandwidth modification succeeded|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
