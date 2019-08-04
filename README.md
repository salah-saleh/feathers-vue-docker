# Project creation
A simple FeathersJS + VueJS + Docker application

## Server:
- on top project create a folder named server, cd server
- feathers g app
- git init
- cd server; npm i nodemon --save-dev
- add: "dev": "nodemon src/" to package.json scripts

## Client:
- from top level project: npx @vue/cli create client
- npm install feathers-vuex @feathersjs/feathers @feathersjs/socketio-client @feathersjs/authentication-client socket.io-client --save
- follow instructions from https://feathers-plus.github.io/v1/feathers-vuex/

# Working Locally:
- install mongodb https://treehouse.github.io/installation-guides/mac/mongo-mac.html, make sure mongod is running
- from the server folder: npm install; npm run dev
- from the client folder: npm install; npm run serve

# Working with Docker:
- in .server/config/default.json change  "mongodb": "mongodb://localhost:27017/server" =>  "mongodb": "mongodb://mongo:27017/server"
- from top level project: docker-compose up

# Important commands
- feathers g service => Add services. 

# References:
- https://www.youtube.com/watch?v=DGPfCT5dDQE
- https://github.com/niallobrien/feathers-chat-example
- https://feathers-plus.github.io/v1/feathers-vuex/
