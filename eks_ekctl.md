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
  --cluster-name my-cluster \
  --principal-arn arn:aws:iam::123456789012:role/MyRole \
  --type STANDARD \
  --kubernetes-groups system:masters
```
