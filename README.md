@@@ This configuration files helps you to configure different ssl certificates for different services(different domain names) in any ingress controller @@@

Ingress
https://cloud.google.com/kubernetes-engine/docs/how-to/ingress-multi-ssl

Creating ssl certificates for domain kube1.minikube.com
openssl genrsa -out test-ingress-1.key 2048
openssl req -new -key test-ingress-1.key -out test-ingress-1.csr -subj "/CN=kube1.minikube.com"
openssl x509 -req -days 365 -in test-ingress-1.csr -signkey test-ingress-1.key -out test-ingress-1.crt

Creating ssl certificates for domain kube2.minikube.com
openssl genrsa -out test-ingress-2.key 2048
openssl req -new -key test-ingress-2.key -out test-ingress-2.csr -subj "/CN=kube2.minikube.com"
openssl x509 -req -days 365 -in test-ingress-2.csr -signkey test-ingress-2.key -out test-ingress-2.crt

Create secrets with ssl keys
kubectl create secret tls my-first-secret --cert test-ingress-1.crt --key test-ingress-1.key
kubectl create secret tls my-first-secret --cert test-ingress-2.crt --key test-ingress-2.key
