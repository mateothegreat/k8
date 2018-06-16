---
description: Services provide the means for pods to communicate with each other.
---

# Services

## Example Service Spec

{% code-tabs %}
{% code-tabs-item title="service.yaml" %}
```yaml
apiVersion: v1
kind: Service
metadata:
  name: mysql
  labels:
    app: mysql
spec:
  ports:
    - port: 3306
      targetPort: 3306
  selector:
    app: mysql
```
{% endcode-tabs-item %}
{% endcode-tabs %}



