minikube start

minikube status

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl port-forward svc/argocd-server -n argocd 8080:443

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

ADD APPLICATION

kubectl get svc -n argocd

kubectl port-forward -n argocd svc/argocd-server 8080:443

kubectl get namespaces

kubectl get svc -n react


You can use the command minikube service react -n react to expose the external IP and access the application. This command will open the application in a web browser using the IP address of the Minikube virtual machine.
Alternatively, you can also use minikube service react -n react --url it will give you the exposed URL of the service, you can use that URL to access the application from browser.
You can also use minikube ip to get the IP of the minikube cluster, then you can use that IP along with the exposed port to access the application via browser
Eg: http://minikube-ip:32181


    minikube start: This command starts a local Kubernetes cluster using Minikube. Minikube is a tool that allows you to run Kubernetes on your local machine, and minikube start initializes a new cluster.

    minikube status: This command checks the status of the Minikube cluster and reports whether it is running or stopped.

    kubectl create namespace argocd: This command creates a new namespace called argocd in the Kubernetes cluster. A namespace is a way to partition resources in a Kubernetes cluster so that different teams or applications can have their own isolated environment.

    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml: This command applies the Kubernetes manifest file located at the specified URL (https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml) to the argocd namespace. The manifest file contains the configuration needed to deploy ArgoCD, a continuous delivery tool.

    kubectl port-forward svc/argocd-server -n argocd 8080:443: This command forwards traffic from the local machine's port 8080 to the argocd-server service running in the argocd namespace on port 443. This allows you to access the ArgoCD web UI from your local machine.

    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo: This command retrieves the argocd-initial-admin-secret Kubernetes secret from the argocd namespace and decodes the password field, which contains the initial password for the ArgoCD admin user. The base64 -d command is used to decode the password, and echo is used to print it to the console.


    kubectl get svc -n argocd: This command lists all the Kubernetes services in the argocd namespace. A service in Kubernetes is an abstraction that defines a logical set of pods and a policy by which to access them.

    kubectl port-forward -n argocd svc/argocd-server 8080:443: This command sets up a port-forwarding connection between the local machine's port 8080 and the argocd-server service's port 443, allowing you to access the ArgoCD web UI on your local machine.

    kubectl get namespaces: This command lists all the namespaces in the Kubernetes cluster.

    kubectl get svc -n react: This command lists all the Kubernetes services in the react namespace. The react namespace may or may not exist in your Kubernetes cluster, and if it does, it would contain services related to applications that are built using the React framework.
