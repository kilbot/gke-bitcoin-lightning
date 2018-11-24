https://kubernetes.github.io/ingress-nginx/deploy/

```sh
$ kubectl create clusterrolebinding cluster-admin-binding --clusterrole cluster-admin --user $(gcloud config get-value account)
$ kubectl apply -f ingress-nginx.yaml
$ kubectl apply -f ingress-service.yaml
```
