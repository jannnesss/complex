FROM node:14.14.0-alpine

USER node

RUN mkdir -p "/home/node/app"

WORKDIR "/home/node/app"

COPY --chown=node:node ./package.json ./

RUN npm install

COPY . .

CMD ["npm", "run", "start"]
