```
eksctl create cluster \
  --name sdm-enable-26june2025 \
  --region us-west-2 \
  --nodes 2 \
  --node-type t3.medium \
  --managed \
  --with-oidc \
  --ssh-access \
  --ssh-public-key sdmenable_pair_19une2025 \
  --node-private-networking=false
```

```
aws eks create-access-entry \
  --cluster-name sdm-enable-26june2025 \
  --principal-arn arn:aws:iam::478603337655:role/sdmenable_instance_profile_19june2025 \
  --type STANDARD \
  --kubernetes-groups sdmenable-sa-grp
```

```
kubectl auth can-i list pods --as=sdm-health
```

```
kubectl auth can-i list namespaces --as=discovery
```

```
kubectl auth can-i impersonate users --as=sdmenable-sa
```

```
kubectl auth can-i impersonate users --as=sdmenable-sa --as-group=sdmenable-sa-grp
```

Ngnix

```
kubectl create namespace ngx
```

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  namespace: site
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

```
kubectl apply -f nginx-deployment.yaml
```

```
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  namespace: site
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer
```

```
kubectl apply -f nginx-service.yaml
```

