# CompreFace-kubernetes

### Origin project for Docker-compose
### https://github.com/exadel-inc/CompreFace
---
## Minikube
Fixed version 0.5.1 and enviroment variables

### Manual

1. (optional) create namespace and switch context
> kubectl apply -f minikube/0-ns.yaml

> kubectl config set-context --current --namespace=compreface

2. Deploy db
> kubectl apply -f minikube/1-db.yaml

3. Deploy CompreFace modules
> kubectl apply -f minikube/2-core.yaml -f minikube/3-api.yaml -f minikube/4-admin.yaml -f minikube/5-fe.yaml

4. For expose to network run on host
> minikube service compreface-ui

###Helm Chart
Install Helm https://helm.sh/docs/intro/install/

All necessary templates and values.yaml for helm chart you can find in the compreface-kubernetes folder

1. Install compreface chart. It will deploy the whole compreface application
>helm install compreface-kubernetes ./compreface-kubernetes --namespace compreface --create-namespace

2. Run minikube service for public access from your browser
>minikube service compreface-ui -n compreface

3. Delete compreface chart. It will terminate compreface application
>helm delete compreface-kubernetes -n compreface

## TODO
- deployments on AWS-GCP-Azure
- enviroment variables
- scalling