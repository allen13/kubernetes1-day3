kubernetes 1 day 3
------------------

Topics

* yaml
* volumes
* configmaps
* secrets
* persistent volumes
* storage class
* deploy wordpress with mysql backend

yaml
----

YAML Ain't Markup Language is a data serialization language that matches user’s expectations about data. It designed to be human friendly and works perfectly with other programming languages. It is useful to manage data and includes Unicode printable characters.

Understanding YAML is important because almost all container related configuration depends on it. A few examples are:

* Docker Compose
* All Kubernetes configs
* Github Actions
* Gitlab CI

Learn how to use yaml by reviewing the tutorial and typing each example into a yaml to json converter

* [tutorial](https://learnxinyminutes.com/docs/yaml/)
* [yaml to json](https://onlineyamltools.com/convert-yaml-to-json)

volumes
-------

Kubernetes supports many types of volumes. A Pod can use any number of volume types simultaneously. Ephemeral volume types have a lifetime of a pod, but persistent volumes exist beyond the lifetime of a pod. Consequently, a volume outlives any containers that run within the pod, and data is preserved across container restarts. 

Links
* [Volumes](https://kubernetes.io/docs/concepts/storage/volumes/)

configmaps
----------

A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume.

A ConfigMap allows you to decouple environment-specific configuration from your container images, so that your applications are easily portable.

Links
* [Configmap](https://kubernetes.io/docs/concepts/configuration/configmap/)
* [Configure a Pod Configmap](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)

secrets
-------

Kubernetes Secrets let you store and manage sensitive information, such as passwords, OAuth tokens, and ssh keys. Storing confidential information in a Secret is safer and more flexible than putting it verbatim in a Pod definition or in a container image.

Links
* [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/)
* [Managing secrets with kubectl](https://kubernetes.io/docs/tasks/configmap-secret/managing-secret-using-kubectl/)

persistent volumes
------------------

A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes. It is a resource in the cluster just like a node is a cluster resource. PVs are volume plugins like Volumes, but have a lifecycle independent of any individual Pod that uses the PV. This API object captures the details of the implementation of the storage, be that NFS, iSCSI, or a cloud-provider-specific storage system.

A PersistentVolumeClaim (PVC) is a request for storage by a user. It is similar to a Pod. Pods consume node resources and PVCs consume PV resources. Pods can request specific levels of resources (CPU and Memory). Claims can request specific size and access modes (e.g., they can be mounted ReadWriteOnce, ReadOnlyMany or ReadWriteMany, see AccessModes).

Links
* [Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)

storage class
-------------

A StorageClass provides a way for administrators to describe the "classes" of storage they offer. Different classes might map to quality-of-service levels, or to backup policies, or to arbitrary policies determined by the cluster administrators. Kubernetes itself is unopinionated about what classes represent. This concept is sometimes called "profiles" in other storage systems

Links
* [Storage Class](https://kubernetes.io/docs/concepts/storage/storage-classes/)

deploy wordpress with mysql backend
-----------------------------------

Create a secret that contains the contents of the mysql-pass file. Feel free to change the passoword.

    oc create secret generic mysql-pass --from-file=./password

Deploy mysql

    oc apply -f mysql-deployment.yml

Deploy wordpress

    oc apply -f wordpress-deployment.yml
