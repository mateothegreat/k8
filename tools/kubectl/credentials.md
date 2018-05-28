# Credentials

#### Create ServiceAccount

```text
kubectl create serviceaccount jenkins-sa
```

#### Retrieve \(decoded\) token from secret created for ServiceAccount

```text
kubectl get secret jenkins-sa-token-vnp5k -o jsonpath={.data.token} | base64 -d
```

#### Configuring a Service Account

```bash
kubectl config set-credentials sa-user --token=$(kubectl get secret <secret_name> -o jsonpath={.data.token} | base64 -d)
```

#### Creating a Cluster Admin Binding

```bash
kubectl create clusterrolebinding cluster-admin-binding --clusterrole=cluster-admin --user=$(gcloud info | grep Account | cut -d '[' -f 2 | cut -d ']' -f 1)
```



