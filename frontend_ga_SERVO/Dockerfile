FROM node

ARG VITE_API_URL
ARG GITHUB_USER
ARG GITHUB_PASSWORD
ARG FRONTEND_GITHUB_URL

WORKDIR /frontend

# Instalar Git
RUN apt-get update && \
    apt-get install -y git

# Clonar el repositorio utilizando las credenciales de Github en el archivo .netrc
RUN echo "machine github.com login $GITHUB_USER password $GITHUB_PASSWORD" >> ~/.netrc && \
    git clone $FRONTEND_GITHUB_URL .

# Instalar dependencias
RUN npm install

# Definir variables de entorno
ENV VITE_API_URL $VITE_API_URL

EXPOSE 5173

# Instalar serve
RUN npm install --g http-server

# Generar archivos estáticos
RUN npm run build

# Comando por defecto
CMD ["npx", "http-server", "-p", "5173", "dist"]


