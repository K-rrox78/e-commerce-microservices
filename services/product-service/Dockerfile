# Stage de développement
FROM node:18-slim AS development

WORKDIR /usr/src/app

# Copie des fichiers de dépendances
COPY package*.json ./

# Installation des dépendances de développement
RUN npm install

# Copie du code source
COPY . .

# Exposition du port
EXPOSE 3000

# Commande par défaut pour le développement
CMD ["npm", "run", "dev"]

# Stage de production
FROM node:18-slim AS production

WORKDIR /usr/src/app

# Création d'un utilisateur non-root
RUN groupadd -r nodejs && useradd -r -g nodejs nodejs

# Copie des fichiers de dépendances
COPY package*.json ./

# Installation des dépendances de production uniquement
RUN npm ci --only=production

# Copie du code source
COPY . .

# Changement des permissions
RUN chown -R nodejs:nodejs /usr/src/app

# Utilisation de l'utilisateur non-root
USER nodejs

# Exposition du port
EXPOSE 3000

# Commande par défaut pour la production
CMD ["npm", "start"]
