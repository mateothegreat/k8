---
description: 'Common, useful commands that come in handy..'
---

# Commands

### Restarting a Deployment

```text
kubectl scale --current-replicas=0 --replicas=3 deployment/<deployment name>
kubectl scale --current-replicas=2 --replicas=3 deployment/<deployment name>
```



