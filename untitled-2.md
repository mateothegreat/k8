# Credentials

```bash
kubectl config set-credentials sa-user --token=$(kubectl get secret <secret_name> -o jsonpath={.data.token} | base64 -d)
```

