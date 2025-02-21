# Deployment Configuration

This repo contains the helm charts to deploy the application containers into the AWS EKS cluster.

  helm upgrade --install aws-load-balancer-controller eks/aws-load-balancer-controller \
  --namespace kube-system \
  --set clusterName=dst-dev-cluster \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller \
  --set aws-region=us-east-1
  
  When installing or upgrading your Helm release, you can override these values on the command line if needed:

helm upgrade --install dst-prod . \
  --set awsAccountId=123456789012 \
  --set environment=prod

aws eks update-kubeconfig --region eu-central-1 --name dst-dev-cluster

kubectl get serviceaccount aws-load-balancer-controller -n kube-system

helm upgrade --install aws-load-balancer-controller eks/aws-load-balancer-controller \
  --namespace kube-system \
  --set clusterName=dst-dev-cluster \
  --set serviceAccount.create=true \
  --set serviceAccount.name=aws-load-balancer-controller \
  --set serviceAccount.annotations."eks.amazonaws.com/role-arn"=arn:aws:iam::<your-account-id>:role/<your-role-name> \
  --set serviceAccount.annotations."eks.amazonaws.com/sts-regional-endpoints"="true" \
  --set aws-region=us-east-1

  aws iam upload-server-certificate --server-certificate-name zerossl_dst_dev_pradikow_com \
> --certificate-body file://certificate.crt --private-key file://private.key --certificate-chain file://ca_bundle.crt
SERVERCERTIFICATEMETADATA       arn:aws:iam::170526064978:server-certificate/zerossl_dst_dev_pradikow_com 

dev-dst-translator-dst-translator-ingress