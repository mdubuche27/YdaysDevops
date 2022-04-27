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
1. Indique a notre containeur que nous utilisons node pour qu'il l'installe
2. copie les fichiers de notre app dans le dossier app 
3. deplacement dans le bon dossier et instlalation des packets
4. Expose le containeur sur le port 4000
5. Ligne de commande qui lance le script avc node
```

### Envoi du conaineur vers Docker Hub

1. Création du refrentiel node-starter : `docker tag <ImageID> mdubuche28/nodejs-starter`
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
1.Décrivez la version de l'API que vous utilisez pour créer cet objet, c'est-à-dire le déploiement - nous utilisons apps/v1
2.Quel type d'objet vous créez. Dans notre cas, c'est Déploiement.
3.Les métadonnées sont utilisées pour organiser l'objet.
  1.Le nom de notre déploiement est nodejs-deployment
4.Spec est utilisé pour définir la spécification de l'objet.
  1.Combien de pods vous souhaitez déployer dans le cluster sous ce déploiement. Dans notre cas, nous voulons déployer deux pods exécutant des conteneurs à partir de notre image.
  2.Identifier les pods vers lesquels acheminer le trafic
    1.indique à quels pods le déploiement s'appliquera.
      1.Nom de notre pod dans notre cas nodejs
  2.Le modèle est utilisé pour définir comment faire tourner le nouveau pod et les spécifications du pod.
    1.Métadonnées du pod nouvellement créé avec ce déploiement
      1.Nous avons une étiquette - la clé est l'application et la valeur est nodejs
  3.Les étiquettes des dosettes fraîchement créées
    1.Spec définit la spécification de la façon dont les conteneurs seront créés
      1.Spécifications des conteneurs
        1.Nom du conteneur
        2.L'image qui peut être utilisée par le conteneur
        3.Quelle option de port utiliser
          1.Nous utilisons containerPort 3000
```

### Créer et exposez un deploymlent 

1. Créer un deployments dans le cluster `kubectl create -f deploy.yaml`
  - l'argument `-f` permet de spécifier le fichier de conf a utilisé 
2. Permet de verfier que le deploiment a bien été créé: `kubectl get deployments`
3. Permet de verfier que les pods a bien été créé: `kubectl get pods`
4. Exposer le deployment: `kubectl expose deployment nodejs-deployment --type="LoadBalancer"`
5. Permet de verfier que le service a bien été créé: `kubectl get svc`
5. Permet d'obtenir les info sur le cluster': `kubectl cluster-info`
