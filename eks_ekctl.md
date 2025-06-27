'''bash

eksctl create cluster \
  --name my-cluster \
  --region us-west-2 \
  --nodes 2 \
  --node-type t3.medium \
  --managed \
  --with-oidc \
  --ssh-access \
  --ssh-public-key my-keypair \
  --node-private-networking=false

  '''
