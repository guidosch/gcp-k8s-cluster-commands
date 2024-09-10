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

### Port Forwarding
```
kubectl port-forward feed-service-7cc46b75b-fxtwd 1234:1234 1235:1235
```
...or via kubefwd based on a list of service names
```
sudo -E kubefwd svc -l 'app.kubernetes.io/name in (kafka,schema-registry,user-management-postgresql)'
```
### Patch POD
... install new version of image (alternative approach to pikard)
```
kubectl patch pod cloudserver-6f874c79c9-bm8vn -p '{"spec":{"containers":[{"name": "cloudserver","image":"europe-west1-docker.pkg.dev/belimo-artifacts/belimo-cloud/belcloud-cloudserver:11466-3369.f74c07330b1"}]}}'
```

