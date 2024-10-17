# Usa una imagen base de Ruby
FROM ruby:3.0

# Instala dependencias del sistema
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client

# Instala Yarn (gestor de paquetes)
RUN npm install -g yarn

# Configura la carpeta de trabajo
WORKDIR /app

# Copia el Gemfile y Gemfile.lock al contenedor
COPY Gemfile Gemfile.lock ./

# Instala las dependencias de Ruby (bundler)
RUN bundle install

# Copia el código de la aplicación al contenedor
COPY . .

# Precompila los assets solo si es el servicio "web"
ARG ROLE
RUN if [ "$ROLE" = "web" ]; then bundle exec rake assets:precompile; fi

# Define el comando para arrancar el contenedor
CMD if [ "$ROLE" = "web" ]; then bundle exec puma -C config/puma.rb; else bundle exec sidekiq; fi
