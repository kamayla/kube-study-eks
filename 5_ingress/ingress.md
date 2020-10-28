# IngressをEKS Cluster内にインストール
```
kubectl create namespace nginx-ingress-controller

helm install nginx-ingress-controller stable/nginx-ingress -n nginx-ingress-controller
```