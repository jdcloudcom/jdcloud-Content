# stopLoadBalancer


## Description
Disable Load Balancer Instance

## Request Method
PUT

## Request Address
https://cps.jdcloud-api.com/v1/regions/{regionId}/slbs/{loadBalancerId}:stopLoadBalancer

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID, call the API (describeCPSLBRegions) to get regions supported by Cloud Physical Server|
|**loadBalancerId**|String|True| |Load Balancer Instance ID|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**clientToken**|String|False| |Generated by the client to guarantee idempotence of request, and the length cannot exceed 36 characters;<br/><br>if multiple requests use the same clientToken, only the first request will be executed and the following requests will directly return the result of the first request<br/><br>|


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](stoploadbalancer#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**success**|Boolean|Load Balancer instance is disabled or not|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
