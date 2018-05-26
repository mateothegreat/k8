---
description: Services provide the means for pods to communicate with each other.
---

# Services

## Example Service Spec

Becoming a super hero is a fairly straight forward process:

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

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

```
// Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```



