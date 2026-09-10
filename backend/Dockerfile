FROM node:22-alpine

WORKDIR /app

COPY package*.json ./
RUN npm cache clean --force && npm install

# Fix CVE-2026-73566: Update tar to patched version
RUN npm update tar --save

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
