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