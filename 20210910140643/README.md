# Getting started with minikube

Minikube is a container management and orchestration tool. Useful for
learning kubernetes and containers. I thought it would be worthwhile to
install minikube on my computer. Installation is simple with 
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
Getting it up and running. Once running we can start minikube with 
```
minikube start
```

Many things work better if we have kubectl installed. To do this we curl
the latest version and install
```
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

To interact with the cluster we can run 
```
kubectl get po -A
#or
minikube dashboard
```

To deploy a container we use `kubectl`

```
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
kubectl expose deployment hello-minikube --type=NodePort --port=8080
``` 
The expose command will expose the port to port 8080 in this case. The
image can come from any location. To access the above container we can
use
```
kubectl port-forward service/hello-minikube 7080:8080
```

There are many more things we can do with minikube. Below are a couple
from the quickstart
```
minikube pause
minikube unpause
minikube delete
```

I plan on trying many things with this tool including:

Running pihole, duckdns, vpn etc. 
Installing on rpi cluster

