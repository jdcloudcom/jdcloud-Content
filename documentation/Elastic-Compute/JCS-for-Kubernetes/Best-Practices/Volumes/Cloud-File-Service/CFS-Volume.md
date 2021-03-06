
# Define the Volume of the nfs type of JCS for Kubernetes with JD Cloud File Service

  JCS for Kubernetes provides the abstraction of Volume, and can support the container sharing file and file persistent volume scenario in Pod; NFS Volume allows that the existing NFS (network file system) is shared and attached to the cluster container, and the file content in NFS Volume can be reserved when Pod is deleted. Moreover, NFS can be mounted at the same time by various sources, meaning that NFS can provide data sharing between Pods of JCS for Kubernetes.

  JD Cloud File Service is a fully-hosted distributed file system with high reliability, expandability and sharable access. It supports standard NFSv4.0 and NFSv4.1 protocols and provides fully-hosted services, so you can achieve seamless integration with JCS for Kubernetes via standard file system attaching steps without modifying applications. For more details, please refer to the [JD Cloud File Service](https://docs.jdcloud.com/en/cloud-file-service/product-overview) documentation.
  
  This file will provide the operation steps and application examples of attaching JD Cloud File Service in JCS for Kubernetes by NFS Volume.
  
## I. Create CFS File Storage

1. You need to create a [CFS File Storage](https://docs.jdcloud.com/en/cloud-file-service/creating-file-system) first, and it is recommended that you create File Storage in Node Subnet in JCS for Kubernetes;

2. File Storage supports mounting File Storage through the IP address of the mount target, and you can query the IP address of the mount target in the File Storage Details, please refer to [File Storage Information](https://docs.jdcloud.com/en/cloud-file-service/file-system-detail) for detail.

## II. Connect to Cluster

 With the Kubernetes command line client kubectl, you can connect to JCS for Kubernetes from the client computer, realizing application deployment. For details, please refer to use of Kubectl client [Connect to JCS for Kubernetes](https://docs.jdcloud.com/en/jcs-for-kubernetes/connect-to-cluster).

## III. Pod uses CFS file storage by NFS Volume

**Description**: You need to install nfs drive on the Node of cluster. For drive installation process, please refer to [Attached File Storage](https://docs.jdcloud.com/en/cloud-file-service/mount-file-system)

```
#Run the commands below under Node terminal:

sudo yum install –y nfs-utils
```
    
1. Create a Pod, mount the CFS file storage created by the first part to Pod by NFS Volume, and write files under the CFS directory. Pod YAML file description is as follows:
```
kind: Pod
apiVersion: v1
metadata:
  name: write-data-to-cfs
spec:
  containers:
  - name: producer
    image: busybox
    imagePullPolicy: IfNotPresent
    command:
    - /bin/sh
    args:
    - -c
    - while true; do ts=`date +%s`; echo "${ts} hello world" >> /mnt/cfs-write/hello.log; sleep 1; done
    volumeMounts:
    - mountPath: "/mnt/cfs-write"       # you can modify the attached directory of CFS based on the project situation
      name: cfs
  volumes:
  - name: cfs
    nfs:
      path: /cfs			#Replace with the directory supported by the attached target, which is attached to the /cfs directory by default
      server: 10.**.**.11		#Replace it with the attached target IP address for file storage
      readOnly: false
```   

**Parameter Description:**

* The above-mentioned YAML file mounts the "/cfs" directory of CFS attached target to the /mnt/cfs-write directory of Pod;
* You can execute the commands below to download Yaml demo file:

`
wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/CFS/write-data-to-cfs.yml
`
* Before creating Pod, please modify the corresponding parameter value in Yaml file according to file storage information.

2. After using the Kubectl client [connect to JCS for Kubernetes](https://docs.jdcloud.com/en/jcs-for-kubernetes/connect-to-cluster), execute the following command to create Pod:
```
kubectl create -f write-data-to-cfs.yml       # file name write-data-to-cfs.yml can be replaced by the file saved in the local directory

kubectl get pods
NAME                READY   STATUS    RESTARTS   AGE
write-data-to-cfs   1/1     Running   0          3m1s
```

3. Execute the following command to enter Pod to view the content saved in /mnt/cfs-write/hello.log file:
```
kubectl exec -it write-data-to-cfs /bin/sh
/ # cat /mnt/cfs-write/hello.log
Output examples are as follows:
1564989208 hello world
1564989209 hello world
1564989210 hello world
1564989211 hello world
1564989212 hello world
1564989213 hello world
1564989214 hello world
1564989215 hello world
1564989217 hello world
1564989218 hello world

```

4. Execute the following command to delete Pod

```
kubectl delete pod write-data-to-cfs
pod "write-data-to-cfs" deleted
```

## IV. Verify Data Permanently Stored in CFS File Storage

1. Re-create a Pod, mount the CFS file created by the first part to Pod by NFS Volume, and verify the file content under the CFS directory. Pod Yaml file description is as follows:
```
kind: Pod
apiVersion: v1
metadata:
  name: read-data-from-cfs
spec:
  containers:
  - name: consumer
    image: busybox
    imagePullPolicy: IfNotPresent
    command:
    - /bin/sh
    args:
    - -c
    - while true; do ls -l /mnt/cfs-read/; sleep 2; done
    volumeMounts:
    - mountPath: "/mnt/cfs-read"		# you can modify the attached directory of CFS based on the project situation
      name: cfs
      readOnly: true
  volumes:
  - name: cfs
    nfs:
      path: /cfs		#Replace with the directory supported by the attached target, which is attached to the /cfs directory by default
      server: 10.**.**.11		          #Please keep attached targets and IP addresses for CFS file storage consistent with those used for test in Step 2
      readOnly: true
```     

**Parameter Description:**

* The above-mentioned YAML file attaches the "/cfs" directory of CFS attached target to the /mnt/cfs-read directory of Pod;
* You can execute the commands below to download Yaml demo file:

`
wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/CFS/read-data-from-cfs.yml
`

* Before creating Pod, please modify the corresponding parameter value in Yaml file according to file storage information.

2. Create Pod, and verify that Pod can be entered to view the file content under the /mnt/cfs-read directory through execution of the following command, when it is in running status.
```
kubectl create -f read-data-from-cfs.yml       # file name read-data-from-cfs.yml can be replaced with a file stored in a local directory

kubectl get pods
NAME                READY   STATUS    RESTARTS   AGE
read-data-from-cfs  1/1     Running   0          15s

kubectl exec -it read-data-from-cfs /bin/sh
/ # cat /mnt/cfs-read/hello.log
Output examples are as follows:
1564989208 hello world
1564989209 hello world
1564989210 hello world
1564989211 hello world
1564989212 hello world
1564989213 hello world
1564989214 hello world
1564989215 hello world
1564989217 hello world
1564989218 hello world
```
3. It can be found through verification of Step 7 that file hello.log written into CFS by Pod named as write-data-to-cfs is saved in CFS file for storage persistently, and can be shared by Pod named as read-data-from-cfs.

4. Execute the following command to delete Pod

```
kubectl delete pod read-data-from-cfs
pod "read-data-from-cfs" deleted
```