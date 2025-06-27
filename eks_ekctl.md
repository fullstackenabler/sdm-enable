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
