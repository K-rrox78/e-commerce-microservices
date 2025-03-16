# Stage de développement
FROM node:18-slim AS development

WORKDIR /app

# Copie des fichiers de dépendances
COPY package*.json ./

# Installation des dépendances de développement
RUN npm install

# Copie du code source
COPY . .

# Exposition du port de développement
EXPOSE 8080

# Commande par défaut pour le développement
CMD ["npm", "run", "serve"]

# Stage de build
FROM node:18-slim AS build

WORKDIR /app

# Copie des fichiers de dépendances
COPY package*.json ./

# Installation des dépendances
RUN npm ci

# Copie du code source
COPY . .

# Build de l'application
RUN npm run build

# Stage de production
FROM nginx:alpine AS production

# Copie de la configuration Nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copie des fichiers buildés depuis l'étape de build
COPY --from=build /app/dist /usr/share/nginx/html

# Création d'un utilisateur non-root
RUN adduser -D -u 1000 nginx-user && \
    chown -R nginx-user:nginx-user /usr/share/nginx/html && \
    chown -R nginx-user:nginx-user /var/cache/nginx && \
    touch /var/run/nginx.pid && \
    chown -R nginx-user:nginx-user /var/run/nginx.pid

USER nginx-user

# Exposition du port
EXPOSE 80

# Nginx démarre automatiquement
