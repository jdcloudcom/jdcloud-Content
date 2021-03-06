# deleteInstance


## Description
Please delete a single Virtual Machine which is paid by configuration and whose monthly package is expired. Virtual Machines without billing information cannot be deleted, but excluding the loss of billing information caused by such case: After requesting to delete Virtual Machines, the abnormal billing information in the system has been deleted but the resource cleanup failed.<br>
The VM status must be <b>running</b>, <b>stopped</b>, or <b>error</b>, and the deletion is only availabe when there is no task in progress of the VM. <br>
The VM that has not expired in monthly package cannot be deleted.
If the cloud disks attached to the VM is billed by configuration and the AutoDelete attribute is true, then the data disk will be deleted along with the VM.
</br>Sensitive operation, enable<a href="https://docs.jdcloud.com/IAM/Operation-Protection">MFA operation protection</a>

## Request method
DELETE

## Request address
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**instanceId**|String|True| |VM ID|

## Request parameter
None


## Response parameter
None


## Response code
|Return code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
