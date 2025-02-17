# Deployment Configuration

This repo contains the helm charts to deploy the application containers into the AWS EKS cluster.

  helm upgrade --install aws-load-balancer-controller eks/aws-load-balancer-controller \
  --namespace kube-system \
  --set clusterName=dst-dev-eks-cluster \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller \
  --set aws-region=eu-central-1
  
  When installing or upgrading your Helm release, you can override these values on the command line if needed:

helm upgrade --install dst-prod . \
  --set awsAccountId=123456789012 \
  --set environment=prod
