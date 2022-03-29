# Elastic Cloud on Kubernetes

Steps and resources for setting up Elastic Cloud on Azure Kubernetes Service

### Installing the Elastic Operator for Kubernetes

```bash

cd elastic-cloud-on-kubernetes

helm upgrade --install elastic-infra infrastructure

```


### Installing the ElasticSearch Cluster


```bash

cd elastic-cloud-on-kubernetes

helm upgrade --install elastic-cluster resources

```

### Getting the Password for Elasticsearch

```bash


PASSWORD=$(kubectl -n searchzone get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}')

echo $PASSWORD

curl -u "elastic:$PASSWORD" -k "https://localhost:9200"

```

https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-managing-compute-resources.html

https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-autoscaling.html

https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-stateless-autoscaling.html

