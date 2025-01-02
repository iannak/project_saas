# Usar uma imagem base do Alpine
FROM alpine:3.12

# Instalar Node.js e npm
RUN apk add --no-cache nodejs npm

# Definir o diretório de trabalho
WORKDIR /app

# Copiar arquivos de dependências
COPY package.json package-lock.json ./

# Instalar as dependências
RUN npm install

# Copiar o restante do código
COPY . .

# Rodar o build da aplicação
RUN npm run build

# Expor a porta para a aplicação
EXPOSE 3000

# Comando para iniciar o servidor
CMD ["npm", "run", "start"]
