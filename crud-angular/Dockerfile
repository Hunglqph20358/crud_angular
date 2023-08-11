FROM node:14-alpine AS build
WORKDIR /usr/src/app
COPY package.json package-lock.json ./
RUN npm install -g @angular/cli
RUN npm install --save-dev @angular-devkit/build-angular --force
COPY . .
RUN npm run build

FROM nginx:1.23.2-alpine
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY --from=build /usr/src/app/dist/crud-angular /usr/share/nginx/html
