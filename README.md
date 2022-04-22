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

- Pour build une image Docker il est possible d'utiliser un dockerfile et un contexte.
- Le dockerfile a pour but de lister les configurations de notre future image.  
- Dans notre cas il permet de créer le container en Node 4.2. Le container créer est ensuite exposer sur le port 4000 et le service est lancé.


## Kubernetes


