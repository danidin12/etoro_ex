# Getting Started

## Installations
- azure-cli
- helm
- kubectl

## First Steps
1. Login to azure using managed identity.
```bash
    curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/' -H Metadata:true   
```
2. Connect to AKS.
```bash
az aks get-credentials --resource-group devops-interview-rg --name devops-interview-aks

kubectl config use-context devops-interview-aks
```

3. Check AKS connection by getting the cluster nodes.
```bash
kubectl get nodes -o wide
```


# NGINX Steps
1. Install NGINX controller.
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml

kubectl get pods -n ingress-nginx \
  -l app.kubernetes.io/name=ingress-nginx --watch

``` 
# Helm Steps
1. Create and deploy helm chart for simple-web.

```bash
helm create simple-web
```

2. Set image and registry variables in [values.yaml](/simple-web/values.yaml) file.

3. Run helm chart.
```bash
helm install simple-web ./simple-web
```

4. Enable [hpa.yaml](simple-web/templates/hpa.yaml) and [ingress.yaml](simple-web/templates/ingress.yaml).
   
5. Change from cluster IP to Load Balancer by adding service section in [values.yaml](/simple-web/values.yaml) file.
   
# Jenkins Steps
url : http://20.73.17.32:8080/

user: user

password : Password1
1. Install jenkins.
2. Create a new item.
3. Connect the item to the git repository.
4. Add an execute shell run command in the build section.
   ```
   helm install simple-web ./simple-web
   ```
5. Run build 


FINISH
🔥🔥🔥🔥🔥🔥🔥🔥