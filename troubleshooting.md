# Troubleshooting

### Force pod deletion

```bash
kubectl delete <pod> --grace-period=0 --force
```

