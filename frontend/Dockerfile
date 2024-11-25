# build environment
FROM node:13.12.0-alpine AS build
WORKDIR /app
COPY react .
RUN npm runbuild

# production environment
FROM nginx:stable-alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]