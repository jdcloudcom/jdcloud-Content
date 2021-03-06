# Resource Pool Management

Resource pool is a concept of a group of resource collection. With the resource pool, resources such as Virtual Machines and Containers under the namespace can be managed.

**Description:**

-   One resource pool can only serve one namespace. However, there are several resource pools under one namespace.
-   A user can create/delete resource pools, import Virtual Machines and export Virtual Machines in the resource pool.

## Preparatory Work

If the user plans to create VM resource type, then before creating a resource pool, it is deemed by default that the user has purchased/subscribed Virtual Machines, Virtual Private Cloud and other resources;

If the user plans to create K8S resource type, then before creating a resource pool, it needs to be deemed by default that the user has purchased/subscribed resources related to cloud K8S;


## Operation Steps

### Create Resource Pool

1.	Log in the JD Distributed Service Framework Console. Click **Resource Management** on the left side navigation bar and log in the resource pool management list.

![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-list-1.png)

2. 	Click **Create Resource Pool** on the top of the list and log in the creation page. Set information of resource pool and click **OK** to complete creation.

If the user creates Virtual Machines resource, it needs to associate the corresponding Virtual Private Cloud.

![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-create-pool-1.png)

If the user creates K8S resource, it needs to associate the corresponding K8S cluster.

![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-create-pool-k8s.png)


3. Resource pool information

In which the available number of Virtual Machines refers to the number of running Virtual Machines; Resource Pool Virtual Machines refer to the total number of Virtual Machines in this resource pool.

![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-pool-detail.png)

| Field | Description |
| :- | :- |
|  Available Count of Virtual Machines |  Refers to the number of running Virtual Machines. |
|  Resource Pool Virtual Machines  |  Refer to the total count of Virtual Machines in this resource pool.  |
|  Ownership Namespace  |  Refers to the namespace attributed in JDSF in this resource pool.  |


4. The Virtual Machine information in resource pool

![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-pool-vmlist.png)


**Note:**

-   The resource pool and the namespace to be served by such resource pool shall be in the same VPC.
-   Users can create/delete resource pools, import Virtual Machines and remove Virtual Machines in the resource pool.
 

### Deletion of Resource Pool

1. 	Log in the JD Distributed Service Framework Console. Click **Resource Management** on the left side navigation bar and log in the resource pool list page.

![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-list-1.png)

2. 	For resources to be deleted, click **Deletion** on the operation bar.

1) For Virtual Machines type resource:

- Before deleting the resource pool, all Virtual Machines in the resource pool need to be deleted.

- Before deleting the resource pool, you need to disassociate the deployment group that is associated on the Virtual Machines.

- Before deleting the data, the user needs to well complete data backup work on his/her own.

2) For K8S type resource:

- Before deleting, you need to delete the application deployed through the resource pool.

- Deletion is to disassociate K8S with JDSF platform.



### Import of Virtual Machines

1. 	Log in the JD Distributed Service Framework Console. Click **Resource Management** on the left side navigation bar and log in the resource pool list page.

2. 	For the resource pool to be operated, click **Import Virtual Machines** on the operation bar.


![](../../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/rsm-import-1.png)


**Description:**

1. Now, only Virtual Machines under the same VPC can be associated and those unassociated can be imported.

2. One Virtual Machine can be associated with 1 resource pool.


### Removal of Virtual Machines

1. Log in the JD Distributed Service Framework Console.	Click **Resource Management** on the left side navigation bar and log in the resource pool list page.

2. Click ID, log in the list page of Virtual Machines, select Virtual Machines to be removed and delete them. Before deleting data, a user needs to disassociate Virtual Machines from the deployment group and then delete the same.

3. Before deletion, a user needs to complete data backup work on his/her own.



