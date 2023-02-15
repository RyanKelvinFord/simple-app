1.) Clone the source code repository for a simple application using the Git version control system.
    git clone https://github.com/RyanKelvinFord/simple-app

2.) Start a local Kubernetes cluster using the Minikube tool.
    minikube start

3.) Check the status of the Minikube cluster to verify that it is running.
    minikube status
    
4.) Create a new namespace called "argocd" in the Kubernetes cluster.
    kubectl create namespace argocd
    
5.) Deploy Argo CD, a continuous delivery tool for Kubernetes, to the "argocd" namespace using a YAML manifest file hosted on GitHub.
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    
6.) Forward the local port 8080 to the HTTPS port 443 of the Argo CD server running in the Kubernetes cluster.
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    
7.) Retrieve the initial password for the Argo CD server from a Kubernetes secret and decode it using base64.
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
    
8.) Apply the Kubernetes manifests in the "manifest/" directory, which includes resources for a Kubernetes deployment, service, and ingress for a React application.
    kubectl apply -k manifest/

9.) List the namespaces in the Kubernetes cluster to verify that the "react" namespace was created.
    kubectl get namespaces
    
10.) List the Kubernetes services in the "react" namespace to verify that the React application service was created.
    kubectl get svc -n react
    
11.) Start a local proxy to the Kubernetes service for the React application and open the application in a web browser.
    minikube service react -n react
    
Overall, these steps are demonstrating how to set up a local development environment for deploying and testing Kubernetes applications using Minikube and Argo CD.
