# Base image para Node.js (versão 18)
FROM node:18 AS build

# Diretório de trabalho
WORKDIR /app

# Copiar arquivos de dependências
COPY package.json package-lock.json ./

# Instalar as dependências
RUN npm install

# Copiar todo o código da aplicação para o container
COPY . .

# Build da aplicação Angular
RUN npm run build --prod

# Servir o conteúdo estático com Nginx
FROM nginx:alpine

# Copiar os arquivos gerados pela build para o diretório de arquivos estáticos do Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expor a porta 80 para que o Nginx possa servir a aplicação
EXPOSE 80

# Comando para rodar o Nginx em modo foreground
CMD ["nginx", "-g", "daemon off;"]
