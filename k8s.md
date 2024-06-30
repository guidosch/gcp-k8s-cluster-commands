# K8s commands

### check current environment

```
k config current-context
```

### Secrets
```
# list secrets
k get secrets
# show content of secret
k get secret superset-1-postgresql-secret -o jsonpath='{.data}'
```

