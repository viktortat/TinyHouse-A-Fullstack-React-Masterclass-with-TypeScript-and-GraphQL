# [NewLine] TinyHouse: A Fullstack React Masterclass with TypeScript and GraphQL [ENG, 2020]

<br/>

**Final Project**:  
https://www.tinyhouse.app/

<br/>

<br/>

## How to run apps

I am working in ubuntu linux 18.04.

Docker, Minikube, Kubectl, Skaffold should be installed.

<br/>

### Docker

```
$ docker -v
Docker version 19.03.12
```

<br/>

### Minikube installation

```
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

```

<br/>

```
$ minikube version
minikube version: v1.12.1
```

<br/>

### Kubectl installation

```
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/

$ kubectl version --client --short
Client Version: v1.18.6

```

<br/>

### Skaffold installation

```
$ curl -Lo skaffold https://storage.googleapis.com/skaffold/releases/latest/skaffold-linux-amd64

$ chmod +x skaffold
$ sudo mv skaffold /usr/local/bin

$ skaffold version
v1.12.1
```

<br/>

### Run minikube

```
$ {
    minikube --profile my-profile config set memory 8192
    minikube --profile my-profile config set cpus 4

    // minikube --profile my-profile config set vm-driver virtualbox
    minikube --profile my-profile config set vm-driver docker

    minikube --profile my-profile config set kubernetes-version v1.18.6
    minikube start --profile my-profile
}
```

<br/>

    // Enable ingress
    $ minikube addons --profile my-profile enable ingress

<br/>

    $ minikube --profile my-profile ip
    172.17.0.3

<br/>

    $ sudo vi /etc/hosts

```
#---------------------------------------------------------------------
# Minikube
#---------------------------------------------------------------------
172.17.0.3 tinyhouse.dev
```

<br/>

## How to run the app

<br/>

commit: 3934dd627e244a12907ea7c4595cb52474a47e18

<br/>

    $ cd skaffold

    $ docker login

Need to update my docker image name webmakaka/tinyhouse\*\*\* to your in scripts from skaffold and k8s folders.

    $ skaffold dev

<br/>

    $ kubectl get pods
    NAME                                           READY   STATUS    RESTARTS   AGE
    tinyhouse-client-deployment-d65d5b866-km548    1/1     Running   0          92s
    tinyhouse-mongo-deployment-755b899c89-qd44c    1/1     Running   0          92s
    tinyhouse-server-deployment-5744884c7c-lf8kp   1/1     Running   0          92s

<br/>

    $ kubectl exec -it tinyhouse-server-deployment-5744884c7c-lf8kp sh

<br/>

    # cd /app/
    # npm run seed

<br/>

**chrome browser**

```
client --> https://tinyhouse.dev/
graphql - https://tinyhouse.dev/api/
```

<br/>

type: **thisisunsafe** in the browser window with security warning.

<!--

# apk add mongodb

-->

<br/>

Expected result:

![Application](/img/pic-started-01.png?raw=true)

<br/>

### Delete minikube with project

    $ minikube --profile my-profile stop && minikube --profile my-profile delete

<hr/>

<br/>

### [Development step by step](./Development.md)

<br/>

---

<br/>

**Marley**

Any questions on eng: https://jsdev.org/chat/  
Любые вопросы на русском: https://jsdev.ru/chat/
