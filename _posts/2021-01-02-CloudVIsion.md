---
layout: post
title: Cloud Vision API from a Kubernetes Cluster
category: 05_Cloud
tag: [Kubernetes, CloudVision]
---

This is for Cloud Vision API from a Kubernetes Cluster that  uses Kubernetes and Cloud Vision API. The guide is from Awwvision: Cloud Vision API from a Kubernetes Cluster 
> https://codelabs.developers.google.com/codelabs/awwvision-cloud-vision-api-from-a-kubernetes-cluster/index.html?index=..%2F..index#0


----



![lca-example](/assets/images/cloudVision.png)


#### Setup and Requirements
- Project ID : my-kubernetes-codedlab
- To authenticate, type gcloud auth list
- Then, gcloud config list project
- Enable the Vision API by visiting the APIs & Services Dashboard on the cloud console

#### Create a Container Engine cluster
- gcloud config set compute/zone `us-central1-f`
- gcloud container clusters create awwvision \
    - num-nodes 2 \
    - scopes cloud-platform
- gcloud container clusters get-credentials awwvision
- kubectl cluster-info

#### Get the Sample
- `git clone https://github.com/GoogleCloudPlatform/cloud-vision`

#### Deploy the sample
- `cd cloud-vision/python/awwvision`
- `make all`

#### Check the Kubernetes resources on the cluster
- `kubectl get pods`
```
dmjgr5@cloudshell:~/cloud-vision/python/awwvision (my-kubernetes-codedlab)$ kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
awwvision-webapp-5886b65c78-9bzkr   1/1     Running   1          115s
awwvision-worker-f56647b49-4w6dp    1/1     Running   0          48s
awwvision-worker-f56647b49-9qc6p    1/1     Running   0          48s
awwvision-worker-f56647b49-f5sbk    1/1     Running   0          48s
redis-master-7c9dc65556-ln25v       1/1     Running   0          3m47s
```

- `kubectl get deployments -o wide`
```
dmjgr5@cloudshell:~/cloud-vision/python/awwvision (my-kubernetes-codedlab)$ kubectl get deployments -o wide
NAME               READY   UP-TO-DATE   AVAILABLE   AGE     CONTAINERS         IMAGES                                           SELECTOR
awwvision-webapp   1/1     1            1           2m6s    awwvision-webapp   gcr.io/my-kubernetes-codedlab/awwvision-webapp   app=awwvision,role=frontend
awwvision-worker   3/3     3            3           59s     awwvision-worker   gcr.io/my-kubernetes-codedlab/awwvision-worker   app=awwvision,role=worker
redis-master       1/1     1            1           3m58s   redis-master       redis  
```

- `kubectl get svc awwvision-webapp`
```
dmjgr5@cloudshell:~/cloud-vision/python/awwvision (my-kubernetes-codedlab)$ kubectl get svc awwvision-webapp
NAME               TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)        AGE
awwvision-webapp   LoadBalancer   10.31.252.91   34.67.220.234   80:30166/TCP   2m29s
```

#### Visit your new web app and start its crawle
- Copy and paste the external IP of the awwvision-webapp service into a new browser to open the webapp, then click Start the Crawler button.
- To delete your Kubernetes pods, replication controllers, and services, and to remove your auto-generated .yaml files, do: make delete













