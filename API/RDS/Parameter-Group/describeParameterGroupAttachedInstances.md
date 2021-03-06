# describeParameterGroupAttachedInstances


## Description
View Cloud Database Instance associated by Parameter Set<br>- Only support MySQL

## Request Method
GET

## Request Address
https://rds.jdcloud-api.com/v1/regions/{regionId}/parameterGroups/{parameterGroupId}/instances

|Name|Type|Required or not|Default Value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**parameterGroupId**|String|True| |Parameter Group ID|

## Request Parameters
|Name|Type|Required or not|Default Value|Description|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |Pages displaying data, which is 1 by default with the value range: [-1,∞). When pageNumber is -1, return all data page numbers; when exceeding total pages, display the last page|
|**pageSize**|Integer|False| |Data entries displayed on each page, which is 10 by default with the value range: [10,100] and a multiple of 10.|


## Returned Parameters
|Name|Type|Description|
|---|---|---|
|**result**|[Result](describeparametergroupattachedinstances#result)| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**instances**|[AttachedDBInstance[]](describeparametergroupattachedinstances#attacheddbinstance)| |
|**totalCount**|Integer| |
### <div id="attacheddbinstance">AttachedDBInstance</div>
|Name|Type|Description|
|---|---|---|
|**instanceId**|String|Instance ID|
|**instanceName**|String|Instance Name, see Help Center Document [Name and Password Restrictions](../../../documentation/Database-and-Cache-Service/RDS/Introduction/Restrictions/SQLServer-Restrictions.md) for specific rules|
|**instanceType**|String|Instance type, e.g., primary instance, read-only instance, etc., see [Enum parameter definition](../Enum-Definitions/Enum-Definitions.md) for details|
|**engine**|String|Instance engine types, e.g., MySQL or SQL Server, etc., see [Enum parameter definition](../Enum-Definitions/Enum-Definitions.md) for details|
|**engineVersion**|String|Instance engine version, see [Enum parameter definition](../Enum-Definitions/Enum-Definitions.md) for details|
|**parameterGroupId**|String|Parameter group ID|
|**parameterStatus**|String|Parameter status, see [Enum parameter definition](../Enum-Definitions/Enum-Definitions.md)|
|**instanceStatus**|String|Instance status, see [Enum parameter definition](../Enum-Definitions/Enum-Definitions.md)|
|**createTime**|String|Instance Creation Time|

## Return Code
|Return Code|Descripton|
|---|---|
|**200**|OK|

## Request Example
GET
```
public void testDescribeParameterGroupAttachedInstances() {
    DescribeParameterGroupAttachedInstancesRequest request = new DescribeParameterGroupAttachedInstancesRequest();
    request.setPageNumber(1);
    request.setPageSize(20);
    request.setParameterGroupId("mysql-pg-mpzspoh243");
    request.setRegionId("cn-north-1");
    DescribeParameterGroupAttachedInstancesResponse response = rdsClient.describeParameterGroupAttachedInstances(request);
    System.out.println(new Gson().toJson(response));
}

```

## Return Example
```
{
    "requestId": "bpaoeib2c7hcvwcso2ujcq31m9quh18f", 
    "result": {
        "instances": [
            {
                "createTime": "2020-01-07 18:42:46", 
                "engine": "MySQL", 
                "engineVersion": "5.7", 
                "instanceId": "mysql-k67q8n46si", 
                "instanceName": "hdj_test", 
                "instanceStatus": "ACTIVE", 
                "instanceType": "cluster", 
                "parameterGroupId": "mysql-pg-mpzspoh243", 
                "parameterStatus": "VALID"
            }
        ], 
        "totalCount": 1
    }
}
```
