# Etapa 1: Build de la app
FROM node:20-alpine AS builder

WORKDIR /app

COPY package.json ./
COPY vite.config.js ./
COPY index.html ./
COPY public ./public
COPY src ./src

RUN npm install && npm run build

# Etapa 2: Servidor de producción
FROM nginx:stable-alpine

# Copiar archivos compilados al directorio de Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Exponer puerto
EXPOSE 80

# Iniciar Nginx
CMD ["nginx", "-g", "daemon off;"]
