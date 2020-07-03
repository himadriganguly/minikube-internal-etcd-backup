# Minikube Internal ETCD Backup

It will automatically create a backup of internal **etcd cluster** in minikube under /data/backup folder. This is done using **CronJob** in **Kubernetes**. The same procedure applies for any **K8s** cluster with internal **etcd cluster**.

## Requirement

1. Running instance of **Minikube** cluster.

## Modify YAML File

1. Check the image of **etcd** used. To do so login into **Minikube** instance and view the file **/etc/kubernetes/manifests/etcd.yaml**

```
minikube ssh
```

```
sudo cat /etc/kubernetes/manifests/etcd.yaml
```

under **spec.containers.image** you will get the image

```
image: k8s.gcr.io/etcd:3.4.3-0
```

then change the YAML accordingly on **line 15**.

2. Check for **--trusted-ca-file**, **--cert-file** and **--key-file** from the above **cat** output and replace on line **23**

replace the value of **--trusted-ca-file** in

```
--cacert=[CA CERT FILE PATH]
```

replace the value of **--cert-file** in

```
--cert=[SERVER CERT FILER PATH]
```

replace the value of **--key-file** in

```
--key=[SERVER KEY FILE PATH]
```
