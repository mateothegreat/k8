---
description: >-
  The Ingress Resource specifies hostname(s) and path(s) mapping to a specific
  Service. The Ingress Controller uses Ingres Resources as a means of
  configuration.
---

# Ingress

{% hint style="info" %}
Be careful when thinking about an "Ingress Resource"!  
  
This should not be confused with the actual "Ingress Controller", which is just a pod running nginx that performs traffic routing as if you were performing a bunch of re-writes.
{% endhint %}

### Ingress with SSL & Basic Auth

{% code-tabs %}
{% code-tabs-item title="ingress.yaml" %}
```yaml
apiVersion: extensions/v1beta1kind: Ingressmetadata:  name: <hostname>  annotations:    kubernetes.io/ingress.class: "nginx"    nginx.ingress.kubernetes.io/auth-type: basic    nginx.ingress.kubernetes.io/auth-secret: nginx-ingress-basic-auth    nginx.ingress.kubernetes.io/auth-realm: "Authentication Required - foo"spec:  tls:  - hosts:    - <hostname>    secretName: <tls secret name>  rules:  - host: <hostname>    http:      paths:
      - path: /        backend:          serviceName: <service name to map to>          servicePort: <service port to map to>
```
{% endcode-tabs-item %}
{% endcode-tabs %}



