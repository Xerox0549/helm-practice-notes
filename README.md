#helm installation command from here 

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```
```bash
chmod 700 get_helm.sh

./get_helm.sh

```
1. here the helm first command for create a apache server chart for a apache server

```bash
helm create apache-helm
```
2. now here to check service.yaml into tamplates file
3. and also check the values.yaml file for adding target port 
4. So after all the things we need to check chart.yml file
5. then we need to make a package file of using 
```bash
helm package apache-helm/
```
6. Now we need to install the currunt packege that are and give the name of the packege like dev-apache

```bash
helm install dev-apache apache-helm
```
7. now time to check pods so there are some pods thats are show running at dehault namespace

```bash
kubeclt get pods
kubectl get svc
kuberctl get deployment
```
8. so here is a problem to namespace so always create a name space 
```bash
helm install dev-apache apache-helm -n apache-helm --create-namespace
```
 So here we neer to check the all again its show all running with one pods
 ```bash
kubeclt get pods -n apache-helm
kubectl get svc -n apache-helm
kuberctl get deployment -n apache-helm
```

9. Also make a production-apache like dev-apache
``` bash
helm install pre-apache apache-helm -n apache-helm --create-namespace 
```
check the all things as same 
```bash
kubeclt get pods -n apache-helm
kubectl get svc -n apache-helm
kuberctl get deployment -n apache-helm
```
10. Now if we need to scale the pods of the apache server like pre-apache or dev-apache so we need to make changes into the vim apache-helm./Chart.yaml and vim apache-helm.yaml/values.yaml and here we need mention a update version of apache and replicas count=3 for a particular server as like ether pre-apache or dev-apache
11. And now we need to recreate package using
```bash
helm package apache-helm 
```bash
helm upgrade pro-apache ./apache-helm -n pro-apache
```
12. if we need to roll back of any specific previous pod for revising number 1 means that we are going to back at previous version and check the pods and show it previous version
```bash
helm rollback pro-apache 1 pro-apache
```
13. for checking the pods 
```
kubeckt get pods -n pro-apache
```
14. Now if we create to create a node.js aap using helm 
```bash
helm create node-js-app
```
# after that making the file we need to make it package of the node-js-app befor making this we can change the file configuration of chart.yml and templates/servicce.yml for targetport mapping
1. make a package of node.js of 
```bash
helm package node-js-app/
helm install dev-node-js-app node-js-app -n dev-node --create-namespace 
```
# for the check pods id is running or not 
```bash
kubectl get pods -n dev-node
```
# for the check service is it running or not 
```bash
kubectl get svc -n dev-node
```
# Now here we perform port forwarding of service for check the user interface
```bash
kubectl Port-forwarding svc/dev-node-app -n dev-node-app 8000:8000 --address=0.0.0.0
```
## helm using helm 

```bash
Helm search repo {repo-name}
```













