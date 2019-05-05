# How-To create individual Kubernetes objects writing with hand

## Persistent-Volume

[Create-PV](./files/create-persistent-volume.yaml)

> kubectl apply -f create-persistent-volume.yaml

```
NOTE: the hostPath: | path: "/data/basicservice" should be available before hand creating a persistent volume.

If it does not exist, create a directory with `mkdir -m 755 -p /data/basicservice`
```
### Verify if Persistent Volume was created

> kubectl get pv

#### Kubernetes Documentation

## Persistent-Volume-Claim

[Create-PVC](./files/create-persistent-volume-claim.yaml)

> kubectl apply -f create-persistent-volume-claim.yaml

### Verify if Persistent Volume Claim was created

> kubectl get pvc

#### Kubernetes Documentation

## Config-Map

[Create-CM](./files/create-configmap.yaml)

## Pod

[Create-Pod](./files/create-pod.yaml)

## Service

[Create-Service](./files/create-service.yaml)

## Service-with-NodePort

[Create-Svc-NodePort](./files/create-service-nodeport.yaml)

## Deployment

[Create-Deployment](./files/create-deployment.yaml)

## StatefulSet

[Create-Sts](./files/create-statefulset.yaml)

## DaemonSet

[Create-Ds](./files/create-daemonset.yaml)

## Jobs

[Create-Job](./files/create-job.yaml)

## Cron-Jobs

[Create-CronJob](./files/create-cronjob.yaml)
