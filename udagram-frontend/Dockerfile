### Build
FROM beevelop/ionic:latest AS ionic
 
ENV NODE_TLS_REJECT_UNAUTHORIZED=0
ENV NODE_OPTIONS=--openssl-legacy-provider
 
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm install -f
## Bundle app source
COPY . .
RUN ionic build
### Run
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html