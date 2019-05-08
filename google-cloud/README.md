# Google Cloud Platform

## Obtain an image from GCR and run a pod

#### Build an app

> docker build -t simpleapp:latest

#### Push app to GCR

> docker tag simpleapp:latest us.gcr.io/repo-name/simpleapp:latest

> gcloud auth configure-docker

> docker push us.gcr.io/repo-name/simpleapp:latest

#### Create GCP Service Account

From console, create a service account with name image-puller and save the configuration file(.json)

#### Create Kubernetes secret

```
$ kubectl create secret docker-registry gcr-json-key \
--docker-server=us.gcr.io \
--docker-username=_json_key \
--docker-password="$(cat ./ckad.json)" \
--docker-email=suryavallabhaneni@gmail.com
```

#### Use Secret in Pod Spec

```
apiVersion: v1
kind: Pod
metadata:
  name: simpleapp
spec:
  containers:
  - name: simpleapp
    image: us.gcr.io/reponame/simpleapp
  imagePullSecrets:
  - name: gcr-json-key
```

#### Create Pod

> kubectl apply -f simpleapp.yaml

```
# kubectl get pods
NAME        READY   STATUS    RESTARTS   AGE
simpleapp   1/1     Running   0          8m8s
```

```
Events:
  Type    Reason     Age   From                       Message
  ----    ------     ----  ----                       -------
  Normal  Pulled     6s    kubelet, ip-172-31-21-230  Successfully pulled image "us.gcr.io/repo-name/simpleapp@sha256:"
  Normal  Created    6s    kubelet, ip-172-31-21-230  Created container simpleapp
  Normal  Started    6s    kubelet, ip-172-31-21-230  Started container simpleapp
```
