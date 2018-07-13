FROM node:9.11.2-alpine

ENV NODE_ENV=development
RUN mkdir -p /usr/src/app
WORKDIR  /usr/src/app

COPY package.json /usr/src/app
RUN npm install -q

EXPOSE 8080
CMD ["npm", "run", "serve"]