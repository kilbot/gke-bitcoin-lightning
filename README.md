## Step 1: Create a GKE cluster

```sh
$ gcloud container clusters create gke-bitcoin-lightning --num-nodes=3
```

## Step 2: Create your PersistentVolumes and PersistentVolumeClaims

```sh
$ kubectl apply -f bitcoin-volumeclaim.yaml
$ kubectl get pvc
```

## Step 3: Add secrets

```sh
# add your secrets to bitcoin-secrets.yaml as base64 encoded
$ echo -n <RPCUSER> | base64
$ echo -n <RPCPASS> | base64

# create secrets
$ kubectl create -f ./bitcoin-secrets.yaml
```

## Step 4: Deploy Bitcoin

```sh
# create pod
$ kubectl create -f bitcoin.yaml

# check to see if pod is running
$ kubectl get pod -l app=bitcoind

# (optional) exec into bitcoin pod
$ kubectl exec -it <POD NAME>  bash
```

## Step 3: Create Bitcoin service

```sh
$ kubectl create -f bitcoin-service.yaml

## check to see if pod is running
$ kubectl get service bitcoind
```
