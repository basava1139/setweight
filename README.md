Argocd 

Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

# Install Argo CD
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Install Argo CD CLI on macOS
brew install argocd

# Change the service type of argocd-server to LoadBalancer
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

# Get the ArgoCD UI address
ARGOCD_ADDR=$(kubectl get svc argocd-server -n argocd -o jsonpath='{.status.loadBalancer.ingress[0].hostname}')

# Login using Argo CD CLI, see https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli to get password
argocd login $ARGOCD_ADDR --skip-test-tls --grpc-web --insecure

# Install Argo Rollouts
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/download/latest/install.yaml

# Install rollouts plugin on macOS
curl -LO https://github.com/argoproj/argo-rollouts/releases/download/v1.5.0/kubectl-argo-rollouts-darwin-amd64
chmod +x ./kubectl-argo-rollouts-darwin-amd64
sudo mv ./kubectl-argo-rollouts-darwin-amd64 /usr/local/bin/kubectl-argo-rollouts






