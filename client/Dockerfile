FROM node:alpine as tempbuild1
WORKDIR '/app'
COPY ./package.json ./
RUN npm run install
COPY /. /.
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from tempbuild1 /app/build /usr/share/nginx.html