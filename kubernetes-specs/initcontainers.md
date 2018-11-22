# InitContainers

```yaml
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: grafana-core
  namespace: $NS
  labels:
    app: grafana
    component: corespec:  replicas: 1
  template:
    metadata:
      labels:
        app: grafana
        component: core
    spec:
      initContainers:
        - name: config-data
          image: busybox
          command: ["chown", "-R", "grafana:grafana", "/var/lib/grafana"]
          volumeMounts:
          - name: $GCE_DISK
            mountPath: /var/lib/grafana
      containers:
      - image: $IMAGE
        name: grafana-core
        imagePullPolicy: IfNotPresent
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
          requests:
            cpu: 100m
            memory: 100Mi
        readinessProbe:
          httpGet:
            path: /login
            port: 3000
          initialDelaySeconds: 60
          timeoutSeconds: 15
        securityContext:
          privileged: true
          allowPrivilegeEscalation: true
          capabilities:
            add: ["SYS_ADMIN"]
        volumeMounts:
          - name: $GCE_DISK
            mountPath: /var/lib/grafana
      volumes:
      - name: $GCE_DISK
        persistentVolumeClaim:
          claimName: $GCE_DISK
```



