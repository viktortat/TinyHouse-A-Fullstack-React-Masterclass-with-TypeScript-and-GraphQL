FROM node:12.16.3-alpine3.9

WORKDIR /app
COPY package.json ./
# RUN npm install --only=prod --silent
RUN npm install --silent
COPY ./ ./
CMD ["npm", "run", "start"]