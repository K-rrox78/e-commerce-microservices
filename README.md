# Application E-Commerce Microservices

Ce projet est une application e-commerce basée sur une architecture microservices, conteneurisée avec Docker.

## Structure du Projet

```
ecommerce-microservices/
├── frontend/               # Application Vue.js
├── services/
│   ├── product-service/   # Service de gestion des produits (Node.js + MongoDB)
│   ├── user-service/      # Service d'authentification (Node.js + JWT)
│   └── cart-service/      # Service de gestion du panier et des commandes (Node.js)
├── docker-compose.yml     # Configuration de développement
├── docker-compose.prod.yml # Configuration de production
└── README.md
```

## Prérequis

- Docker
- Docker Compose
- Git

## Services

### Frontend (Vue.js)
Interface utilisateur de l'application e-commerce.

### Service Produits
Gestion du catalogue de produits avec MongoDB.

### Service Utilisateurs
Gestion des utilisateurs et authentification avec JWT.

### Service Panier
Gestion du panier d'achat et des commandes.

## Configuration

### Développement
```bash
docker-compose up
```

### Production
```bash
docker-compose -f docker-compose.prod.yml up
```

## Sécurité
- Images optimisées avec multi-stage builds
- Exécution des conteneurs en non-root
- Gestion sécurisée des secrets
- Registry privée pour les images

## Monitoring
- Logs centralisés
- Métriques avec Prometheus/Grafana (en option)

## CI/CD
Pipeline de build automatisé pour les images Docker.

## Contributeurs
[Votre équipe]
