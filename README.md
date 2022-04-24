# HelloWorld Node

## Node Application Structure 
```
.
|──────app/
| |────Dockerfile
| |────package.json
| |────server.js
| |────readme.md

```

## Node Application Lancement

```
npm start
```

## Docker 

### Lancement 

1. Installer Docker
2. Lancer un cmd.
3. Build l'image Docker : `docker build -t hello-world .`
4. Lancer une image dans un container : `docker run -d -p 4001:4000 hello-world`
  - l'argument `-d` est pour lancer le container en arriere plan (daemon mode).
  - l'argument `-p` permet de publier le container sur le port specifier.

### Dockerfile

1. Pour build une image Docker il est possible d'utiliser un dockerfile et un contexte.
2. Le dockerfile a pour but de lister les configurations de notre future image.  


```
Fonctionnalités ligne par ligne 
```

### Envoi du conaineur vers Docker Hub

1. Création du refrentiel node-starter : `docker tag node-server mdubuche28/nodejs-starter`
  - l'argument `tag` est pour donnée une étiquette au referentiel ?

2. Poussez le refrentiel ver DockerHub: `docker push mdubuche28/nodejs-starter`

## Kubernetes

### Lancement du cluster MiniKube
1. Installer Minikube et le lancer avec un gestionnaire de VM (VBox, Docker, Hyper V)
2. Lancer minikube: `minikube start` 
3. verfier lancement: `minikube status`

### Création du fichier deploy.yaml

Le fichier deploy.yaml contient toutes les informations necessaires aux deploiments 
Explication de ca conception : 

```
Fonctionnalités ligne par ligne 
```

### Créer et exposez un deploymlent 

1. Créer un deployments dans le cluster `kubectl create -f deploy.yaml`
  - l'argument `-f` permet de spécifier le fichier de conf a utilisé 
2. Permet de verfier que le deploiment a bien été créé: `kubectl get deployments`
3. Permet de verfier que les pods a bien été créé: `kubectl get pods`
4. Exposer le deployment: `kubectl expose deployment nodejs-deployment --type="LoadBalancer"`
5. Permet de verfier que le service a bien été créé: `kubectl get svc`
