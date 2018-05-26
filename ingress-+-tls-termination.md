---
description: Terminate SSL via an ingress resource with the certificates from a secret.
---

# Ingress + TLS Termination

## Create TLS Secret

```text
kubectl create secret tls foo-secret --key /tmp/tls.key --cert /tmp/tls.crt
```

## Create Ingress Resource

{% code-tabs %}
{% code-tabs-item title="ingress.yaml" %}
```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: $HOST
  annotations:
    kubernetes.io/ingress.class: "nginx"   
spec:
  tls:
  - hosts:
    - $HOST
    secretName: tls-$HOST
  rules:
  - host: $HOST
    http:
      paths:
      - path: /
        backend:
          serviceName: $SERVICE_NAME
          servicePort: $SERVICE_PORT

```
{% endcode-tabs-item %}
{% endcode-tabs %}

