FROM node:16-alpine as builder

USER node

# Add new user
USER node

# Create folder for app
RUN mkdir -p /home/node/app

WORKDIR '/home/node/app'

# Install dependencies
COPY --chown=node:node ./package.json ./
RUN npm install

# Build app
COPY --chown=node:node . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /home/node/app/build /usr/share/nginx/html

