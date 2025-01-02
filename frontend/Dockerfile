# Base image para Node.js (versão 18)
FROM node:18 AS build

# Diretório de trabalho
WORKDIR /app

# Copiar arquivos de dependências
COPY package.json package-lock.json ./

# Instalar as dependências
RUN npm install

# Copiar o restante do código
COPY . .

# Build da aplicação Angular
RUN npm run build --prod

# Servir a aplicação com Nginx
FROM nginx:alpine

# Copiar os arquivos de build para o diretório do Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expor a porta 80
EXPOSE 80

# Comando para rodar o Nginx
CMD ["nginx", "-g", "daemon off;"]
