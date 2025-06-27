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
  --kubernetes-groups system:masters
```
