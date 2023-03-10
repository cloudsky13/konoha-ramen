# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with "admin" user and below token (as in documentation):
argocd admin initial-password -n argocd
(make sure to update new password in the User Info option.)

#Ingress setup on minikube

To manage ingress controllers kubernetes provides nginx ingress. It's support is extended to minikube as well as addons.
With a simple command all dependencies will be made available and ingress will be enabled.

Command:  minikube addons enable ingress

Output reference:

<img width="822" alt="image" src="https://user-images.githubusercontent.com/60884268/224271075-80461663-260a-4723-aff3-a9bee83c5f0e.png">

Once ingress addon is enable a new namespace "ingress-nginx" is created in minikube. You can verify the status of all resources created in ingress-nginx namespace using below command:

Command: kubectl get all -n ingress-nginx

Output reference:

<img width="892" alt="image" src="https://user-images.githubusercontent.com/60884268/224272830-90d5e9df-d3d5-4c34-8abd-9b44cc1f017c.png">

