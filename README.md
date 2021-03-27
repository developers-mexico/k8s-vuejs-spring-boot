minikube start

minikube addons enable ingress

kubectl get pods -n kube-system

openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tls_self.key -out tls_self.crt -subj "/CN=*.todo.dev" -days 36

kubectl create secret tls tls-certificate --key tls_self.key --cert tls_self.crt -n kube-system

minikube stop

minikube delete