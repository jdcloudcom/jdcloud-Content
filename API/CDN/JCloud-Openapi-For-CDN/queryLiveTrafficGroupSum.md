# queryLiveTrafficGroupSum


## Description
Search and count data and summarize as well as sum the same

## Request Method
POST

## Request Address
https://cdn.jdcloud-api.com/v1/liveStatistics:groupSum


## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**startTime**|String|True| |Search start time, UTC time, format: yyyy-MM-dd'T'HH:mm:ss’Z’, example: 2018-10-21T10:00:00Z|
|**endTime**|String|True| |Search end time, UTC time, format: yyyy-MM-dd'T'HH:mm:ss’Z’, example: 2018-10-21T10:00:00Z|
|**domain**|String|False| |Domain required to be searched must be domain with permission under user pin|
|**subDomain**|String|False| | |
|**appName**|String|False| |app Name|
|**streamName**|String|False| |Stream Name|
|**fields**|String|False| |Field Required To Be Searched|
|**area**|String|False| | |
|**isp**|String|False| | |
|**scheme**|String|False| |Searched Stream Protocol|
|**period**|String|False| |Time granularity, value: [oneMin,fiveMin,followTime], followTime only can return the summarized data|
|**groupBy**|String|False| |Grouping Basis|
|**reqMethod**|String|False| | |


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](querylivetrafficgroupsum#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**startTime**|String| |
|**endTime**|String| |
|**domain**|String| |
|**statistics**|[StatisticsGroupSumDataItem[]](querylivetrafficgroupsum#statisticsgroupsumdataitem)| |
### <div id="statisticsgroupsumdataitem">StatisticsGroupSumDataItem</div>
|Name|Type|Description|
|---|---|---|
|**startTime**|String|UTC time, format: yyyy-MM-dd'T'HH:mm:ss’Z’, example: 2018-10-21T10:00:00Z|
|**endTime**|String|UTC time, format: yyyy-MM-dd'T'HH:mm:ss’Z’, example: 2018-10-21T10:00:00Z|
|**data**|Object|Search result, the type is HashMap<String, Object>|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|