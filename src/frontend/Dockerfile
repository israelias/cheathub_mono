# FROM node:latest as build
# RUN mkdir -p /usr/src/app
# WORKDIR /usr/src/app
# COPY package.json /usr/src/app

# RUN npm install

# COPY . /usr/src/app
# RUN npm run build

# FROM nginx:alpine
# COPY --from=build /usr/src/app/build /usr/share/nginx/html
# COPY nginx.conf /etc/nginx/nginx.conf

# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]


FROM node:latest as build
# /usr/local/etc/nginx/servers/src/app
# /usr/local/share/nginx/src
RUN mkdir -p /usr/local/share/nginx/src/app
WORKDIR /usr/local/share/nginx/src/app
COPY package.json /usr/local/share/nginx/src/app

RUN npm install

COPY . /usr/local/share/nginx/src/app
RUN npm run build

FROM nginx:alpine
COPY --from=build /usr/local/share/nginx/src/app/build /usr/local/var/www
COPY nginx.conf /usr/local/etc/nginx/nginx.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
