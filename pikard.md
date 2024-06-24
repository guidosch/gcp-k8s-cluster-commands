# Pikard

https://confluence.ergon.ch/display/klondike/Pikard


# Pikard deployment of changed config
```
# find the right component
pikard core-cloud development deploy --list
pikard core-cloud development deploy cbapl/reportservice --config-diff --dry-run
```

# Pikard deployment of container
```
pikard core-cloud development deploy cbapl/reportservice --apply --latest
pikard core-cloud development deploy cbapl/reportservice --version 2023.2

# china
pikard core-cloud china:development deploy cba/cc --version [your-version-file] --apply
```

# Restart or scale POD
```
kubectl rollout restart deploy nginx-cbapl-services

# delete pod (does autostart again)
k delete pod nginx-cbapl-services-xxxx

### Service downscale to zero
kubectl scale deployment/feed-service --replicas=0

#### scale to one
kubectl scale deployment/feed-service --replicas=1
```

### gcloud auth
```
glcloud auth login
glcoud init (create new configuration)
gcloud 
pikard-helpers (list helper scripts to switch project env)
```

# Environment
```
k config current-context
gcloud config configurations list (auflisten der configurationen)
pikard-helpers
gccdev --> GCP Dev. Umgebung
for i in gcc{dev,int,prd,uat}; do kubectl get nodes --context $i; done
```


### PODs (k iis alias for kubectrl)
```
k get pods
k get nodes
k describe pod [pod_name]
k describe node [node_name]
k logs -f [pod]
```

### Nodes
```
k get nodes
k describe node [node_name]
```

## Logs
```
k logs -f [pod]

# from sidecare container
k logs -f [pod] -c telegraf
```

### logs from sidecar container "-c"
```
k config current-context
config get-contexts gccdev
```

# Copy files from POD
```
kubectl cp example-pod:/tmp/example-dir ./example-dir
k cp sourceFile [podname]:/tmp
```

#influx
```
select * from "c7427325-cc27-4691-9f30-efe5885d1687" order by time desc limit 10;
```

```



### gsutil
gsutil ls [bucket url]


### topic und andere dinge wieder erstellen/sync auf dem cluster
pikard core-cloud development manage-databases --dry-run
