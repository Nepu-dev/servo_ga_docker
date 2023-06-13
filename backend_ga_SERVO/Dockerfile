FROM node

ARG MONGO_URI
ARG JWT_SECRET
ARG PORT
ARG GITHUB_USER
ARG GITHUB_PASSWORD
ARG FRONTEND_URL

WORKDIR /backend

# Instalar Git
RUN apt-get update && \
    apt-get install -y git

# Clonar el repositorio utilizando las credenciales de Github en el archivo .netrc
RUN echo "machine github.com login $GITHUB_USER password $GITHUB_PASSWORD" >> ~/.netrc && \
    git clone https://github.com/Nepu-dev/backend_ga_SERVO.git .

# Instalar dependencias
RUN npm install

# Definir variables de entorno
ENV MONGO_URI $MONGO_URI
ENV PORT $PORT
ENV JWT_SECRET $JWT_SECRET
ENV FRONTEND_URL $FRONTEND_URL
ENV BACKEND_URL http://localhost:4000

# Exponer puerto
EXPOSE $PORT

# Comando por defecto
CMD [ "npm", "start" ]