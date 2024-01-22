# 🚀 Rapport ACE

Auteurs: Naja Mohamed et Mouhoubi Meryem
Date: 20/01/2024

---

## ACE
Pr. LACHGAR

## Aperçu
Notre projet repose sur une application de blog développée en utilisant l'architecture microservices. Cette approche permet une conception modulaire et évolutive, favorisant la flexibilité et la maintenabilité de l'application.

### Importance de l'architecture microservices
L'architecture microservices offre plusieurs avantages, tels que la scalabilité indépendante, la facilité de déploiement, et la réduction des dépendances entre les composants. Elle permet également une gestion plus efficace des équipes de développement et une meilleure résilience.

#### Scalabilité Indépendante
- L'architecture microservices permet d'évoluer indépendamment chaque composant du système.
- Chaque microservice peut être déployé, mis à l'échelle et mis à jour de manière autonome.
- Permet d'ajuster la capacité des parties spécifiques de l'application sans affecter les autres.
- Offre une flexibilité considérable pour répondre aux fluctuations de la demande.

#### Facilité de Déploiement
- Favorise un déploiement continu et une livraison fréquente.
- Les microservices peuvent être déployés séparément, accélérant le cycle de développement.
- Permet de publier des fonctionnalités, des correctifs ou des améliorations sans perturber l'intégrité du système.
- Réduit les risques associés aux mises à jour, assurant une mise en production plus rapide et plus fiable.

#### Réduction des Dépendances
- Minimise les dépendances entre les services, contrairement aux architectures monolithiques.
- Chaque microservice communique généralement via des API bien définies.
- Permet aux équipes de développement de travailler de manière plus autonome.
- Facilite l'évolution et la maintenance, car les changements dans un microservice n'affectent pas nécessairement les autres.

#### Gestion Efficace des Équipes de Développement
- Les équipes peuvent être organisées pour être responsables de microservices spécifiques.
- Favorise la spécialisation et permet aux équipes de se concentrer sur des domaines spécifiques de l'application.
- Chaque équipe peut opérer de manière autonome, accélérant le développement et améliorant la productivité.
- La communication entre les équipes se fait généralement par des interfaces clairement définies, minimisant les conflits.

#### Meilleure Résilience
- En cas d'échec d'un microservice, l'ensemble de l'application peut continuer de fonctionner.
- Cette architecture distribuée contribue à une meilleure résilience du système.
- La détection des pannes et la gestion de la charge peuvent être optimisées pour chaque microservice individuellement.
- Garantit une disponibilité plus élevée de l'application dans son ensemble.


## Architecture

### Description des Services
- **mysql**: Service de base de données MySQL pour stocker les données de l'application.
- **app**: Service principal de l'application, gérant la logique métier.
- **app-ui**: Interface utilisateur de l'application, développée en Angular.
- **consul**: Service de découverte de services pour la gestion des microservices.
- **analyticsMicroservice**: Microservice dédié à l'analyse des données.
- **api_gateway**: Point d'entrée central pour l'accès aux microservices.
- **kafka**: Service de messagerie pour la communication asynchrone entre les microservices.
- **zookeeper**: Service de coordination pour Kafka.

- Screen Consul
![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/d0786f62-419a-4564-b400-0631cfd51369)


### Architecture des Microservices
![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/5e6998ab-31a4-44da-8b61-31c12c9ce3ae)


### Conception des Microservices

Conception du Blog Service Backend

Le service backend du blog est conçu comme une entité indépendante, responsable de la gestion de la logique métier liée aux publications, commentaires, et autres fonctionnalités du blog.
Il fonctionne de manière autonome, permettant des évolutions spécifiques sans impact sur d'autres parties de l'application.
Interface Distincte et Clair pour le Blog Service Backend

Le blog service expose une interface claire, définissant les points d'entrée pour la création, la modification, et la récupération des publications et des commentaires.
Cette interface bien définie simplifie l'intégration avec d'autres services et garantit une communication efficace au sein de l'architecture microservices.
Fonctionnalités Spécifiques au Blog Service Backend

Le blog service se spécialise dans la gestion des publications et des interactions associées.
Il encapsule la logique métier liée aux opérations de blog, permettant une organisation du code claire et une maintenance facile des fonctionnalités spécifiques au blog.
Communication avec d'Autres Services via API REST et Kafka

Le blog service communique avec d'autres services, tels que le service d'analyse, à l'aide d'API REST et de messages Kafka.
Les API REST permettent des interactions directes, tandis que Kafka facilite la communication asynchrone pour des scénarios où des événements importants doivent être propagés de manière déconnectée.
Exemple : Publication d’un Commentaire

La publication d'un commentaire déclenche un événement Kafka.
Le microservice du service de blog publie l'événement dans une file d'attente appelée commentEventTopic où les microservices Analytics sont abonnés.
Lors de l'ajout d'un commentaire à un article, un nouvel événement Kafka est immédiatement ajouté au sujet.

![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/f4fac001-e866-4bf2-98e2-d3acb797bc64)

### Capture d’écran de Console de Kafka
![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/d39545fa-f3f7-49ed-a969-a8bd5b2e9ea4)

### Demo Kafka


https://github.com/Mednj/blog_micro_latest/assets/69809265/03d03570-8077-4c95-9040-e13763e7f260


## Conteneurisation avec Docker
![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/fe86dcf7-194c-4c71-9879-7baae0ad909e)
## Capture d’écran terminal docker ps :
![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/382adff9-550d-4aca-93e9-70fc7be695ba)

### CI/CD avec Jenkins
![image](https://github.com/Mednj/blog_micro_latest/assets/69809265/799caf04-76f9-48e5-b4d2-8500f52c31bc)

Video Demo:
https://github.com/Mednj/blog_micro_latest/assets/69809265/911b267e-982e-4840-b930-e3dc620054ed


[Images]

```yaml
docker-compose.yml
