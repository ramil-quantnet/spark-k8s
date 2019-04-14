# Install VirtualBox

https://virtualbox.org


# Install scoop for Windows in Power Shell

```sh
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

And then install

```sh
scoop install vim
scoop install docker docker-compose docker-machine
scoop install minikube
scoop install kubectl
```


# Spark

Run on Spark to check that it works

```scala
val myWords = "HI HI HOW ARE YOU HAH"
val mySplit = myWords.split(" ").foldLeft(Map.empty[String, Int]) {
    (count, word) => count + (word -> (count.getOrElse(word, 0) + 1))
}
```


# Deploying Spark on Kubernetes

Start the cluster:

```sh
$ minikube start --memory 8192 --cpus 4
$ minikube dashboard
```

Build the Docker image:

```sh
$ minikube docker-env
$ docker build -H tcp://192.168.99.101:2376 --tlsverify --tlscacert=C:\Users\username\.d
ocker\machine\machines\default\ca.pem --tlscert=C:\Users\username\.docker\machine\machines\default\cert.pem --tlskey=C:\
Users\username\.docker\machine\machines\default\key.pem -t spark-hadoop:2.2.1 -f ./docker/Dockerfile ./docker
```

Create the deployments and services:

```sh
$ kubectl create -f ./kubernetes/spark-master-deployment.yaml
$ kubectl create -f ./kubernetes/spark-master-service.yaml
$ kubectl create -f ./kubernetes/spark-worker-deployment.yaml
$ minikube addons enable ingress
$ kubectl apply -f ./kubernetes/minikube-ingress.yaml
```

Add an entry to hosts:

```sh
$ minikube ip
```

