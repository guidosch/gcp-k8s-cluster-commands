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

### Networking
Show address of the ingress load balancer
```
SERVICE_IP=$(kubectl get ingress superset-1-superset-ingress \
  --namespace default \
  --output jsonpath='{.status.loadBalancer.ingress[0].ip}')

echo "https://${SERVICE_IP}/"
```

