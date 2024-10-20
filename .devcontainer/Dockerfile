# Usar la imagen con dependencias preinstaladas
FROM ghcr.io/chatwoot/chatwoot_codespace:latest

# Establecer el directorio de trabajo
WORKDIR /workspace

# Copiar todos los archivos de la aplicación al contenedor
COPY . /workspace

# Añadir la variable de entorno para desactivar la precompilación de activos
ENV SKIP_ASSET_COMPILE=true

# Instalar las dependencias con yarn y bundler
RUN yarn && gem install bundler && bundle install
