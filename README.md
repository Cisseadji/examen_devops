
# Projet DevOps - Serveur HTTP Minimaliste avec Docker

## Description du projet

Ce projet consiste à créer un serveur HTTP minimaliste en Python et à le conteneuriser avec Docker. L’objectif est d’apprendre les bases de Docker, Docker Compose et l’automatisation CI/CD avec GitHub Actions.

Le serveur HTTP sert une page web simple accessible sur le port 8000.

---

## Structure du projet
basic-docker-project/
├── app/
│ └── server.py
├── Dockerfile
├── docker-compose.yml
├── README.md
└── .github/workflows/ # Pour la partie CI/CD


---

## Installation et exécution

### 1. Exécuter sans Docker

1. **Installer Python** : Assurez-vous d'avoir Python installé sur votre machine.
2. **Exécuter le serveur** :
bash
 python app/server.py
Accéder au serveur :
Ouvrez votre navigateur et allez à l'adresse : http://localhost:8000.

### 2. Exécuter avec Docker
Construire et exécuter l’image Docker
Construire l'image Docker :

```bash
  docker build -t my-http-server .
### Exécuter le conteneur :

bash
docker run -p 8000:8000 my-http-server
### Accéder au serveur :
 ### Ouvrez votre navigateur et allez à l'adresse : http://localhost:8000.

### Exécuter avec Docker Compose
### Exécuter le projet avec Docker Compose :

bash
docker-compose up --build
Accéder au serveur :
Ouvrez votre navigateur et allez à l'adresse : http://localhost:8000.

Pousser l’image sur DockerHub
1. Se connecter à DockerHub
Se connecter à DockerHub :

bash
docker login

2. Construire et taguer l’image
Construire l'image Docker :

bash
docker build -t adjicisse/image-http-server:latest .
Taguer l'image :

bash
Copy
docker tag adjicisse/image-http-server:latest adjicisse/image-http-server:latest
3. Pousser l’image sur DockerHub
Pousser l'image sur DockerHub :

bash
docker push adjicisse/image-http-server:latest
Vérifier sur DockerHub :
Allez sur votre compte DockerHub pour vérifier que l'image a bien été poussée.

CI/CD - Automatisation avec GitHub Actions
Un pipeline CI/CD est mis en place pour automatiser la construction et le push de l’image Docker sur DockerHub à chaque modification du code sur la branche main.

Fonctionnement du pipeline
À chaque push sur main, GitHub Actions déclenche un workflow (.github/workflows/docker-publish.yml).

Ce workflow :

Clone le code.

Se connecte à DockerHub.

Construit l'image Docker.

Pousse l'image sur DockerHub.

Secrets GitHub à configurer
Pour que l’authentification Docker fonctionne, ajoutez ces secrets dans GitHub > Settings > Secrets :

DOCKER_USERNAME → Votre nom d'utilisateur DockerHub.

DOCKER_PASSWORD → Votre mot de passe DockerHub.

Déploiement et Test
Récupérer et exécuter l’image depuis DockerHub
Récupérer l'image depuis DockerHub :

bash
docker pull adjicisse/image-http-server:latest
Exécuter l'image :

bash
docker run -p 8000:8000 adjicisse/image-http-server:latest
Accéder au serveur :
Ouvrez votre navigateur et allez à l'adresse : http://localhost:8000.