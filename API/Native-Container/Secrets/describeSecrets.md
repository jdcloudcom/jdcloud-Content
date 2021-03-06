# describeSecrets


## Description
Search secret list. <br> 
This API supports paging query with 20 items per page by default.


## Request method
GET

## Request address
https://nativecontainer.jdcloud-api.com/v1/regions/{regionId}/secrets

|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## Request parameter
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |Page; 1 by default|
|**pageSize**|Integer|False| |Page size; it is 20 by default; value range[10, 100]|
|**filters**|[Filter[]](describesecrets#filter)|False| |The name - secret is the name, supporting fuzzy search<br>|

### <div id="filter">Filter</div>
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**name**|String|True| |Name of Filter Requirements|
|**operator**|String|False| |Operator of filter requirements is eq by default|
|**values**|String[]|True| |Value of Filter Requirements|

## Response parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](describesecrets#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**secrets**|[Secret[]](describesecrets#secret)| |
|**totalCount**|Number| |
### <div id="secret">Secret</div>
|Name|Type|Description|
|---|---|---|
|**name**|String|Confidential Data Name|
|**secretType**|String|Now, only the following private data type is supported: docker-registry, which is the docker registry verification type|
|**createdAt**|String|Creation Time|
|**data**|[DockerRegistryData](describesecrets#dockerregistrydata)|Confidential Data|
### <div id="dockerregistrydata">DockerRegistryData</div>
|Name|Type|Description|
|---|---|---|
|**server**|String|Registry Server Address|
|**username**|String|User Name|
|**password**|String|Password |
|**email**|String|Email Address|

## Response code
|Return code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
