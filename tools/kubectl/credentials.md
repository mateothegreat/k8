# Credentials

#### Create ServiceAccount

```bash
kubectl create serviceaccount jenkins-sa
```

#### Retrieve \(decoded\) token from secret created for ServiceAccount

```text
kubectl get secret jenkins-sa-token-vnp5k -o jsonpath={.data.token} | base64 -d
```

#### Create ~/.kube/config with CA & ServiceAccount Token

{% code-tabs %}
{% code-tabs-item title="~/.kube/config" %}
```yaml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: <insert plain text CA>
    server: https://<api endpoint>
  name: <cluster name>
contexts:
- context:
    cluster: <cluster name>
    namespace: default
    user: default
  name: <cluster name>
current-context: <cluster name>
kind: Config
preferences: {}
users:
- name: default
  user:
    as-user-extra: {}
    token: <insert base64 decoded token from service account user>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

```bash
kubectl config set-credentials sa-user \
        --token=$(kubectl get secret <secret_name> -o jsonpath={.data.token} | base64 -d)
```

#### Creating a Cluster Admin Binding

```bash
kubectl create clusterrolebinding jenkins-sa-binding \
        --clusterrole=cluster-admin \
        --user="system:serviceaccount:default:jenkins-sa"
```



