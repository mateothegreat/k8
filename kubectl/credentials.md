# Credentials

#### Configuring a Service Account

```bash
kubectl config set-credentials sa-user --token=$(kubectl get secret <secret_name> -o jsonpath={.data.token} | base64 -d)
```

#### Creating a Cluster Admin Binding

```bash
kubectl create clusterrolebinding cluster-admin-binding-shawn --clusterrole=cluster-admin --user=$(gcloud info | grep Account | cut -d '[' -f 2 | cut -d ']' -f 1)
```



