# createAliasIp


## Description
Add alias IP

## Request Method
PUT

## Request Address
https://edcps.jdcloud-api.com/v1/regions/{regionId}/aliasIps

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID, calling APIs (describeEdCPSRegions) to get regions supported by Distributed Cloud Physical Server|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**clientToken**|String|False| |Generated by the client to guarantee idempotence of request, and the length cannot exceed 36 characters;<br/><br>if multiple requests use the same clientToken, only the first request will be executed and the following requests will directly return the result of the first request<br/><br>|
|**aliasIpSpec**|[AliasIpSpec](createaliasip#aliasipspec)|True| |Alias IP Configuration|

### <div id="aliasipspec">AliasIpSpec</div>
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**instanceId**|String|False| |Instance ID|
|**aliasIps**|[AliasIpInfo[]](createaliasip#aliasipinfo)|False| |Alias ip Configuration|
### <div id="aliasipinfo">AliasIpInfo</div>
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**id**|String|False| |Primary CIDR or Secondary CIDR id|
|**cidr**|String|False| |cidr Fragment|

## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](createaliasip#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**successList**|[AliasIpSuccessInfo[]](createaliasip#aliasipsuccessinfo)| |
|**errorList**|[AliasIpErrorInfo[]](createaliasip#aliasiperrorinfo)| |
### <div id="aliasiperrorinfo">AliasIpErrorInfo</div>
|Name|Type|Description|
|---|---|---|
|**cidr**|String|cidr Fragment|
|**message**|String|Error Information|
### <div id="aliasipsuccessinfo">AliasIpSuccessInfo</div>
|Name|Type|Description|
|---|---|---|
|**aliasIpId**|String|Alias IP id|
|**cidr**|String|cidr Fragment|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
