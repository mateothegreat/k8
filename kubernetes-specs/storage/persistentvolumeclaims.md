# PersistentVolumeClaims

{% code-tabs %}
{% code-tabs-item title="pvc.yaml" %}
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: fast
  resources:
    requests:
      storage: 100Gi

```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
storageClassName can be of "slow" or "fast".  
"fast" is typically used with cloud providers to indicate SSD type backed storage devices.
{% endhint %}
