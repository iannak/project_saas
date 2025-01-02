# Base image para Node.js (versão 18)
FROM node:18

# Diretório de trabalho
WORKDIR /app

# Copiar arquivos de dependências
COPY package.json package-lock.json ./

# Instalar dependências
RUN npm install

# Copiar todo o código da aplicação para o container
COPY . .

# Build da aplicação (sem o flag --prod)
RUN npm run build

# Expor a porta 3000 usada pelo NestJS
EXPOSE 3000

# Comando para rodar o servidor em modo de desenvolvimento
CMD ["npm", "run", "start"]
